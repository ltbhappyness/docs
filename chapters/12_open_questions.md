# 12. Open questions

> **Status:** skeleton — content migration from `vedam.docx` pending.

Open design questions that the project has consciously deferred. Each will be promoted into a dedicated section of its parent page when resolved.

---

## 12.1 Archive economics without fees or tokens

How to incentivise long-term archival storage when there is **no fee** and **no token** at MVP. Candidates to investigate: voluntary altruism + reputation, reciprocity protocols, social commitment via chapters, optional "archive credit" non-monetary points, sponsorship by NPO. Parent: [03_storage.md](./03_storage.md).

## 12.2 Censorship-resistance policy

Community rules built into the network, not money-gated, not poll-gated. Concrete rule set TBD. Parent: [10_threat_model.md](./10_threat_model.md).

## 12.3 Formal verification scope and timeline

Which components warrant machine-checked proofs (consensus core, vbc, crypto wrappers), in what tooling (Coq / Lean / TLA+), on what timeline. Parent: [08_security.md](./08_security.md).

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
