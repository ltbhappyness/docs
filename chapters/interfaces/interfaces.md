---
type: Chapter
title: Interfaces
description: Northbound calls, transport hooks, node classes, and placeholder rows for verticals.
tags: [design-spec]
generated:
  by: process:ltbh-vedam
  at: 2026-11-18T21:10:00+05:30
---

# 3. Interfaces

[Part II](../architecture/design.md) is the design of any node. This part is the edge an application uses, the hooks a transport fills in, how a build chooses a class, and the rows the tree currently has. Those rows are placeholders. Their product meaning is not settled, and none of them owns the others.

## 3.1 Northbound

An application calls a vertical by filling a `vi_msg_t` and naming a verb. The public header for a row lists only the verbs and attributes that row allows an application to see. Internal verbs exist so the node can bring a row up and tear it down. An application does not call those.

The same message is used whether the call stays in-process or leaves on a link. A generated description of the message is published for authors who are not compiling the C tree. The C headers an application includes are the in-process API. The published description is for a peer that speaks the bytes.

Watches return once when the watch is registered. A later change is a separate stream. That stream is not a second message shape. It carries the same attribute list.

## 3.2 Transport hooks

Each link slot is an operations table of five hooks: close, listen, accept, connect, and call. The local slot is the local hook. The inter-process slot is the inter-process hook. The remote slot is the remote hook. There is no fourth link. A class may still say which filling flags are on. The queue layout and the hand-written length prefix are present fillings a build may leave unused. gRPC is a remote procedure call that writes a length in front of the message. Connect carries the same service and method on an ordinary web request. Those two forms are the direction for the remote link.

| Hook | When it runs |
|------|----------------|
| listen | The node is starting the receive side of that slot. |
| accept | A byte transport has a new caller. The local slot does not use this. The calling thread is the connection. |
| connect | A caller opens a sender toward an address. |
| call | One verb. The message is encoded once if the slot leaves the process. |
| close | The side that opened the descriptor closes it. |

A build may omit a slot. The hooks for an omitted slot are not compiled. The local slot is always present.

The shared socket helpers are compiled when the local-socket filling or the length-prefixed filling is on, so a build that turns on only the local-socket filling still links those helpers.

Addresses used at start are formed inside the node. They are not taken from the environment.

## 3.3 Classes of build

A class is a `.config` selection, not a different platform. The committed `.config` is class C. A configure reads that file. A missing file fails the configure. A bypass path may be passed for one configure and is not written back over `.config`. Sample files for classes A through E live beside the schema. The root build file does not name those samples. A later container may replace `.config` or pass a bypass. That container is not part of this repository.

| Class | Role in the build | What it does not do |
|-------|-------------------|---------------------|
| A | Full host libraries, all ordinary links, the daemon. | It is not a different call shape. |
| B | The same host shape as A. | It is not a second protocol. |
| C | The default host: queue, TCP, and the local socket, plus the daemon. | It does not include the compiler path. |
| D | Host libraries with the byte links off. | It does not listen on a queue or a socket. |
| E | A WebAssembly build of the libraries. No daemon, no lock, no byte links. | It does not run on the machine that merely hosts the page. |

Class E uses `emcc` from `PATH`, or from a path given on the configure command. If neither is set, configure fails and names `emcc`. The repository does not store a machine path and does not download a compiler. The module exports `vedam_init`. It does not use threads and it is not a standalone module. A page instantiates it and calls that function. The host that served the page does not.

## 3.4 Rows in the tree today

The tree has rows so the call path, the lock, and the generator can be exercised. The sentences below are placeholders. They are not a product map.

| Placeholder | What is safe to say now |
|-------------|-------------------------|
| Process control | One object that stands for the node. It does not own the other rows. |
| Identity | A row reserved for identity. Its rules are not in this chapter. |
| Storage | A row reserved for stored objects. The on-disk log is not specified here. |
| Security | A row reserved for security. It is not a policy document. |
| Contract program | A row reserved for a program whose result may decide a later log entry. No engine is linked. |
| Local plugin | A row reserved for a module that runs only on this node. It is not replayed by other nodes. |

Adding a row is a table entry and a generated header. It is not a change to `vi_msg_t` and not a change to the three slots.
