# 6. Execution — vbc (Vedam ByteCode)

> **Status:** skeleton — content migration from `vedam.docx` pending.

A small **integer-only** deterministic interpreter in C (~1k LOC target). Hosts validate consensus-critical logic with vbc; most DApps run as **off-chain Linux gRPC services** and sign their results onto shards. No WASM / zkVM / TEE requirement to participate in consensus.

---

## 6.1 Sections to fill (placeholders)

- 6.1.1 Design constraints: small, auditable, deterministic, integer-only, no floats.
- 6.1.2 Opcode table (placeholder — to be enumerated when finalised).
- 6.1.3 Gas model: cost per opcode, memory bound, step bound.
- 6.1.4 Host call table: state read / state write only; no I/O, no time, no randomness.
- 6.1.5 Smart-contract bytecode layout: TLV-structured, content-addressed.
- 6.1.6 Re-execution model for validators (replay determinism).
- 6.1.7 Why **off-chain Linux services** for most DApp logic: gRPC over Unix socket, capability sandboxing via namespaces / seccomp / rlimits.

Embedded figure target:

`![Figure 12: vbc execution](../figures/fig12_vbc_execution.svg)`

---

## 6.2 Worked example (placeholder)

To be added once opcode table is finalised. Will include a minimal contract (e.g. a chapter membership check), its bytecode listing, gas accounting, and a re-execution trace.

---

## 6.3 References

To be populated (deterministic VM prior art, gas accounting in EVM as comparison point — not as model).
