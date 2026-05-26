# 14. Glossary

Project-internal terms, kept in one place to avoid drift across pages.

---

## A

**app-chanting** — Vedam's messaging product. Deliberately named "chanting", not "chat": low-frequency, high-intention, high-quality exchange is the cultural target. See [02_architecture.md](./02_architecture.md).

**Ananda** — bliss; in *sat-chit-ananda* (existence-awareness-bliss), the nature of the Self in Vedanta. The project's name *Vedam* points here.

## C

**Chapter** — a per-subject, single-writer, signed log. The unit of identity and authorship on Vedam. See [07_identity.md](./07_identity.md).

**Class A / B / C / D / E** — node classes (archivist / full / light / IoT / browser). See [02_architecture.md](./02_architecture.md).

**CRAB** — Cryptographic erasure via key destruction. A technique for honouring the right-to-be-forgotten on content-addressed logs without rewriting history. See [08_security.md](./08_security.md) and [12_open_questions.md](./12_open_questions.md).

## D

**Designated host** — validator node selected by $H(\text{sender}, \text{app}, \text{repo}, \text{epoch})$ to sequence ingress for a window; **never** the submitter's own node instance. See [02_architecture.md](./02_architecture.md).

**finality_digest** — SHA-256 over canonical tx bytes + parent ref + round hint; quorum ack target. Stored in ledger git metadata. See [05_consensus.md](./05_consensus.md).

## E

**Eclipse attack** — a network adversary that isolates a victim peer from the honest set; mitigated in Vedam by Penrose / $\mathbb{Z}[\varphi]$ peer selection with epoch rotation. See [04_network.md](./04_network.md).

## H

**HotStuff** — the BFT consensus protocol family Vedam inherits; chosen for $O(n)$ communication and linear view-change. See [05_consensus.md](./05_consensus.md).

## L

**L0 / L1 / L2 / L3** — global Merkle-of-Merkles / shard / chapter / IoT anchor layers. See [05_consensus.md](./05_consensus.md).

## N

**Narwhal / Bullshark** — DAG-based mempool + BFT ordering of batch metadata; complements **per-commit async quorum** in v0.4. See [05_consensus.md](./05_consensus.md).

## P

**PERMA** — Seligman's positive psychology model: Positive emotion, Engagement, Relationships, Meaning, Accomplishment. One of several frameworks a subject may opt into for private self-reflection. See [13_bill_of_rights.md](./13_bill_of_rights.md) Right 7.

**phi / $\varphi$** — golden ratio $\varphi = (1 + \sqrt{5})/2 \approx 1.618$. Used throughout Vedam — Venus / pentagon symbology, $\mathbb{Z}[\varphi]$ integer peer selection. See [04_network.md](./04_network.md) and [00_mission.md](./00_mission.md).

**Proof-of-Personhood (PoP)** — non-plutocratic validator selection input combining capability + willingness + reputation + personhood evidence. See [05_consensus.md](./05_consensus.md) and [07_identity.md](./07_identity.md).

## S

**S3E** — Class A archivist / service-backbone node. Many peers at the same layer; not a single coordinator. Historical "brain" metaphor in pre-2026 docs; the networking-layer meaning is Class A unless explicitly disambiguated.

**sat-chit-ananda** — existence–awareness–bliss; the Vedanta framing from which the project's name derives.

## V

**vedam-client-*** — protobuf + library for apps: build/sign `vedam-tx`, call chat/identity gRPC.

**vedam-host-*** — validator-side libraries: verify txs, canonical git recipe, compute `finality_digest`.

**vedam-tx** — canonical versioned transaction envelope protobuf. See [06_execution.md](./06_execution.md).

**vbc** — *(Round-1)* Vedam ByteCode — **historical**; superseded by v0.3 WASM (never shipped) and v0.4 native validation.

**WASM dApp contract (Tier B)** — sandboxed `.wasm` for trustless rules (tokens, AMMs, composable calls). Distinct from EVM; see [06_execution.md](./06_execution.md) §6.0.

**vedam-client-wallet** — keys, signing, nonce tracking; ships in client library, not on-chain.

**Vedam** — the project's first product; the decentralized network itself; from *vedam* (Sanskrit / Malayalam: knowledge).

**VEDANTA** — historical name (pre-2026 docs) for the user / application entrypoint for humans and machines; superseded by current architecture terminology.
