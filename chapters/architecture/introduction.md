---
type: Chapter
title: "Introduction"
description: "why the architecture part exists, who it is for, and what it covers."
tags: [design-spec]
timestamp: 2026-09-11T00:00:00Z
---

# 2. Introduction

Part I said why Vedam exists. This part says how the platform is put together so that why can survive contact with running software. It is the map of the house: who lives here, what the rooms are called, which doors connect them, and which later chapters walk into each room and stay.

The [Mission](../foundations/mission.md) remains the authority on purpose. Nothing in this part is allowed to quietly become an engagement machine, a happyness score, or a landlord.

---

## 2.1 Purpose

This part is written for people who will build on Vedam, review it, or live on it and want to know what they are being asked to trust.

It explains, in order: the words the rest of the spec will use; whose questions the architecture must answer; then the high-level design itself — the planned source tree, the public interfaces, the inner modules, and the two ways a node starts (inside an app, or as the **vedamd** daemon). Later parts do not repeat that map. They fill it in. Interfaces come first. Interiors of libraries come after.

The design choice underneath everything else is simple. Vedam is libraries. An app that can link those libraries **is** a node. A page that cannot link them talks to a node that is already running. The chapters that follow exist to make that sentence precise, not to freeze every binary flag before the interfaces are designed.

---

## 2.2 Scope

This part describes the **shape of the platform**: how a node instance is born and ended; how public messages are generated from a single contract; how those messages travel (inside a process, on a local queue, in shared memory, over a local or remote call, or across the peer network); how history is stored as git-shaped repositories; how events are the log; how identity looks from the inside and from the account owner’s chair; how programmable rules run as native checks or as WebAssembly; how peers overlay and come to agreement; how neural libraries sit on the platform for later apps; how chanting is the first application library; and how operators and a test network are expected to behave.

This part does **not** walk the C files of the implementation tree. That tree follows this spec; it is not this spec. This part does not record private agent memory, sell a product, name a commercial multi-agent offering, rank anyone’s happyness, or charge a fee or a token in order to take part. It does not specify kernel-bypass networking or production GPU offload as something this generation must ship (an offload slot exists so later work has a door). Public C headers are generated; they are not hand-written by library authors as the contract.

A browser build is the **same libraries**, compiled to WebAssembly, or a thin conversation with a helper node. It is not a second Vedam.

---

## 2.3 Audience

Different readers need different doors into the same house.

| Reader | What this part must make clear |
|--------|--------------------------------|
| Someone writing a Vedam library or plugin | Which interface they implement, and that plugins use the same message shapes as code linked at build time. |
| Someone maintaining **vedamd** | That the daemon stays small: load configuration, start the System class, run until asked to stop. The product is still the libraries. |
| Someone writing an application | When to link the libraries and start a node inside the app, and when to talk to a node that is already running. Which classes actually create objects, and which objects already exist after the System starts. |
| An account owner reading for trust | Where the human terms live (Part V). This part will not bury them in cryptography. |
| An auditor or researcher | Who the stakeholders are, why a node never sequences its operator’s own submits, and that grants cannot be widened by an agent. |

---

## 2.4 Documents this part relies on

The architecture does not stand alone. The table names the companions and what they are for.

| Document | What it supplies |
|----------|------------------|
| [Mission](../foundations/mission.md) and [Motivation](../foundations/motivation.md) | Why the platform exists, and which primitives make those goals harder to violate. |
| The rest of this part | Words, viewpoints, and the high-level design. |
| [Part III](../interfaces/proto-codegen.md) | The public message contract and the generated C API. |
| [Part IV](../modules/inventory.md) | What sits inside each library. |
| [Part V](../identity-security/external.md) | Identity and terms in the account owner’s language. |
| [Part VI](../engineering/engineering.md) | Build, tests, and operations. |
| [Part VII](../governance/open-questions.md) | Open decisions, glossary, and the bill of rights. |
| libgit2, libp2p, gRPC, protobuf, libsodium | Existing libraries named where Vedam actually uses them. Each is introduced in the high-level architecture before it is treated as known. |

---

## 2.5 Assumptions and constraints

These are working facts for the design, not slogans.

The protocol libraries are written in **C**, because they must link into phones, PCs, small devices, and a daemon. A native app links them through the usual foreign interface on that platform (on Android and iOS, that means the native development kit). **vedamd** is the headless host. A client that cannot link C — a page in a browser — speaks to a node that is already running.

By default there is **one running instance per process that started it**. Another program on the same machine may attach to that instance instead of starting a second one. The account owner may still choose to run more than one instance. The platform does not force a swarm.

Most devices Vedam cares about are ordinary: phones, laptops, browsers, small gateways. Machines with graphics processors are welcome and optional. **A node must work on CPU alone.** When fast interconnects between accelerators are absent, group communication falls back to ordinary send and receive, with a multicast-like fan-out on the overlay.

**The device works first.** After the System class is created, the instance is useful with the network unplugged. Joining other peers is an enhancement, not a login.

A node **never sequences its operator’s own submits**. The replica that orders incoming work for a window is a designated host, not a master, and it does not order the work of the person who operates it.

**Logging is the Event class.** Diaries are not written to ad-hoc files as the design.

Neural generate, train, infer, and distribute are **platform libraries**. Account-owner neural applications come later. They are not a later personality of the daemon.

The license intent is on the [cover](../../vedam.md). Implied objects that System create may or may not allocate (for example whether identity keys exist at start or at first update) are frozen in Part III or listed as open.

---

## 2.6 Two ideas Vedam is inspired by

Vedam’s vision is its own. Two public lines of work are still worth naming, because the platform **takes a part of each** and refuses the rest.

**Data in the owner’s hands.** A person should hold their own facts. Applications should be replaceable. The public record can hold hashes; the readable life stays with the owner. Vedam takes that. It does not take a hosted identity issuer, and it does not let a server be the real access-control brain.

**Rules strangers can check.** When two people who do not share a company must trust a rule, that rule should run where both can see it — as native validation or as WebAssembly — not as a private service. Vedam takes that. It does not take a global fee market, and it does not require a token in order to exist.
