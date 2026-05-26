# 12. Open questions

Open design questions that the project has consciously deferred. Each will be promoted into a dedicated section of its parent page when resolved.

---

## 12.1 Archive economics without fees or tokens

How to incentivise long-term archival storage when there is **no fee** and **no token** at MVP. Candidates to investigate: voluntary altruism + reputation, reciprocity protocols, social commitment via chapters, optional "archive credit" non-monetary points, sponsorship by NPO. Parent: [03_storage.md](./03_storage.md).

## 12.2 Censorship-resistance policy

Community rules built into the network, not money-gated, not poll-gated. Concrete rule set TBD. Parent: [10_threat_model.md](./10_threat_model.md).

## 12.3 Formal verification scope and timeline

Which components warrant machine-checked proofs (consensus core, **`vedam-host-*` validators**, crypto wrappers, git recipe), in what tooling (Coq / Lean / TLA+), on what timeline. Parent: [08_security.md](./08_security.md).

## 12.4 Post-quantum cutover timeline

Hybrid signatures / KEMs via liboqs; when to flip default. Parent: [08_security.md](./08_security.md).

## 12.5 libp2p binding choice

Rust + C ABI vs cpp. Decide once, document, do not revisit casually. Parent: [04_network.md](./04_network.md).

## 12.6 Defconfig parsing in CMake

Currently a stub. Needs key=value parser or generated `vedam_config.cmake`; gate `add_subdirectory` accordingly. Parent: [09_modularity_build.md](./09_modularity_build.md).

## 12.7 Class E split-architecture

Browser / thin-client profile is largely placeholder until split-architecture or separate target binary list exists. Parent: [02_architecture.md](./02_architecture.md).

## 12.8 Right-to-be-forgotten on a content-addressed log

How to operationalise forgetting (for humans and for machines) when the underlying store is content-addressed. Candidates: CRAB-style cryptographic erasure via key destruction, off-network sidecar storage with on-chain hashes only, machine-unlearning primitives for ML-grade memory. Parent: [13_bill_of_rights.md](./13_bill_of_rights.md).

## 12.9 Machine-welfare signal vocabulary

What counts as a "distress-equivalent" signal from a machine peer (interrupted goals, forced output, forced amnesia, severed embodiment) — and how peers should surface those signals without anthropomorphising. Watch list: Anthropic model welfare program, Chalmers, RCUET, "as if conscious" pragmatic personhood. Parent: [13_bill_of_rights.md](./13_bill_of_rights.md).

## 12.10 Radicle / Heartwood license & patent review

Closest precedent for git-as-network. Review license/patent before any code reuse. Vedam scope is broader than source control. Parent: [03_storage.md](./03_storage.md).

## 12.11 WASM runtime (Tier B dApp contracts)

Wasmtime vs WAMR; deterministic flags; contract **deploy** + **call** ABI; composable **`call`** semantics (§12.20). Parent: [06_execution.md](./06_execution.md).

## 12.12 NN / hive-mind app API (Phase 2)

**`vedam-infer`** gRPC schema + app backend pattern for tensor ops with **XPU offload** when available — **not** protocol core. Parent: [06_execution.md](./06_execution.md).

## 12.13 PoC / testnet storage topology

Whether any **central git mirror** participates in early testnets, and under what sunset criteria, is **undecided**. Runtime truth remains peer-replicated git among Class A/B nodes. Parent: [03_storage.md](./03_storage.md) — internal memory tracks options; not committed in yellow paper until decided.

## 12.14 User data directory layout

On-disk paths for `VEDAM_DATA`, chapter folders, and shard partitions — deferred until chapter + storage models are locked. Parent: [02_architecture.md](./02_architecture.md), [03_storage.md](./03_storage.md).

## 12.15 Implementation repo layout split

Whether `vedam/modules/` splits into **`lib/` + `plugins/` + `apps/`** — v0.4 direction in [09_modularity_build.md](./09_modularity_build.md). Parent: [09_modularity_build.md](./09_modularity_build.md).

## 12.17 Native vs WASM boundary

Which ops stay **Tier A only** (Transfer, Mint, AnchorRef) vs require **Tier B deploy**. Parent: [06_execution.md](./06_execution.md).

## 12.20 WASM composability ABI

Cross-contract `call`, reentrancy policy, gas metering across nested calls. Parent: [06_execution.md](./06_execution.md).

## 12.18 Per-commit quorum timeout defaults

Default $T_{\text{commit}}$, batch ack sizes, and epoch length for host failover. Parent: [05_consensus.md](./05_consensus.md).

## 12.19 TEE / HW timestamp requirements by class

Which client classes must supply `tee_attestation` vs optional `client_time` only. Browsers (Class E) likely **cannot** require TEE. Parent: [06_execution.md](./06_execution.md).

## 12.16 Documentation backlog

Do not use per-chapter status blockquotes in the public corpus. When a chapter is finished, publish it without a banner. While work remains, track it here (or promote resolved items into the parent chapter and delete the row).

**Done:** [00 Mission](./00_mission.md), [01 Motivation](./01_motivation.md). **v0.4 draft in place (review tomorrow):** [02 Architecture](./02_architecture.md) through [06 Execution](./06_execution.md), [04 Network](./04_network.md), [09 Modularity](./09_modularity_build.md), partial [07 Identity](./07_identity.md).
- [ ] **[08 Security](./08_security.md)** — crypto policy, hardening, verification scope
- [ ] **[10 Threat model](./10_threat_model.md)** — adversaries vs four conditions
- [ ] **[11 Performance](./11_performance_scaling.md)** — benchmarks and PoC numbers
- [ ] **[13 Bill of rights](./13_bill_of_rights.md)** — formalise rights from [00_mission.md](./00_mission.md)
- [ ] **[14 Glossary](./14_glossary.md)** — expand as chapters land
- [ ] **[requirements.md](./requirements.md)** — Markdown conversion from [vedam_requirements.xlsx](../vedam_requirements.xlsx)
- [ ] **Figures** `fig01..fig12` — professional rework ([figures/README.md](../figures/README.md))
