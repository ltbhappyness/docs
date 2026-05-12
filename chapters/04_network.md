# 4. Network layer

> **Status:** skeleton — content migration from `vedam.docx` pending.

**libp2p** underneath (QUIC/TCP, Noise, DHT, **gossipsub**). **gRPC** carries DApp and internal API traffic, framed over libp2p bidirectional streams when peer-to-peer; gRPC/QUIC permitted between known peers when tooling supports it.

---

## 4.1 Sections to fill (placeholders)

- 4.1.1 Transports: QUIC primary, TCP fallback, mTLS-noise security.
- 4.1.2 Peer discovery: Kademlia DHT, bootstrap nodes, capability gossip.
- 4.1.3 PubSub: gossipsub topics, mesh formation, score-based moderation.
- 4.1.4 gRPC over libp2p streams: protocol IDs under `/vedam/...`, framing conventions.
- 4.1.5 **Eclipse mitigation:** Penrose / $\mathbb{Z}[\varphi]$ integer neighbourhood selection with epoch rotation. No floats; Fibonacci backoff for rate shaping.
- 4.1.6 NAT traversal, hole-punching, relay nodes.
- 4.1.7 Open: libp2p binding choice (Rust + C ABI vs cpp) — link to [12_open_questions.md](./12_open_questions.md).

Embedded figure target:

`![Figure 6: phi / Penrose peer selection](../figures/fig06_phi_penrose_peer_select.svg)`

---

## 4.2 References

To be populated (libp2p specs, gossipsub paper, Penrose tiling references, Fibonacci backoff prior art).
