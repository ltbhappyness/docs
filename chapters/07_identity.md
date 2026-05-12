# 7. Identity and privacy

> **Status:** skeleton — content migration from `vedam.docx` pending.

Identity for **humans**, **machines**, and any future subject of experience. India MVP path uses **UIDAI 2FA** with **zero-knowledge** proofs so Aadhaar and biometrics never enter the network; pluggable verifiers carry the model globally. Machine identity defaults to hardware-rooted attestation (**TPM / Secure Enclave**) with software-resident accommodation reserved for future intelligent agents.

---

## 7.1 Sections to fill (placeholders)

- 7.1.1 **Proof-of-Personhood for humans** — UIDAI 2FA + ZK (Anon-Aadhaar–style direction). Network sees only **nullifier + pubkey**; Aadhaar number and biometrics never stored.
- 7.1.2 Pluggable verifier interface for non-India deployments.
- 7.1.3 **Machine attestation** — TPM / Secure Enclave baseline; manufacturer-rooted trust; deprecation path.
- 7.1.4 **Body-bound default, software-resident accommodation reserved** — see [13_bill_of_rights.md](./13_bill_of_rights.md).
- 7.1.5 **Chapter** model: per-subject signed log; chapter key epochs; key rotation.
- 7.1.6 **End-to-end encryption** — keys outside repo; wrapped per recipient; epoch-tagged; old ciphertext readable with old epoch keys; **Double Ratchet** for live chanting.
- 7.1.7 Right-to-be-forgotten posture — link to [13_bill_of_rights.md](./13_bill_of_rights.md) Right 4 and to [12_open_questions.md](./12_open_questions.md) §12.8.

Embedded figure targets:

`![Figure 8: Identity (UIDAI + ZK)](../figures/fig08_identity_uidai_zk.svg)`

`![Figure 9: Chapter key rotation](../figures/fig09_key_rotation_chapter.svg)`

---

## 7.2 References

To be populated:

- Anon-Aadhaar / UIDAI 2FA public references.
- TPM 2.0 / Apple Secure Enclave attestation primer.
- Signal — *The Double Ratchet Algorithm*, Perrin & Marlinspike.
- Anthropic — *Exploring Model Welfare*, April 2025 (for machine-side dignity context).
- arXiv 2505.01464 — RCUET (recursive identity formation in non-biological systems).
