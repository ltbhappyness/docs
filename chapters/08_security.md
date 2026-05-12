# 8. Security discipline

> **Status:** skeleton — content migration from `vedam.docx` pending.

**Do not hand-roll crypto.** **Do not hand-roll consensus.** Use audited libraries; cite the protocols being implemented; harden hosts with standard Linux primitives rather than mandating full VMs.

---

## 8.1 Sections to fill (placeholders)

- 8.1.1 Crypto library policy: **libsodium**, **Noise**, audited ZK stacks, **liboqs** for post-quantum.
- 8.1.2 Algorithm choices: Ed25519 / X25519 baseline; ChaCha20-Poly1305 AEAD; Argon2id KDF; HKDF for ratcheting.
- 8.1.3 PQ posture: hybrid signatures / KEMs path via liboqs; cutover timeline open.
- 8.1.4 Linux hardening: namespaces, seccomp filters, rlimits, no SUID, drop capabilities.
- 8.1.5 **No full-VM requirement** for MVP; light OS isolation only.
- 8.1.6 Threat-side coverage — see [10_threat_model.md](./10_threat_model.md).
- 8.1.7 Formal verification: scope, candidates (consensus core; vbc), timeline — open.
- 8.1.8 Secret handling: never in repo; OS keychain / env; key destruction (CRAB) for cryptographic forgetting.

---

## 8.2 References

To be populated:

- libsodium documentation.
- Noise Protocol Framework — Perrin.
- liboqs project, NIST PQ standardisation status.
- *Law and Tech IE* — CRAB model for cryptographic erasure on immutable ledgers.
