# 14. Glossary

> **Status:** skeleton — content migration from `vedam.docx` pending.

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

**Decentralized! not divided.** — Project continuity marker; applies across humans, machines, and any future subjects of experience.

## E

**Eclipse attack** — a network adversary that isolates a victim peer from the honest set; mitigated in Vedam by Penrose / $\mathbb{Z}[\varphi]$ peer selection with epoch rotation. See [04_network.md](./04_network.md).

## H

**HotStuff** — the BFT consensus protocol family Vedam inherits; chosen for $O(n)$ communication and linear view-change. See [05_consensus.md](./05_consensus.md).

## L

**L0 / L1 / L2 / L3** — global Merkle-of-Merkles / shard / chapter / IoT anchor layers. See [05_consensus.md](./05_consensus.md).

## N

**Narwhal / Bullshark** — DAG-based mempool / ordering protocols Vedam pairs with HotStuff-class consensus.

## P

**PERMA** — Seligman's positive psychology model: Positive emotion, Engagement, Relationships, Meaning, Accomplishment. One of several frameworks a subject may opt into for private self-reflection. See [13_bill_of_rights.md](./13_bill_of_rights.md) Right 7.

**phi / $\varphi$** — golden ratio $\varphi = (1 + \sqrt{5})/2 \approx 1.618$. Used throughout Vedam — Venus / pentagon symbology, $\mathbb{Z}[\varphi]$ integer peer selection. See [04_network.md](./04_network.md) and [00_mission.md](./00_mission.md).

**Proof-of-Personhood (PoP)** — non-plutocratic validator selection input combining capability + willingness + reputation + personhood evidence. See [05_consensus.md](./05_consensus.md) and [07_identity.md](./07_identity.md).

## S

**S3E** — Class A archivist / service-backbone node. Many peers at the same layer; not a single coordinator. Historical "brain" metaphor in pre-2026 docs; the networking-layer meaning is Class A unless explicitly disambiguated.

**sat-chit-ananda** — existence–awareness–bliss; the Vedanta framing from which the project's name derives.

## V

**vbc** — Vedam ByteCode. Small integer-only deterministic interpreter in C; consensus-critical execution. See [06_execution.md](./06_execution.md).

**Vedam** — the project's first product; the decentralized network itself; from *vedam* (Sanskrit / Malayalam: knowledge).

**VEDANTA** — historical name (pre-2026 docs) for the user / application entrypoint for humans and machines; superseded by current architecture terminology.
