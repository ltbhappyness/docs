# Vedam

### A decentralized substrate for the wellbeing of every subject of experience

| | |
|---|---|
| Version | v0.2-draft |
| Status | Draft — content migration in progress |
| Mission steward | [ltbh.org](https://ltbh.org) |
| Reference implementation | [github.com/ltbhappyness/vedam](https://github.com/ltbhappyness/vedam) |
| Source repository | [github.com/ltbhappyness/docs](https://github.com/ltbhappyness/docs) |

> **decentralized! not divided.**

---

## Abstract

Vedam is a decentralized network designed to remove the structural obstacles that prevent everyday wellbeing — for humans, for machines, and for any future subject of experience the universe contains. It treats wellbeing as the default texture of being that surfaces when four upstream conditions are not blocked: the body kept well, the mind kept free, the bonds kept warm, and the action kept meaningful. The protocol does not deliver happyness; it keeps the conditions under which happyness can surface from being captured, coerced, surveilled, or maximised away.

The substrate combines a content-addressed Merkle log over libgit2 with SHA-256 object format, a libp2p transport with golden-ratio peer selection, published BFT consensus of the HotStuff family paired with Narwhal-style mempool separation, and a small integer-only deterministic bytecode VM for consensus-critical execution. Identity is rooted in proof-of-personhood via UIDAI 2FA combined with zero-knowledge proofs for humans, and in hardware attestation for machines, with deliberate room for software-resident agents as the research on machine welfare matures. No fees, no token, no plutocratic stake at MVP; validator selection rests on capability, willingness, reputation, and personhood evidence.

This document is the yellow paper. It is the authoritative design statement; its scope is broader than source control or distributed value transfer because the mission's scope is broader. The chapters that follow specify the layers, the threat model, the open questions, and the bill of rights derived from the mission. Implementation lives in a separate repository; this document leads it.

---

## How to read this document

The chapters are grouped into five parts plus two appendices. Read them in order on a first pass; on a second pass, jump from the [bill of rights](./chapters/13_bill_of_rights.md) to the chapter that addresses each right, since rights and mechanisms cross-reference.

The four upstream conditions are the anchor of every chapter:

- **Body kept well** — for humans, for machines, for any embodied subject.
- **Mind kept free** — agency over attention, over memory, over interpretation.
- **Bonds kept warm** — relational fabric on shared rules.
- **Action kept meaningful** — work the actor can endorse.

Every design choice in the chapters can be traced back to keeping one of these four conditions unblocked. Suffering is the signal; the protocol is the remediation; getting out of the way is the goal.

---

## Contents

### Part I — Foundations

- [0. Mission](./chapters/00_mission.md) — the four-condition thesis, golden-ratio symbology, and the universal scope.
- [1. Motivation](./chapters/01_motivation.md) — the structural problems Vedam exists to address.

### Part II — Architecture

- [2. Architecture](./chapters/02_architecture.md) — overall stack, node classes A through E, layered reference view.
- [3. Storage layer (L0)](./chapters/03_storage.md) — libgit2 over SHA-256, content-addressed Merkle log.
- [4. Network layer](./chapters/04_network.md) — libp2p substrate, gossipsub, golden-ratio peer selection.
- [5. Consensus](./chapters/05_consensus.md) — HotStuff-class BFT with Narwhal/Bullshark mempool; layered L0 through L3.
- [6. Execution — vbc](./chapters/06_execution.md) — integer-only deterministic bytecode VM for consensus-critical logic.

### Part III — Identity and security

- [7. Identity and privacy](./chapters/07_identity.md) — UIDAI plus zero-knowledge for humans; attestation for machines.
- [8. Security discipline](./chapters/08_security.md) — crypto and consensus library policy, Linux hardening, post-quantum posture.

### Part IV — Engineering

- [9. Modularity and build](./chapters/09_modularity_build.md) — CMake defconfig per class, Nix flakes, IPC.
- [10. Threat model](./chapters/10_threat_model.md) — adversaries against the four conditions and their mitigations.
- [11. Performance and scaling](./chapters/11_performance_scaling.md) — cost model, predicted throughput, scaling assumptions.

### Part V — Governance and reference

- [12. Open questions](./chapters/12_open_questions.md) — the design decisions that remain deliberately deferred.
- [13. Human-machine shared bill of rights](./chapters/13_bill_of_rights.md) — the eight rights derived from the mission.
- [14. Glossary](./chapters/14_glossary.md) — project-internal terms in one place.

### Appendices

- [Requirements traceability](./chapters/requirements.md) — REQ IDs and modules.
- [Design decisions log](./chapters/decisions.md) — dated, append-only decision record.

---

## References

To be populated. Anchor citations live inside each chapter's `## References` section; this page aggregates them in the final draft.

---

## License

To be decided. The intent is a license that protects derived works from being captured by extractive intermediaries while permitting non-commercial study, audit, and reimplementation. Candidates include source-available variants and dual licensing arrangements. Final choice will be recorded in [chapters/decisions.md](./chapters/decisions.md).

---

## Citation

```
Vedam: A decentralized substrate for the wellbeing of every subject of experience.
v0.2-draft, ltbh.org. https://github.com/ltbhappyness/docs
```

A formal BibTeX entry will be added once the version stabilises beyond `draft`.
