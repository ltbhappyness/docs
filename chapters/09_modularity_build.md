# 9. Modularity and build

> **Status:** skeleton — content migration from `vedam.docx` pending.

**CMake + defconfig files** per node class (no Kconfig). Modules split into `core-*` and `app-*`; inter-process communication is **gRPC over Unix domain socket**. Reproducibility direction: **Nix flakes** with builder **capability gossip** and content-addressed cache.

---

## 9.1 Sections to fill (placeholders)

- 9.1.1 Repo layout for [vedam/](https://github.com/ltbhappyness/vedam): `modules/core-*`, `modules/app-*`, `config/defconfig.class-*`, `proto/`, `tools/`.
- 9.1.2 Per-class defconfig files (`config/defconfig.class-a` … `class-e`); `VEDAM_NODE_CLASS` selector; `config/schema.proto` for non-C tooling.
- 9.1.3 Defconfig parsing — currently a stub in CMake; needs key=value parsing or generated `vedam_config.cmake`; gate `add_subdirectory` accordingly.
- 9.1.4 Module list and intent — see [02_architecture.md](./02_architecture.md) and `vedam/AGENTS.md`.
- 9.1.5 IPC schema: `.proto` sources under `proto/` and `modules/*/proto/`; gRPC over UDS for same-host; gRPC frames over libp2p streams for cross-host — link to [04_network.md](./04_network.md).
- 9.1.6 Reproducible builds: Nix flakes; builder capability gossip; k-of-N attestation policy optional.
- 9.1.7 Versioning: semver per app; warm vs cold upgrades; optimistic cross-version compatibility with explicit deprecation windows.

Embedded figure targets:

`![Figure 10: Module dependencies](../figures/fig10_module_dependencies.svg)`

`![Figure 11: Build provenance](../figures/fig11_build_provenance.svg)`

---

## 9.2 References

To be populated (CMake documentation, Nix flakes, capability-gossip prior art if any).
