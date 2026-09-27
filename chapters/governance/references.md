---
type: Chapter
title: "References"
description: "aggregated citations for the Vedam Design Spec."
tags: [design-spec]
generated:
  by: process:ltbh-vedam
  at: 2026-09-11T00:00:00Z
---

# 17. References

Anchor citations also live in each chapter. This page aggregates them. Wikipedia links in Part I were chosen as topic entry points.

---

## 17.1 Mission and ethics

- [ltbh.org](https://ltbh.org) — mission steward
- Jennings, Moreau, Nicholson, et al., *Human–Agent Collectives*, CACM 2014
- Cavoukian, Privacy by Design
- Nissenbaum, contextual integrity
- Mayer-Schönberger, *Delete: The Virtue of Forgetting in the Digital Age*, 2009
- Value-sensitive design literature (direct and indirect stakeholders)

---

## 17.2 Local-first and data sovereignty

- Local-first software: the copy on the owner’s device is the real copy; the network is how copies meet
- [SOLID](https://en.wikipedia.org/wiki/Solid_(web_decentralization_project)) family — citizen, not clone
- RDF, Turtle, SPARQL, LDP (W3C)
- HDT (Header-Dictionary-Triples)
- UCAN; SIOPv2; DPoP

---

## 17.3 Agreement, git, overlay

- libgit2; git object model
- libp2p; gossipsub; Noise
- gRPC; Protocol Buffers; protobuf-c; nanopb
- Yin et al., *HotStuff*, PODC 2019
- Danezis et al., Narwhal / Tusk / Bullshark
- Radicle / Heartwood as git-over-P2P precedent (license review open)

---

## 17.4 Collectives and NN libraries (research, not products)

- ggml-class on-device inference
- Petals / DiLoCo-class distributed inference and training (shape only)
- UEC / libfabric / InfiniBand / NVLink / CUDA as **optional** hoods under vedam-ccl
- Kleinberg navigability (compute placement $r$, distinct from $\varphi$)

---

## 17.5 Build and ops

- CMake; Nix flakes; optional Yocto/OE later
- clang sanitizers
- Erlang OTP as metaphor for event-sourced restart (not a BEAM requirement)
- TUF-inspired OTA direction (open)

---

## 17.6 Geometry

- Golden ratio, Fibonacci, Penrose tiling — [Mission](../foundations/mission.md#geometry-and-proportion)

---

## 17.7 This specification

- [Vedam Design Spec cover](../../vedam.md)
- Implementation: [github.com/ltbhappyness/vedam](https://github.com/ltbhappyness/vedam)
