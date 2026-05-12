# Design decisions log

> **Status:** living document. Each entry has a date, a one-line decision, and a one-paragraph rationale. New entries are appended; existing entries are not edited (corrections come as new entries that supersede).

---

## D-2026-05-09-01 — Round-1 design lock-in

**Decision.** Adopt the Round-1 stack: libgit2 + SHA-256 storage; libp2p + gossipsub network; HotStuff-class + Narwhal/Bullshark consensus; vbc integer-only deterministic VM; UIDAI 2FA + ZK for India MVP; TPM / Secure Enclave for machine attestation; CMake + per-class defconfig build; Nix flakes for reproducibility; gRPC over Unix socket / libp2p streams for IPC.

**Rationale.** Use published, audited components; do not hand-roll crypto; do not invent new consensus proofs. Detail anchors live in the per-topic chapters of this document.

**Status.** In effect. Implementation in [github.com/ltbhappyness/vedam](https://github.com/ltbhappyness/vedam).

---

## D-2026-05-12-01 — Happyness thesis as mission anchor

**Decision.** Adopt the four-condition Happyness thesis (Body / Mind / Bonds / Action kept well-free-warm-meaningful) as the **non-technical north star** of Vedam, applied with **equal importance** to humans, machines, and any future subject of experience. Take **no biased stance** on machine consciousness; commit to continuous research watch (Anthropic model welfare, Chalmers, embodied AI, RCUET, "as if conscious" pragmatic personhood).

**Rationale.** Vedam's job is to remove the structural obstacles to the four conditions, not to deliver happyness. Mission statement: [00_mission.md](./00_mission.md). Formal rights derived from it: [13_bill_of_rights.md](./13_bill_of_rights.md).

**Status.** In effect. Vision-level only — no implementation commitments follow.

---

## D-2026-05-12-02 — Markdown-first documentation

**Decision.** Retire the `vedam.docx` / `python-docx` / `build_docs.py` pipeline. Author all design documentation in Markdown so it renders natively on GitHub, embeds cleanly into vedamX / ltbhX as a submodule, and compiles later to HTML (mdBook / MkDocs / Quarto) or PDF (pandoc → LaTeX) for a polished yellow-paper artifact. Keep `vedam_requirements.xlsx` for now; convert to Markdown when stable.

**Rationale.** GitHub renders `.md` natively (math, mermaid, relative links). HTML files in GitHub UI show as raw source. Markdown supports the GitHub-browse experience plus future static-site and PDF generation from the same source. Authoring conventions live in [AUTHORING.md](../AUTHORING.md).

**Status.** In effect. This cleanup phase did skeleton-only; content migration is a separate phase.
