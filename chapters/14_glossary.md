---
type: Chapter
title: "Glossary"
description: "project-internal terms in one place."
tags: [yellow-paper]
timestamp: 2026-07-11T00:00:00Z
---

# 14. Glossary

Project-internal terms, kept in one place to avoid drift across pages.

---

## A

**app-chanting** — Vedam's messaging product. Deliberately named "chanting", not "chat": low-frequency, high-intention, high-quality exchange is the cultural target. See [02_architecture.md](./02_architecture.md).

**Ananda** — bliss; in *sat-chit-ananda* (existence-awareness-bliss), the nature of the Self in Vedanta. The project's name *Vedam* points here.

## A

**App-scoped pseudonym** — a per-application identifier derived from the root Subject, mutually unlinkable across apps; cross-app linkage is opt-in and ZK-provable by the subject. See [07_identity.md](./07_identity.md).

## C

**Capability (UCAN-style)** — a signed, delegable, revocable grant ("holder of pseudonym P may append to resource R until T"), verified at the owner's node with no central ACL server. See [07_identity.md](./07_identity.md).

**CEK / content-key envelope** — a per-resource content key, wrapped (encrypted) once per authorized recipient's pseudonym key; enables decryption without a central key server. See [03_storage.md](./03_storage.md).

**Chapter** — a per-subject, single-writer, signed git repo; a subject's identity container and content namespace (may hold public, private, and group data side by side). See [07_identity.md](./07_identity.md).

**Class A / B / C / D / E** — node classes (archivist / full / light / IoT-gateway / client). See [02_architecture.md](./02_architecture.md).

**CRAB** — Cryptographic erasure via key destruction. Honours the right-to-be-forgotten on content-addressed logs without rewriting history. See [08_security.md](./08_security.md) and [12_open_questions.md](./12_open_questions.md).

## D

**Designated host** — validator node selected by $H(\text{sender}, \text{app}, \text{repo}, \text{epoch})$ to sequence ingress for a window; **never** the submitter's own node instance. See [02_architecture.md](./02_architecture.md).

**finality_digest** — SHA-256 over canonical tx bytes + parent ref + round hint; quorum ack target. Stored in ledger git metadata. See [05_consensus.md](./05_consensus.md).

## E

**Eclipse attack** — a network adversary that isolates a victim peer from the honest set; mitigated in Vedam by Penrose / $\mathbb{Z}[\varphi]$ peer selection with epoch rotation. See [04_network.md](./04_network.md).

## H

**HDT** — Header-Dictionary-Triples, a compact binary RDF serialization used for large, static graphs. See [15_data_model.md](./15_data_model.md).

**HotStuff** — the BFT consensus protocol family Vedam inherits; chosen for $O(n)$ communication and linear view-change. See [05_consensus.md](./05_consensus.md).

## L

**L0 / L1 / L2 / L3** — global Merkle-of-Merkles / shard / chapter / IoT anchor layers. See [05_consensus.md](./05_consensus.md).

## N

**Narwhal / Bullshark** — DAG-based mempool + BFT ordering of batch metadata; complements **per-commit async quorum** in v0.4. See [05_consensus.md](./05_consensus.md).

**Nullifier (personhood)** — a one-time zero-knowledge value derived from a valid Aadhaar credential; same per human, reveals nothing about the number. The **uniqueness gate** for registration — **not** a usable identifier. See [07_identity.md](./07_identity.md).

## P

**PERMA** — Seligman's positive psychology model: Positive emotion, Engagement, Relationships, Meaning, Accomplishment. One of several frameworks a subject may opt into for private self-reflection. See [13_bill_of_rights.md](./13_bill_of_rights.md) Right 7.

**phi / $\varphi$** — golden ratio $\varphi = (1 + \sqrt{5})/2 \approx 1.618$. Used throughout Vedam — Venus / pentagon symbology, $\mathbb{Z}[\varphi]$ integer peer selection. See [04_network.md](./04_network.md) and [00_mission.md](./00_mission.md).

**Proof-of-Personhood (PoP)** — for humans, a one-time Anon-Aadhaar-style ZK proof over the offline signed Aadhaar QR, emitting a nullifier; enforces one account per human without storing the Aadhaar number. Also a non-plutocratic validator-selection input. See [07_identity.md](./07_identity.md) and [05_consensus.md](./05_consensus.md).

## R

**RDF** — Resource Description Framework; the triple-based, app-independent content model Vedam uses for payloads. See [15_data_model.md](./15_data_model.md).

**Root Subject ID** — a subject's single accountable, pseudonymous DID; device keys and app pseudonyms derive from it; gated by a personhood nullifier at registration. See [07_identity.md](./07_identity.md).

## S

**SIOPv2** — Self-Issued OpenID Provider v2; the subject self-signs login assertions (no central or federated issuer), resolved via the on-chain identity registry. See [07_identity.md](./07_identity.md).

**Storage adapter** — abstraction over where objects physically live (local / peer / cloud); cloud adapters hold ciphertext only and are never the finality authority. See [03_storage.md](./03_storage.md).

**S3E** — Class A archivist / service-backbone node. Many peers at the same layer; not a single coordinator. Historical "brain" metaphor in pre-2026 docs; the networking-layer meaning is Class A unless explicitly disambiguated.

**sat-chit-ananda** — existence–awareness–bliss; the Vedanta framing from which the project's name derives.

## V

**vedam-client-*** — protobuf + library for apps: build/sign `vedam-tx`, call chat/identity gRPC.

**vedam-host-*** — validator-side libraries: verify txs, canonical git recipe, compute `finality_digest`.

**vedam-noded** — the configurable node daemon (storage + consensus + identity + chat), profiled per class; earlier drafts named it `vedam-hostd`. See [16_deployment.md](./16_deployment.md).

**vedam-tx** — canonical versioned transaction envelope protobuf. See [06_execution.md](./06_execution.md).

**vbc** — *(Round-1)* Vedam ByteCode — **historical**; superseded by v0.3 WASM (never shipped) and v0.4 native validation.

**WASM dApp contract (Tier B)** — sandboxed `.wasm` for trustless rules (tokens, AMMs, composable calls). Distinct from EVM; see [06_execution.md](./06_execution.md) §6.0.

**vedam-client-wallet** — keys, signing, nonce tracking; ships in client library, not on-chain.

**Vedam** — the project's first product; the decentralized network itself; from *vedam* (Sanskrit / Malayalam: knowledge).

**VEDANTA** — historical name (pre-2026 docs) for the user / application entrypoint for humans and machines; superseded by current architecture terminology.
