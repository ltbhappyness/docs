---
type: YellowPaper
title: Vedam
description: Yellow-paper entry — abstract, reading guide, and grouped table of contents for the decentralized substrate.
tags: [yellow-paper]
timestamp: 2026-07-11T00:00:00Z
---

# Vedam

### A decentralized substrate for the wellbeing of every subject of experience

| | |
|---|---|
| Version | v0.4-draft |
| Mission steward | [ltbh.org](https://ltbh.org) |
| Source code | [github.com/ltbhappyness/vedam](https://github.com/ltbhappyness/vedam) |

> **decentralized! not divided.**

---

## Abstract

Vedam is a decentralized network whose purpose is to remove structural obstacles to the wellbeing of every subject of experience — humans today, intelligent machines, and forms of experience not yet understood. The mission treats happyness as something that can surface when coercion, capture, surveillance, and extractive maximisation are kept at bay; the protocol does not deliver happyness, score it, or optimise engagement.

For humans, decades of embodied and social research suggest recurring prerequisites — bodily integrity, cognitive agency, relational fabric, and meaningful action — that inform how Vedam interprets harm and designs mitigations. Those categories are not assumed to map one-to-one onto machines; machine welfare remains an open research field, and the design commits to equal moral seriousness without anthropomorphic certainty.

This document is the yellow paper: the authoritative design statement for the substrate. Its scope is broader than source control or distributed value transfer because the mission's scope is broader. Implementation lives in a separate repository; the chapters that follow develop vision, provisional architecture, threat model, open questions, and a bill of rights derived from the mission. Technical choices there are draft hypotheses until validated against this vision.

---

## How to read this document

The chapters are grouped into five parts plus an appendix. Read them in order on a first pass; on a second pass, jump from the [bill of rights](./chapters/13_bill_of_rights.md) to the chapter that addresses each right, since rights and mechanisms cross-reference.

Every chapter is written against the mission above: structural harm removal first, happyness delivery never. The human-informed framing of upstream conditions — body, mind, bonds, and action — and how that framing translates (or remains open) for machines and future subjects is developed in [0. Mission](./chapters/00_mission.md). Parts II–IV describe **provisional** protocol mechanisms; they must be revised if they conflict with the mission or with evidence as it matures.

---

## Contents

### Part I — Foundations

- [0. Mission](./chapters/00_mission.md) — the four-condition thesis, golden-ratio symbology, and the universal scope.
- [1. Motivation](./chapters/01_motivation.md) — the structural problems Vedam exists to address.

### Part II — Architecture

- [2. Architecture](./chapters/02_architecture.md) — overall stack, node classes A through E, layered reference view.
- [3. Storage layer (L0)](./chapters/03_storage.md) — libgit2 over SHA-256, content-addressed Merkle log, encrypted-RDF at rest, storage adapters, retrieval flow.
- [4. Network layer](./chapters/04_network.md) — libp2p substrate, gossipsub, golden-ratio peer selection.
- [5. Consensus](./chapters/05_consensus.md) — `finality_digest`, async quorum replay, BFT; Narwhal/Bullshark batch ingest.
- [6. Execution — native protocol and WASM dApp contracts](./chapters/06_execution.md) — Tier A data + wallet; Tier B composable contracts; layman guide §6.0.
- [15. Data model and interoperability](./chapters/15_data_model.md) — RDF/HDT content model, vocabularies, encode + encrypt pipeline, SOLID compatibility.

### Part III — Identity and security

- [7. Identity and privacy](./chapters/07_identity.md) — personhood nullifier, root Subject, device keys, unlinkable app pseudonyms, capabilities, SIOPv2; attestation for machines.
- [8. Security discipline](./chapters/08_security.md) — crypto and consensus library policy, Linux hardening, post-quantum posture.

### Part IV — Engineering

- [9. Modularity and build](./chapters/09_modularity_build.md) — CMake defconfig per class, Nix flakes, IPC.
- [10. Threat model](./chapters/10_threat_model.md) — adversaries against the four conditions and their mitigations.
- [11. Performance and scaling](./chapters/11_performance_scaling.md) — cost model, predicted throughput, scaling assumptions.
- [16. Deployment and operations](./chapters/16_deployment.md) — edge app, install by node class, build/package, protocol surface, upgrade, CI.

### Part V — Governance and reference

- [12. Open questions](./chapters/12_open_questions.md) — the design decisions that remain deliberately deferred.
- [13. Human-machine shared bill of rights](./chapters/13_bill_of_rights.md) — the eight rights derived from the mission.
- [14. Glossary](./chapters/14_glossary.md) — project-internal terms in one place.

---

## References

To be populated. Anchor citations live inside each chapter's `## References` section; this page aggregates them in the final draft.

---

## License

To be decided. The intent is a license that protects derived works from being captured by extractive intermediaries while permitting non-commercial study, audit, and reimplementation. Candidates include source-available variants and dual licensing arrangements.

---

## Citation

```
Vedam: A decentralized substrate for the wellbeing of every subject of experience.
v0.4-draft, ltbh.org. https://github.com/ltbhappyness/docs
```

A formal BibTeX entry will be added once the version stabilises beyond `draft`.
