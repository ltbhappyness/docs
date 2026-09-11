---
type: Chapter
title: "Terminology"
description: "words used in the architecture; the full glossary lives in Part VII."
tags: [design-spec]
timestamp: 2026-09-11T00:00:00Z
---

# 3. Terminology

The table in each section is the working vocabulary for Part II. The [glossary](../governance/glossary.md) is the longer list. If a later chapter needs a word that is not here, it should define it there and then be added to the glossary — not invented in passing.

---

## 3.1 People and the moral layer

| Term | Meaning |
|------|---------|
| **Account owner** | The party who holds the keys, the root of every grant, quiet-hours, and the right to accept or refuse an upgrade for an instance. This is the ordinary public term. |
| **Master** | The short noun for that same account owner. It is never used for a replica, a sequencer, or a designated host. |
| **Subject** | The dignity layer: a human, a machine, or a future form of experience. A subject is who can flourish or be harmed. It is not a synonym for “login,” and it is not owned by an application. One account owner may represent one or more subjects; one subject may operate many devices. |
| **Partner or tool** | Autonomous software either works **with** a subject under shared rules (a partner) or **for** a subject under a grant (a tool). It is never a “master replica.” |

---

## 3.2 Process and instance

| Term | Meaning |
|------|---------|
| **Library** | A `libvedam-*` archive or shared object. This is what engineering attention is for. The product of the implementation tree is libraries, not a fat user interface. |
| **Plugin** | A module loaded at run time (`dlopen`). Mandatory plugins start with the instance. Optional plugins start when the account owner enables them. Plugins speak the same messages as code that was linked at build time. |
| **Instance** | One running System object: the event bus, the transports, the git datastore, and the mandatory plugins. |
| **vedamd** | A small **C daemon**. It exists only when the node must run without a user interface — an always-on PC, a machine in the cloud, or any host a web page can reach. It loads configuration, starts the System class, and stays in the background until it is told to stop. It is not the usual process on a phone. On a phone the app **is** the node. |
| **Embed** | A native application `dlopen`s the libraries and starts the System class **in its own process**. A future chanting app in its own repository is this case. |
| **Attach** | A process that did **not** start the instance binds to one that already exists, over a transport. A web page talking to **vedamd** is this case. |
| **Node class A–E** | Five roles a running node can take: a long-term archive, a full validator, a light operator (typical phone or laptop), a small gateway, or a thin web client. The high-level architecture defines each role. |
| **Designated host** | The validator chosen to order incoming work for a window. It is not called master. It does not order the operator’s own submits. |

---

## 3.3 API and messages

| Term | Meaning |
|------|---------|
| **Generated API** | C headers emitted from `.proto` files by the Vedam code generator: shared types, one header per class, and an umbrella header. App authors include those headers. They do not choose a transport in the header. |
| **System class** | The first public class. Creating a System object starts the instance. Several other classes have no Create of their own because the System already made their objects. |
| **CRUD+Notify** | Create, Read, Update, Delete, and a Notify stream. The same verbs exist on every transport. A class may omit Create from its public header when the object is implied. |
| **Event class** | The log. Severity, component, correlation, and similar fields are attributes on events. Logging is not “open a file and print lines.” |
| **Ops class** | Self-heal: issues, reviews, and upgrades as events. GitHub, JIRA, or Jenkins may exist as optional adapters. They are not the module. |

---

## 3.4 How messages move, and where bytes rest

| Term | Meaning |
|------|---------|
| **Transport** | A plug-in path that carries the **same** protobuf bytes: a direct call inside the process, a POSIX message queue, a shared-memory ring, gRPC (a remote call, local or networked), or libp2p (the peer overlay). Every transport offers a stream and can spread load. |
| **Datastore** | Git, through libgit2 (and libgit2 compiled to WebAssembly in a browser build). There is not a second application database beside it. |
| **Offload** | A reserved slot for later accelerator work. This generation specifies the door, not a production GPU path. |
| **Message plane and ledger plane** | Readable life (encrypted RDF and blobs) versus what peers must agree in public (hashes, refs, a finality digest, identity registry entries). |
| **vedam-ccl** | A thin hood over fast collective hardware when it is present. When it is absent, the same calls become ordinary send and receive on the overlay. CPU-only remains mandatory. |

---

## 3.5 Identity and data (architecture level)

| Term | Meaning |
|------|---------|
| **Nullifier** | A uniqueness gate so one human body is not registered twice. It is not a name anyone uses as an identifier. |
| **Root subject identifier** | The accountable identifier for a subject. |
| **Device key** | A signing key delegated to one device. |
| **App-scoped pseudonym** | The everyday working identity inside one application. Cross-app linkage is opt-in and uses zero-knowledge proof when it happens at all. |
| **Chapter** | The signed git repository that is one subject’s identity container. |
| **Capability** | A grant in the UCAN style: signed, delegable, revocable, and only able to shrink. An agent cannot mint a wider grant than the master issued. |
| **Collective, island, inner and outer step** | Language for overlay neighbourhoods. The glossary carries the longer notes. |

---

## 3.6 Why this spec does not say “users of Vedam”

Platforms that harvest attention learned to call people **users**. The word sounds neutral. It is not. A user is someone a system uses: a seat, a funnel, a metric, a feed. Documentaries such as *The Social Dilemma* made that grammar visible — people trained as the product, while the interface kept saying “user.”

Vedam refuses that sentence. An **account owner** holds the keys. A **subject** has dignity. An application **attaches** to an instance; it does not own the person. There are no “users of Vedam,” because Vedam is not a landlord and subjects are not inventory.
