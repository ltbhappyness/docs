# 11. Performance and scaling

> **Status:** skeleton — content migration from `vedam.docx` pending; PoC numbers TBD.

Predicted throughput, latency, and scaling behaviour, with PoC measurements added as they are produced. Formulas are stated explicitly so reviewers can disagree with the assumptions, not just the conclusions.

---

## 11.1 Cost model (placeholder)

Per-block consensus message cost under HotStuff-class with $n$ validators, $f$ Byzantine, and proposer rotation:

$$C_{\text{msgs/block}} = O(n)$$

(Linear in $n$ thanks to threshold-signature aggregation; Vedam inherits this property from HotStuff.)

Mempool dissemination (Narwhal):

$$C_{\text{tx-broadcast}} = O(\log n) \text{ hops, } O(1) \text{ per validator round}$$

---

## 11.2 Throughput prediction (placeholder)

Define:

- $T_{\text{block}}$ — block interval.
- $B_{\text{txs}}$ — transactions per block.
- $\eta$ — utilisation factor.

Then expected throughput:

$$\text{TPS} = \frac{B_{\text{txs}} \cdot \eta}{T_{\text{block}}}$$

Concrete numbers pending PoC.

---

## 11.3 Storage growth prediction (placeholder)

Per-shard growth per day:

$$G_{\text{shard/day}} = \text{TPS}_{\text{shard}} \cdot s_{\text{tx}} \cdot 86400$$

with class-tiered retention policies — see [03_storage.md](./03_storage.md).

---

## 11.4 Sections to fill (placeholders)

- 11.4.1 Latency budget per layer (network → mempool → consensus → storage → app).
- 11.4.2 Scaling axes: shard count, validators per shard, archive nodes per shard, IoT batching factor.
- 11.4.3 Fault-tolerance under partition: liveness vs safety trade-offs.
- 11.4.4 Energy / cost-per-transaction estimate (no PoW, so dominated by network + signature ops).
- 11.4.5 PoC results — to be added.
- 11.4.6 Comparison table vs Ethereum / Solana / Aptos / Sui — once PoC numbers exist; no marketing claims until then.

---

## 11.5 References

To be populated (HotStuff paper for $O(n)$ claim; Narwhal/Bullshark papers for mempool model; libgit2 perf notes).
