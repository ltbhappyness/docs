---
type: Chapter
title: "Glossary"
description: "project-internal terms in one place."
tags: [design-spec]
generated:
  by: process:ltbh-vedam
  at: 2026-11-18T22:35:00+05:30
---

# 16. Glossary

Project-internal terms, kept in one place to avoid drift. The node’s words are the table in [Design — Terminology](../architecture/design.md#221-terminology).

---

## A

**Account owner** — the party who holds keys, grant root, quiet-hours, and upgrade consent. Public default term. Never “user of Vedam.”

**app-chanting** — The first messaging product, in its own repository when it exists. Named “chanting”, not “chat”: low-frequency, high-intention exchange. Not a plugin inside `vedam/`.

**Ananda** — bliss; in *sat-chit-ananda* (existence-awareness-bliss). The project's name *Vedam* points here.

**App-scoped pseudonym** — per-application identifier derived from the root Subject, mutually unlinkable across apps; cross-app linkage is opt-in ZK. Cluster D.

---

## C

**Capability (UCAN-style)** — signed, delegable, revocable, **attenuating** grant, verified at the owner's node. Agents cannot widen it. Root: account owner.

**CEK / content-key envelope** — per-resource content key, wrapped per authorized pseudonym.

**Chapter** — per-subject, single-writer, signed git repo; identity container and content namespace.

**Class A / B / C / D / E** — a letter in `.config` that selects how the libraries are built. A is the full host libraries, all ordinary links, and the daemon. It is not a different call shape. B is the same host shape as A. It is not a second protocol. C is the default host: a queue, TCP, and the local socket, plus the daemon. It does not include the compiler path. D is the host libraries with the byte links off. It does not listen on a queue or a socket. E is a WebAssembly build of the libraries, with no daemon, no lock, and no byte links. It does not run on the machine that merely hosts the page.

**Collective** — overlay compute group (vedam-ccl). Create is opt-in; not implied by System create.

**CRAB** — cryptographic erasure via key destruction.

---

## D

**Datastore** — git vtable (libgit2; Class E: libgit2-in-WASM).

**Designated host** — validator selected by $H(\text{sender}, \text{app}, \text{repo}, \text{epoch})$ to sequence ingress; **never** the submitter's own instance; **never** called master.

---

## E

**Eclipse attack** — isolate a peer from the honest set; mitigated by Penrose / $\mathbb{Z}[\varphi]$ selection with epoch rotation.

**Event (class)** — the log. Severity, component, correlation, audience are attrs. Not log files.

**Emergence** — global structure from local rules ($\varphi$ neighbourhoods, Fibonacci backoff). Not a growth KPI.

---

## F

**finality_digest** — SHA-256 over canonical tx bytes + parent ref + round hint; quorum ack target.

---

## G

**Generated API** — C headers from YAML under `tools/codegen/`: `vi/types.h`, `vi/class/<vertical>.h`, and `vi_msg_t`. The same attribute ids appear as enums in `proto/vedam/`. Application authors do not choose a transport in the header.

---

## H

**HDT** — Header-Dictionary-Triples, compact binary RDF.

**HotStuff** — BFT family informing linear view-change literature; Vedam adds git persistence and async per-commit replay.

---

## I

**Inner / outer step** — overlay neighbourhood walk language (geometry plugin).

**Instance** — one running System object.

**Island** — overlay partition / neighbourhood cluster (geometry + discovery).

---

## L

**L0 / L1 / L2 / L3** — global Merkle-of-Merkles / shard / chapter / IoT anchor layers.

**Local-first** — System create yields a working offline instance; overlay is enhancement.

---

## N

**Narwhal / Bullshark** — DAG mempool + BFT ordering of batch metadata; complements per-commit async quorum.

**NN applications** — account-owner apps that use platform generate/train/infer/distribute libraries. Not a later phase of `vedamd`.

**Nullifier (personhood)** — one-time ZK uniqueness gate; not a usable identifier.

---

## O

**Offload** — vtable for accelerators; skeleton this generation (no DPDK/RoCE).

**Ops** — self-heal module; issues are events. GitHub/JIRA/Jenkins are optional adapters.

---

## P

**PERMA** — Seligman's model; opt-in local introspection only. [Bill of rights](./bill-of-rights.md) Right 7.

**phi / $\varphi$** — golden ratio. Neighbour tables and backoff; Kleinberg $r$ for compute placement is distinct.

**Plugin** — `dlopen` module; mandatory vs capability/need.

**Proof-of-Personhood (PoP)** — India MVP: Anon-Aadhaar-style ZK over offline signed QR, emitting a nullifier.

---

## R

**RDF** — Resource Description Framework; app-independent content model.

**Root Subject ID** — accountable pseudonymous DID; device keys and app pseudonyms derive from it.

---

## S

**SIOPv2** — Self-Issued OpenID Provider v2; no central issuer.

**Storage adapter** — local / peer / ciphertext-only cloud; cloud never finality authority.

**Subject** — identity and moral layer (human, machine, future). Not a synonym for login.

**System** — first API class; Create starts the instance.

**S3E** — historical “brain” metaphor; networking-layer meaning is Class A unless disambiguated.

**sat-chit-ananda** — existence–awareness–bliss; name heritage.

---

## T

**Transport** — a descriptor on one of three links (in-process, same machine, network). Call carries the verb, including notify. A later overlay dials through the same descriptor.

---

## V

**vedam-ccl** — collective hood over NVLink/UEC/libfabric/IB/CUDA when present; Send/Recv + multicast-like otherwise.

**vedamd** — a small C daemon. It calls `vedam_init` and stays in the background when the node has no user interface. It is not the usual process on a phone.

**vedam-tx** — canonical versioned transaction envelope.

**vedam.net** — first product network page (today `vedamX` lander); talks to a helper node.

**Vedam** — the decentralized substrate; from *vedam* (knowledge).

**VEDANTA** — historical name for an application entrypoint; superseded.

**vbc** — historical bytecode name; superseded by WASM Tier B (never shipped vbc).

**WASM dApp contract (Tier B)** — sandboxed `.wasm` for trustless rules between strangers.
