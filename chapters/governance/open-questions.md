---
type: Chapter
title: "Open questions"
description: "design decisions deliberately deferred, including honest Happyness gaps."
tags: [design-spec]
timestamp: 2026-09-11T00:00:00Z
---

# 14. Open questions

Decisions the project has deferred. Each is promoted into its parent chapter when resolved. There are no per-chapter status banners in this spec.

---

## 14.1 Inherited (still open)

**Archive economics without fees or tokens.** Voluntary altruism, reciprocity, chapter social commitment, optional non-monetary archive credit, NPO sponsorship. Parent: [Module inventory](../modules/inventory.md) cluster C.

**Censorship-resistance policy.** Community rules in the network, not money-gated, not poll-gated. Concrete set TBD. Parent: [Identity, security, and terms](../identity-security/external.md).

**Formal verification scope.** Consensus core, host validators, crypto wrappers, git recipe; Coq / Lean / TLA+; timeline. Parent: cluster J.

**Post-quantum cutover.** Hybrid signatures / KEMs via liboqs; when to flip default. Parent: cluster J.

**libp2p binding.** Rust + C ABI vs C++. Decide once. Parent: cluster G.

**Defconfig parsing in CMake.** Key=value → generated `vedam_config.h`; gate optional MQ / gRPC / Connect sources. Parent: [Engineering](../engineering/engineering.md). Plan exists in `vedam/config/README.md`.

**Official gRPC and Connect.** Replace the temporary HTTP/1.1 unary path with linked gRPC (and Connect over QUIC). Connect ops already stub listen. Parent: [Transport and datastore](../interfaces/transport-datastore.md).

**Test framework.** Grow beyond three grouped test binaries toward a reusable harness and per-class suites. Parent: [Engineering](../engineering/engineering.md).

**Platform socket category.** Move TCP / Unix-socket helpers behind `vplatform_*` when the temporary HTTP path is replaced or kept. Parent: HLA layering.

**Class E split-architecture.** WASM libraries vs helper node vs both; dynamic linking in the browser. Parent: HLA + cluster A.

**Erasure on a content-addressed log.** CRAB, hashes-only ledger, machine unlearning. Parent: Part V (short note) and bill of rights.

**Machine-welfare signal vocabulary.** Distress-equivalent events without anthropomorphising. Parent: Part I honest gaps + bill of rights.

**Radicle / Heartwood license and patent.** Review before any code reuse.

**WASM runtime (Tier B).** Wasmtime vs WAMR; deploy/call ABI; composability / reentrancy / metering.

**Native vs WASM boundary.** Which ops stay Tier A (Transfer, Mint, AnchorRef) vs require Tier B deploy.

**PoC / testnet storage topology.** Whether any central git mirror participates early, and sunset criteria.

**Account-owner data directory layout.** `VEDAM_DATA`, chapter folders, shards.

**Implementation repo layout.** First System slice uses `include/vi|vii|lib|platform`, `src/lib|va|via|vta|platform`, linked `libvedam`. Optional `dlopen` plugins by registered id remain the direction; empty placeholder `lib/` / `plugins/` trees were removed.

**Per-commit quorum timeout defaults.** $T_{\text{commit}}$, batch ack sizes, epoch length.

**TEE / HW timestamp by class.** Browsers likely cannot require TEE.

**Software-resident agent uniqueness.** How to admit them without a Sybil hole.

**Identity primitive specs.** Offline-QR verifier, SIOPv2 binding, UCAN profile, CEK wrap/KDF.

**Tiered-finality consistency.** Reconcile single BFT path with self → DM → public BFT.

**Non-India personhood verifiers.** Same one-account rule without double registration across schemes.

---

## 14.2 Composition still open

**Implied System objects.** Exact list after Create; Identity keys at Create vs first Update; whether a default chanting repo is implied.

**Android MQ.** POSIX MQ fallback on Android.

**vedam.net discovery of vedamd.** Local socket path versus a name on the local network versus an address the owner types — Engineering states the candidates; pick defaults per operating system.

**protobuf-c vs nanopb vs both.**

**Ops adapters in-tree.** Whether GitHub / JIRA / Jenkins adapters ever live in `vedam/` or stay out-of-tree.

**Auto-apply upgrade default per class.** Consent on C–E is the direction; A/B builder default still to freeze.

**Proto compatibility windows.** How many `tx_version` / `protocol_version` majors overlap.

**Overlay CCL spec.** Mapping Send/Recv + multicast-like onto NVLink/UEC/libfabric/IB when present.

**Class E dynamic linking.** WASM component model vs static subset.

---

## 14.3 Happyness correspondence (honest gaps)

Platform primitives that **landed** (see [Mission-hardening](../foundations/mission.md#mission-hardening-on-the-platform)): no ranking API, encryption default, local-first Create, grant root in the account owner, unranked events, quiet-hours System default, chanting as first app, Penrose neighbourhoods, Event as log.

Still **app- or culture-only** (not pretended as substrate):

- Clinical mental-health outcomes
- Civic “truth” certification
- Warmth of a particular human bond
- Machine phenomenal welfare vocabulary (events reserved; words open)

If a later chapter claims a hook for these, it must show the API. Until then they stay here.

---

## 14.4 Future topics (not blockers)

More personhood verifiers; archive/compute without a token; machine vocabulary; formal verification; PQ cutover; whether $\varphi$ tables need Kleinberg mixing for search (compute placement already distinct); optional Yocto images.

Emergence vs growth: local rules review on a schedule, not a headcount KPI.

---

## 14.5 Documentation process

One part at a time; private tickets stay out of this tree. Former numbered chapter filenames were retired; the living list is [vedam.md](../../vedam.md).
