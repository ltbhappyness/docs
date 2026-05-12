# 3. Storage layer (L0)

> **Status:** skeleton — content migration from `vedam.docx` pending.

Content-addressed Merkle storage on top of **libgit2** with the **SHA-256 object format**. Git provides the log; consensus output is **written** as commits — git does not solve consensus.

---

## 3.1 Sections to fill (placeholders)

- 3.1.1 Object model: blobs, trees, commits, tags; how TLV transaction blobs sit inside trees.
- 3.1.2 SHA-256 transition rationale (vs SHA-1); libgit2 support state.
- 3.1.3 Class tiering for partial clone: `blob:none`, depth limits, promisor remotes (A archivist / B full / C light / D IoT / E browser).
- 3.1.4 Round = commit; metadata TLV envelope.
- 3.1.5 Large-file handling: off-network with encrypted sidecar links.
- 3.1.6 Indexes as git-native `refs/indexes/*` (no external DB for MVP).
- 3.1.7 Garbage collection beyond finality horizon; audit digest preservation.
- 3.1.8 Open: archive economics without fees/tokens — link to [12_open_questions.md](./12_open_questions.md).

Embedded figure target:

`![Figure 5: Git storage mapping](../figures/fig05_git_storage_mapping.svg)`

---

## 3.2 References

To be populated (libgit2, Git SHA-256 transition docs, promisor remotes documentation).
