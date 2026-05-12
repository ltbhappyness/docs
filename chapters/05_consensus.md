# 5. Consensus

> **Status:** skeleton — content migration from `vedam.docx` pending.

**Published BFT** (HotStuff-class) for L0 and L1; **Narwhal/Bullshark-style** mempool separation. Vedam does not invent new consensus proofs — it implements cited protocols and writes the agreed output as git commits.

---

## 5.1 Layered model (placeholder)

| Layer | Role |
|-------|------|
| L0 | Global Merkle-of-Merkles across shards. |
| L1 | Shards (the BFT-replicated logs). |
| L2 | Single-writer **chapters** (per-subject signed log). |
| L3 | IoT batched anchors. |

Embedded figure target:

`![Figure 4: Consensus layers](../figures/fig04_consensus_layers.svg)`

---

## 5.2 Sections to fill (placeholders)

- 5.2.1 Protocol family: HotStuff (Yin et al. 2019) — three-phase, linear view-change, $O(n)$ communication per decision.
- 5.2.2 Mempool: Narwhal (Danezis et al. 2022) + Bullshark for ordering.
- 5.2.3 Safety and liveness statements citing source papers; new proofs only where Vedam introduces new claims.
- 5.2.4 View synchronisation, pacemaker, timeouts.
- 5.2.5 **Validator selection** — non-plutocratic: capability + willingness + reputation + Proof-of-Personhood weight. **No** stake auctions; **no** fees / no token at MVP.
- 5.2.6 Determinism: OS scheduling is not trusted for agreement; vbc re-execution under gas and memory bounds — link to [06_execution.md](./06_execution.md).
- 5.2.7 PTP / time sync — deferred (not in MVP).

---

## 5.3 Sample formal statements (placeholders, fill once finalised)

> **Definition 5.1 (Quorum).** A quorum is any set $Q \subseteq V$ of validators with $|Q| \ge \lceil 2n/3 \rceil + 1$ where $n = |V|$.

> **Theorem 5.1 (Safety).** Under the standard partial-synchrony model with $f < n/3$ Byzantine validators, no two honest validators commit conflicting blocks at the same height.
>
> *Proof.* By reference to the HotStuff safety proof; the protocol message structure is preserved unchanged. $\square$

---

## 5.4 References

To be populated:

- Yin, Malkhi, Reiter, Gueta, Abraham — *HotStuff: BFT consensus with linearity and responsiveness*, PODC 2019.
- Danezis, Kokoris-Kogias, Sonnino, Spiegelman — *Narwhal and Tusk*, EuroSys 2022.
- Spiegelman, Giridharan, Sonnino, Kokoris-Kogias — *Bullshark*, CCS 2022.
