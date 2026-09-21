---
type: Chapter
title: "Transport and datastore"
description: "transport ops tables; git datastore; offload skeleton; stream and load balance."
tags: [design-spec]
timestamp: 2026-09-22T00:00:00Z
---

# 9. Transport and datastore

Transport, datastore, and offload sit **under** the generated class API. Application-facing headers under `include/vi/` do not mention them. System create (via `vedam_init`) and later binds select ops tables.

---

## 9.1 Transport ops

Every adapter implements `v_transport_ops_t`: open, close, connect, listen, call, subscribe, unsubscribe, publish.

| Backend | Framing | Typical use | Status in this slice |
|---------|---------|-------------|----------------------|
| **In-process** | Direct `vii_*` on the caller thread | Same-process host; tests | Implemented |
| **POSIX MQ** | Length-prefixed proto bytes | Same machine, separate processes | Implemented Rx path |
| **gRPC-style HTTP** | Unary POST, gRPC length prefix, protobuf body | Temporary remote and Unix-socket IPC | Implemented; **not** linked to official gRPC C++ |
| **Connect / QUIC** | Planned | Remote attach with modern HTTP | Stub listen |
| **Shared memory** | Same bytes on a ring | Low-latency local attach | Planned |
| **libp2p / QUIC** | Framed proto on `/vedam/api/<ver>` | Overlay; inter-node | Planned |

Environment variables choose ops and addresses at init (`VEDAM_TRANSPORT_LOCAL`, `VEDAM_TRANSPORT_IPC`, `VEDAM_TRANSPORT_REMOTE`, and their `_ADDR` forms). Compile-time defconfig macros will later gate optional sources.

**Stream:** requests and subscribe do not assume one datagram per verb in the full design. **Load balance:** multiple local listeners or remote peers for the same class; sticky where keys require it (datastore).

Security direction: Noise (libp2p); Unix-socket credentials for local helpers; shared memory only among processes the account owner launched.

Native apps that embed the node use **in-process**. Class E (browser) may omit full libp2p and talk to a helper; WebAssembly builds still speak the **same messages**.

---

## 9.2 Datastore vtable (git)

Git provides **integrity**. Consensus chooses which commits are **final**. Git alone does not order transactions or tolerate Byzantine writers. This vertical is designed; it is not part of the System-only shipping slice.

| Op (conceptual) | Git meaning |
|-----------------|-------------|
| Put blob / tree / commit | libgit2 write |
| Read object by id | ODB read; verify hash |
| Pack / fetch | Replication unit (not per-message `git push` on the hot path) |
| Ref update | After finality or pending/`WAL` policy |

**Class E:** libgit2-in-WASM behind the same ops ([wasm-git](https://github.com/petersalomonsen/wasm-git) as a precedent, not a required dependency).

Storage **adapters** (local disk, peer, ciphertext-only cloud) plug under the ODB. Own-credentials invariant: a node never uses another subject’s storage credentials. Detail: [Module inventory](../modules/inventory.md).

---

## 9.3 Offload vtable (skeleton)

This generation specifies the **vtable only**: buffer, stream, completion Event. No DPDK, no RoCE, no production CUDA requirement. When a GPU is present, capability profile advertises it; Compute class may later bind an offload plugin. CPU-only remains mandatory.

---

## 9.4 Overlay versus local

Local transports never become a second API. Overlay join is a later update on network plugins, not a login gate for System get.

---

## 9.5 References

[System class](./system.md) · [Proto layout and codegen](./proto-codegen.md) · [High-level architecture](../architecture/high-level-architecture.md)
