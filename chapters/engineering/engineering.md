---
type: Chapter
title: "Engineering"
description: "CMake, defconfig, Nix, tests, event-log, ops module, testnet, and GPU-versus-phone analysis."
tags: [design-spec]
generated:
  by: process:ltbh-vedam
  at: 2026-11-18T22:35:00+05:30
---

# 13. Engineering

How the Design Spec is built, tested, operated, and scaled. Libraries remain the product. **vedamd** is a small C daemon that starts those libraries when there is no user interface; it is not the product.

---

## 13.1 Repositories

| Tree | Visibility | Role |
|------|------------|------|
| **`vedam-interface/`** | Public | Published `.proto` copies for application authors. |
| **`vedam/`** | Private until it is safe | C libraries, codegen (YAML → headers/proto), transports, **vedamd**. |
| **`docs/`** | Private now, public soon | This Design Spec |
| **`.magic/`** | Always private | Agent memory; never linked from this spec |
| **Product apps** | Each its own repository | Chanting mobile, later neural apps, [vedam.net](https://vedam.net). They link Vedam libraries or talk to **vedamd**. They are not folders inside `vedam/`. |
| **`ltbhX/`** | Mission site | Not the platform |

---

## 13.2 CMake, defconfig, Nix, optional Yocto

Linux-framework-like flow:

- `config/defconfig.class-a` … `class-e` as Kconfig-style feature sets.
- CMake **must parse** them into `vedam_config.h` and gate optional sources (plan documented in `vedam/config/README.md`; not fully wired yet — [Open questions](../governance/open-questions.md)).
- Presets: host debug, sanitizer, Class C default, cross ARM, Class E WASM.
- `CMAKE_EXPORT_COMPILE_COMMANDS` for clangd.
- Tooling: clang-format, clang-tidy, ASan/UBSan/TSan jobs, optional cppcheck.
- **Nix flakes** for reproducible CI.
- **Optional Yocto/OE** later for IoT images — not an HLA blocker.
- Codegen is a **CMake custom command** from YAML. Public headers and `proto/vedam/` are never hand-edited as the contract.
- Tests in this tree: `test_ds`, `test_util`, `test_system`, `test_lock_transport`, `test_grpc_read`, `test_verticals`, `test_codec_r8`. Queue tests need permission to open a POSIX message queue. A larger framework can come later.
- No shipped fat-binary requirement: source + recipes + OTA.

```bash
cd vedam
python3 tools/codegen/generate.py --root .
cmake -B build
cmake --build build
ctest --test-dir build --output-on-failure
```

`.config` is read now. [Design](../architecture/design.md#2511-the-selection-file) describes that selection. Class E is client libraries compiled to WebAssembly, not a requirement to keep **vedamd** running all the time.

---

## 13.3 Logging is not files

The **Event API class** is the log. Severity, component, correlation key, stack digest are attrs.

Handlers: git batch persist, Notify, Ops ingest, optional human debug sink that **consumes events**.

No `syslog` file and no `vedam.log` as the design.

---

## 13.4 Ops / self-heal pipeline

Library + plugins, `ops.proto`, same CRUD. External tools are **adapters**.

1. **Observe** — log / error / crash / perf / test-fail events.
2. **Normalize** — correlate into an issue key.
3. **Track** — open / reproducing / patch-proposed / reviewing / merged / verifying / shipped / closed (full SM in cluster L).
4. **Adapter plugins (optional)** — GitHub issues/PRs, JIRA, Jenkins/GitHub Actions, chat. Early humans use these. Not required in-tree (open whether they ever are).
5. **Reproduce** — replay fixtures / testnet events.
6. **Change** — patch in a git worktree; diffs as git objects; commit as events.
7. **Review** — subscribe; accept/reject events. Early: human developers. Later: **deterministic checks + policy** — policy engines and test oracles, not a person-shaped agent as substrate.
8. **Integrate** — merge when policy quorum is met (not consensus-hot-path).
9. **Qualify** — UT/QA event packs; sanitizer jobs as subscribers.
10. **Upgrade** — upgrade events → **System.Update**. Phones: **account-owner consent**. Builder/archivist: may auto-apply. Self-heal ≠ silent worldwide push.

Mission-hardening: no engagement metric; no silent fleet capture; grants still root in the account owner for **their** instance.

Erlang OTP (supervisor restart, event-sourced aggregates) is the research metaphor, implemented in C events + plugins, not a BEAM requirement.

---

## 13.5 Upgrade without network pause

| Mechanism | Purpose |
|-----------|---------|
| `protocol_version` in handshake | Refuse incompatible peers |
| `tx_version` in envelope | Read old history |
| Plugin flags in defconfig | Enable types gradually |
| Overlap window | Dual decoders N and N−1 |

Malicious OTA: signature verification mandatory. Mirrors may cache artifacts; none are required as a central store.

---

## 13.6 Testnet, discovery, CI

Heterogeneous testnet: phones, PCs, optional GPU, Class E browser.

**Discovery of a helper `vedamd`:** Unix-domain socket path (documented per OS), optional mDNS on LAN, manual address. vedam.net and chanting **web** try a local helper first, then a chosen peer under the own-credentials invariant. Chanting **mobile** starts its own instance; it does not need to discover `vedamd` unless the account owner chooses a remote helper.

CI: configure × class; sanitizers; proto codegen freshness; unit tests; packaging smoke. PoC storage topology (whether a central git mirror appears in early testnets) remains open; runtime truth is still peer-replicated git among A/B.

---

## 13.7 GPU versus phone (memory and latency)

Most subjects will hold **phones, ordinary PCs, browsers, and IoT**, not datacenter GPUs. Treat that majority as first-class.

| Class of machine | Memory order of magnitude | Role |
|------------------|---------------------------|------|
| Smartphone (average DRAM ~8 GB class; usable after OS often ~2–4 GB) | Gigabytes | **Embeds** the node; chant, keys, small cache; **use** NN remotely |
| Laptop / light Class C | Tens of GB | Light **vedamd** if headless; otherwise the native app is the node |
| Optional GPU node | High tens of GB HBM/GDDR (e.g. 96 GB class accelerators exist; they are **not** the median) | Offload plugin when present |
| Class E browser | Tab limits | WASM libraries or helper node |

A 1B-parameter model does not “fit in the phone” as the architecture's brain. Sharded generate/train/infer/distribute + vedam-ccl is the path; CPU Send/Recv collectives remain mandatory.

**Latency task (analysis, not a benchmark claim):** pipeline RTT on overlay (ms–tens of ms) versus HBM hop (sub-microseconds to microseconds). Collectives must not assume HBM. Numbers pending PoC; formulas belong with HotStuff $O(n)$ message cost and Narwhal mempool notes below.

Consensus cost sketch (inherited; not a marketing TPS):

$$C_{\text{msgs/block}} = O(n)$$

Throughput sketch:

$$\text{TPS} = \frac{B_{\text{txs}} \cdot \eta}{T_{\text{block}}}$$

Storage growth per shard:

$$G_{\text{shard/day}} = \text{TPS}_{\text{shard}} \cdot s_{\text{tx}} \cdot 86400$$

with class-tiered retention. Concrete PoC numbers are not claimed here.

Energy: no PoW; dominated by network + signatures + optional accelerator duty-cycle (Events).

---

## 13.8 Installation by class (summary)

Vedam ships source, schemas, recipes. Participants build or cross-compile.

| Class | Typical host | Profile |
|-------|--------------|---------|
| A | Server | Archive **vedamd** plus libp2p; durable disk |
| B | Server | Full validator |
| C | Phone / laptop | Embeds the node (`vedamd` on laptop if headless; app process on phone) |
| D | IoT hub | Gateway; optional SOLID/LDP |
| E | Browser | WASM or talk to a helper; gRPC to a node |

A native app **is** the local node. A web UI talks to a **helper** `vedamd` (UDS or remote) when present.

---

## 13.9 Technology choices

| Layer | Choice |
|-------|--------|
| Core language | C |
| Apps | Native: link C libraries. Web and other non-linking clients: speak a transport to a node |
| Storage | libgit2 SHA-256 + adapters |
| Networking | libp2p (binding open) |
| Schema | protobuf; generated C API |
| Crypto | libsodium + Noise; liboqs later |
| Data | RDF; HDT for large/static |
| Tier B | WASM (runtime open) |
| Build | CMake + defconfig + Nix |

---

## 13.10 References

CMake; Nix; protobuf-c / nanopb; gRPC; libgit2; libp2p; Catch2 / GoogleTest (pick at first test); TUF-inspired OTA direction (open); HotStuff; Narwhal/Bullshark.
