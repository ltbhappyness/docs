# 2. Architecture

> **Status:** skeleton — content migration from `vedam.docx` pending.

Stack overview, node classes A-E, and the layered reference architecture. Detailed module specifications live in their own pages — this page is the map.

---

## 2.1 Reference architecture (placeholder)

Embedded figure target:

`![Figure 3: Layered reference architecture](../figures/fig03_layered_architecture.svg)`

The figure needs professional rework — see [figures/README.md](../figures/README.md).

---

## 2.2 Node classes (placeholder)

| Class | Role | Defconfig file in `vedam/` |
|-------|------|-----------------------------|
| A | Archivist / S3E backbone | `config/defconfig.class-a` |
| B | Full validator | `config/defconfig.class-b` |
| C | Light / operator (default dev profile) | `config/defconfig.class-c` |
| D | Edge / IoT gateway | `config/defconfig.class-d` |
| E | Browser / thin client | `config/defconfig.class-e` |

Embedded figure target:

`![Figure 2: Node classes](../figures/fig02_node_classes.svg)`

---

## 2.3 Sections to fill (placeholders)

- 2.3.1 Topology: S3E hub set + peers (Figure 1).
- 2.3.2 Layered view: DApps, External API (gRPC), Internal services, Consensus, Storage, Network, OS.
- 2.3.3 Module dependency graph — link to [09_modularity_build.md](./09_modularity_build.md).
- 2.3.4 Data flow (chanting example) (Figure 7).

---

## 2.4 Cross-references

- [03_storage.md](./03_storage.md) — storage layer detail.
- [04_network.md](./04_network.md) — network layer detail.
- [05_consensus.md](./05_consensus.md) — consensus detail.
- [06_execution.md](./06_execution.md) — vbc execution detail.
- [vedam/AGENTS.md](https://github.com/ltbhappyness/vedam/blob/master/vedam/AGENTS.md) — implementation handbook.
