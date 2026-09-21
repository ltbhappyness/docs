---
type: DesignSpec
title: Vedam
description: Vedam Design Spec — abstract, how to read, and table of contents.
tags: [design-spec]
timestamp: 2026-09-22T00:00:00Z
---

# Vedam Design Spec

### A decentralized substrate for the wellbeing of every subject of experience

| | |
|---|---|
| Document | Vedam Design Spec |
| Mission steward | [ltbh.org](https://ltbh.org) |
| Implementation | [github.com/ltbhappyness/vedam](https://github.com/ltbhappyness/vedam) |

> **decentralized! not divided.**

<p align="center">
  <img src="./vedam_logo.svg" alt="Vedam logo — six pentagons in fivefold symmetry with a V accent" width="240" />
</p>

---

## Abstract

Vedam is a place to live online without a landlord — a **platform** people and machines can run on, and a **culture** they can belong to. It is closer to a shared way of being than to a product, and closer to a craft than to a church, though it asks for the same seriousness a living tradition asks: care for bodies, minds, bonds, and meaningful work. Technically it is a set of libraries that turn an ordinary device into a peer. It is not “a protocol” in the thin sense of a cable format, though it does publish agreed messages so strangers can work together without a company in the middle.

Its purpose is to remove structural obstacles to the wellbeing of every **subject of experience** — humans today, intelligent machines, and forms of experience not yet understood. Happyness, in this house, is what can surface when coercion, capture, surveillance, and extractive maximisation are kept at bay. Vedam does not deliver happyness, score it, or tune anyone’s attention for profit. It clears the well and steps aside.

For humans, decades of embodied and social research point to recurring gates — a body kept well, a mind kept free, bonds kept warm, and action kept meaningful. Those gates tell Vedam how to read harm. They are not assumed to map one-to-one onto machines. Machine welfare is still an open field. The design commits to equal moral seriousness without pretending to certainty about silicon souls.

This document is the **Vedam Design Spec**: the public design statement. [Part I](#part-i--foundations) states the mission and the motivation. The parts that follow specify architecture, generated interfaces, libraries, identity and terms, engineering, and governance. Implementation lives in a separate repository. When code and this spec conflict, this spec wins until it is consciously revised.

The engineering work is **libraries**. A native app — later, a chanting phone app in its own repository — starts the System class in its own process (`vedam_init`). That app **is** the node. When the node must run without a screen, a small C daemon named **vedamd** starts the same libraries. A web page on [vedam.net](https://vedam.net) **talks to** that daemon. Optional plugins loaded by registered identifier remain the long-term shape for modules that are not always present.

Public message copies for application authors live in **[vedam-interface](https://github.com/ltbhappyness/vedam-interface)**. The C tree generates `.proto` and C headers from YAML in `tools/codegen/`, then publishes matching bytes to that repository when a change is ready for outsiders.

---

## How to read this document

Read from [Part I](#part-i--foundations) onward, in the order below. The [chapter index](./chapters/index.md) is the same list.

---

## Contents

### Part I — Foundations

- [Mission](./chapters/foundations/mission.md) — four-condition thesis, geometry, account owner / master / Isha (Ee-Sha), mission-hardening, agents.
- [Motivation](./chapters/foundations/motivation.md) — structural obstacles: attention economy, companion capture, encryption-in-name-only, agent risks.

### Part II — Architecture

- [Introduction](./chapters/architecture/introduction.md) — purpose, audience, and the VI → VLIB call layers.
- [Terminology](./chapters/architecture/terminology.md) — words used in the architecture; the full glossary is in Part VII.
- [Viewpoints](./chapters/architecture/viewpoints.md) — who cares, what they need to know, where those answers live.
- [High-level architecture](./chapters/architecture/high-level-architecture.md) — source tree, layers, public interfaces, inner modules, and how a node runs.

### Part III — Interfaces

- [Proto layout and codegen](./chapters/interfaces/proto-codegen.md) — YAML source of truth; Jinja codegen; generated VI/VII and wire protobuf.
- [System class](./chapters/interfaces/system.md) — first class: types, attributes, verbs, and each layer’s job.
- [Transport and datastore](./chapters/interfaces/transport-datastore.md) — how the same message travels, and how git holds history.
- [API classes](./chapters/interfaces/api-classes.md) — remaining generated classes including Event (the log) and Ops.

### Part IV — Modules

- [Module inventory](./chapters/modules/inventory.md) — inner libraries: process, events, transport and git, identity, RDF, WASM, network, neural platform, security, build, ops.

### Part V — Identity, security, and terms

- [Identity, security, and terms](./chapters/identity-security/external.md) — the account-owner view of identity, grants, threats, acceptable use, and upgrade consent.

### Part VI — Engineering

- [Engineering](./chapters/engineering/engineering.md) — how the libraries are built, tested, operated, and scaled.

### Part VII — Governance and reference

- [Open questions](./chapters/governance/open-questions.md) — decisions still open, including honest gaps in the Happyness story.
- [Human-machine shared bill of rights](./chapters/governance/bill-of-rights.md) — eight rights derived from the mission.
- [Glossary](./chapters/governance/glossary.md) — project-internal terms.
- [References](./chapters/governance/references.md) — aggregated citations.

---

## List of figures

The cover mark is [`vedam_logo.svg`](./vedam_logo.svg). Diagrams live in the chapters that need them.

| Figure | Where |
|--------|--------|
| Libraries, embedded node, and vedamd | [High-level architecture](./chapters/architecture/high-level-architecture.md) |
| Public interfaces and inner modules | [High-level architecture](./chapters/architecture/high-level-architecture.md) |
| Starting an instance | [High-level architecture](./chapters/architecture/high-level-architecture.md) · [System class](./chapters/interfaces/system.md) |
| A second process talking to a running node | [High-level architecture](./chapters/architecture/high-level-architecture.md) |
| Chanting data path | [High-level architecture](./chapters/architecture/high-level-architecture.md) |
| Retrieve / decrypt | [Module inventory](./chapters/modules/inventory.md) |
| Codegen pipeline | [Proto layout and codegen](./chapters/interfaces/proto-codegen.md) |
| Ops / self-heal pipeline | [Engineering](./chapters/engineering/engineering.md) |

---

## Inspiration

Vedam follows its own vision. It is not a child of today’s web3 products, and it is not trying to become one. Two public ideas, though, are worth taking pride in using — the way a builder reuses a good joint without moving into someone else’s house.

The first idea is **data in the owner’s hands**. Tim Berners-Lee and the Solid project argued that a person should hold their own graph of facts, that apps should be interchangeable, and that a website should not become the warehouse of a life. Vedam takes the useful part: the account owner keeps the readable copy; apps come and go; hashes can be agreed in public while plaintext stays off the public ledger. Vedam does not take Solid’s hosted issuer, and it does not trust a server to police who may read.

The second idea is **rules strangers can check**. Ethereum showed that a program in a sandbox can be the contract between people who do not share a company. Vedam takes the useful part: when two strangers must trust a rule, that rule runs as native checks or as WebAssembly, not as a private server. Vedam does not take Ethereum’s account model, and it does not put a fee or a token on the substrate in order to exist.

A third, quieter habit: **the device is the source of truth**. If the network is down, the node still works. Sharing is a later choice, not the price of joining. Neighbourhood and backoff follow local geometric rules, not a growth target. Fast growth is not a success metric.

---

## License

The legal text is still to be chosen. The intent is already clear.

Anyone may **read this document** and use the ideas in it. Anyone may write their own software from this design, on their own terms, so long as they are not copying Vedam’s interfaces or Vedam’s code.

The **libraries, generated interfaces, and implementation** are meant to be used **as a whole**. People may link them, run them, and build applications on the Vedam network through the public interfaces. They must not take only the convenient pieces, or quietly alter a piece, in order to keep the look of Vedam while dropping the parts that protect subjects — encryption defaults, grant root in the account owner, no ranking landlord, no fee to exist. A compatible implementation implements the contract; a fork that keeps the name and guts the ethics is not the use this license will permit.

---

## Citation

```
Vedam Design Spec: A decentralized substrate for the wellbeing of every subject of experience.
ltbh.org. https://github.com/ltbhappyness/docs
```
