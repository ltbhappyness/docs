---
type: Chapter
title: "Transport and datastore"
description: "transport vtable including generated adapters; git datastore; offload skeleton; stream and load balance."
tags: [design-spec]
timestamp: 2026-09-11T00:00:00Z
---

# 9. Transport and datastore

Three vtables sit under the generated API: **transport**, **datastore**, **offload**. App-facing class headers do not mention them; System bind and plugins do.

---

## 9.1 Transport vtable

Every adapter implements stream semantics and **load balance** across listeners / peers.

| Backend | Framing | Notify | Typical use |
|---------|---------|--------|-------------|
| **In-process** | Direct calls; function pointers from the generated table | Callbacks into the Event bus | Same-process host; tests |
| **POSIX MQ** | Length-prefixed proto bytes | Queue; Event lib wakes workers | Same machine, separate processes |
| **Shared memory** | Same bytes on a ring or slot | Wait / futex on a sequence | Low-latency local attach |
| **gRPC** | Four services + bidi Notify (UDS or QUIC) | Stream | Web to helper; remote attach |
| **libp2p / QUIC** | Framed proto on `/vedam/api/<ver>` | Stream | Overlay; inter-node |

Android MQ fallback (if POSIX MQ is constrained) is an [open question](../governance/open-questions.md).

**Stream:** requests and Notify do not assume one datagram per verb. **Load balance:** multiple local listeners or remote peers for the same class; sticky where keys require it (datastore).

Security: Noise (libp2p); UDS credentials for local gRPC; shm only among processes the account owner launched.

Native apps that embed the node use **in-process**. Class E (browser) may omit full libp2p and talk to a helper; WASM builds still speak the **same messages**.

---

## 9.2 Datastore vtable (git)

Git provides **integrity**. Consensus chooses which commits are **final**. Git alone does not order transactions or tolerate Byzantine writers.

| Op (conceptual) | Git meaning |
|-----------------|-------------|
| Put blob / tree / commit | libgit2 write |
| Read object by id | ODB read; verify hash |
| Pack / fetch | Replication unit (not per-message `git push` on the hot path) |
| Ref update | After finality or pending/`WAL` policy |

**Class E:** libgit2-in-WASM behind the same ops ([wasm-git](https://github.com/petersalomonsen/wasm-git) as a precedent, not a required dependency).

Storage **adapters** (local disk, peer, ciphertext-only cloud) plug under the ODB. Own-credentials invariant: a node never uses another subject’s storage credentials. Detail: [Module inventory](../modules/inventory.md) cluster C/E.

---

## 9.3 Offload vtable (skeleton)

This generation specifies the **vtable only**: buffer, stream, completion Event. No DPDK, no RoCE, no production CUDA requirement. When a GPU is present, capability profile advertises it; Compute class may later bind an offload plugin. CPU-only remains mandatory.

---

## 9.4 Overlay versus local

| Path | Transport |
|------|-----------|
| App on device ↔ **vedamd** | Local socket, POSIX message queue, shared memory, or in-process |
| Node ↔ designated host / validators | libp2p streams; gRPC framed on those streams |
| Ciphertext fetch | Locate/Fetch over the same overlay; packs not chatty push |

libp2p moves bytes; it does not finalize history ([Module inventory](../modules/inventory.md) cluster G).

---

## 9.5 Network knobs (HLA level)

- Primary: QUIC; fallback TCP; Noise handshake.
- Peer discovery: Kademlia + bootstrap + capability gossip; Penrose / $\mathbb{Z}[\varphi]$ neighbour tables with epoch rotation.
- Fibonacci backoff under load.
- Batch gossip of proposal/ack frames — not high-frequency `git push` per message.
- NAT / hole-punch / relay for mobile.

Binding choice (Rust FFI vs C++) remains open.

---

## 9.6 References

libp2p; gossipsub; gRPC; protobuf-c / nanopb; libgit2; wasm-git precedent.
