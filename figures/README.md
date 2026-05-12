# Figures — standards

Navigation: [vedam](../vedam.md) · [chapters/](../chapters/)

> **Status:** the 12 numbered SVG files (`fig01..fig12`) in this directory are placeholders inherited from the retired `vedam.docx` pipeline. They are programmatic SVG (not literal hand-drawings), but they were authored for the Word artifact and need a professional rework before this docs set goes public. The 13th file, `vedam_logo.svg`, is the project mark and is treated as final.

---

## Cover figure — `vedam_logo.svg`

`vedam_logo.svg` is the cover mark used by [docs/README.md](../README.md) and may be reused as a section opener in `vedam.md`. It is mathematically generated from the same geometry as [vedamX/src/components/VedamLogo.tsx](https://github.com/ltbhappyness/vedamX): six regular pentagons in fivefold symmetry with the golden ratio as diagonal-to-side ratio, plus a V accent that traces two of the pentagram's natural diagonals (the accent appears only on the SVG cover variant, not in the React component). The file has no rework priority.

---

## Standards

1. **SVG only.** No PNG / JPG for diagrams. Raster images allowed only for photographs, scans, or screenshots of UI — never for design figures.
2. **No hand-drawn diagrams.** Pen-and-paper sketches are useful for ideation; they do not ship in the documentation.
3. **Consistent style.** One stylesheet across all figures: matching font family, palette, stroke weights, arrowhead style. Style guide TBD (will be added here when the first reworked figure lands).
4. **Author with proper tools.**
   - **Mermaid** (`mermaid` fenced code blocks inside `.md`) for flowcharts, sequence diagrams, class diagrams, ER diagrams, state diagrams — anything Mermaid can express clearly. Renders natively on GitHub; no SVG file in this folder.
   - **Authored SVG** (Inkscape, Figma export, Excalidraw export, draw.io export) for anything Mermaid cannot express well: layered architecture views, topology diagrams with specific spatial layout, mathematical illustrations, geometry figures.
   - **Programmatic SVG** is acceptable when the diagram benefits from generation (e.g., golden-ratio constructions, Penrose tilings). Keep generators in `tools/` of the [vedam repo](https://github.com/ltbhappyness/vedam) or this docs repo, not inline.
5. **Accessibility.**
   - Every figure embedded in a `.md` page MUST have meaningful `alt` text: `![Figure 3: Layered reference architecture, showing DApps over External API over Internal services over Consensus, Storage, Network, OS](../figures/fig03_layered_architecture.svg)`.
   - Use sufficient contrast.
   - Avoid colour-only encoding — pair colour with shape, label, or texture.
6. **Numbering.** `figXX_short_name.svg` where `XX` is a two-digit number aligned to its first use across the docs set. Renumbering is acceptable; update references when you renumber.
7. **No theme-baked colours that fail in dark mode.** Either provide a neutral palette that works in both, or ship a separate `figXX_dark.svg` variant and select via Markdown picture syntax once we decide hosting.

---

## Inventory (state at retirement of the .docx pipeline)

All twelve SVGs were authored for inclusion in `vedam.docx` and embedded as high-res PNG in the Word document. They are kept here as starting material for the rework; **none should be considered final**.

| File | Used by | Rework priority |
|------|---------|----------------|
| `fig01_topology_s3e.svg` | [02_architecture.md](../chapters/02_architecture.md) | High |
| `fig02_node_classes.svg` | [02_architecture.md](../chapters/02_architecture.md) | High |
| `fig03_layered_architecture.svg` | [02_architecture.md](../chapters/02_architecture.md) | High |
| `fig04_consensus_layers.svg` | [05_consensus.md](../chapters/05_consensus.md) | Medium |
| `fig05_git_storage_mapping.svg` | [03_storage.md](../chapters/03_storage.md) | Medium |
| `fig06_phi_penrose_peer_select.svg` | [04_network.md](../chapters/04_network.md) | High (geometry-critical) |
| `fig07_data_flow_chanting.svg` | [02_architecture.md](../chapters/02_architecture.md) | Medium |
| `fig08_identity_uidai_zk.svg` | [07_identity.md](../chapters/07_identity.md) | High |
| `fig09_key_rotation_chapter.svg` | [07_identity.md](../chapters/07_identity.md) | Medium |
| `fig10_module_dependencies.svg` | [09_modularity_build.md](../chapters/09_modularity_build.md) | Medium |
| `fig11_build_provenance.svg` | [09_modularity_build.md](../chapters/09_modularity_build.md) | Low |
| `fig12_vbc_execution.svg` | [06_execution.md](../chapters/06_execution.md) | High |
| `vedam_logo.svg` | [README.md](../README.md), [vedam.md](../vedam.md) | None (final) |

Hand-drawn artifact (`fig01_topology_s3e_handdraw.png`) was removed during the docs cleanup; do not restore it.

---

## When in doubt — prefer Mermaid

GitHub renders Mermaid natively in `.md`; the diagram lives inside the page that uses it; there is no separate file to keep in sync. Reach for an SVG file in this folder only when Mermaid cannot express the layout cleanly.
