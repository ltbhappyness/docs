# Chapters

# Part I — Foundations

* [0. Mission](00_mission.md) - the four-condition thesis, golden-ratio symbology, and the universal scope.
* [1. Motivation](01_motivation.md) - the structural problems Vedam exists to address.

# Part II — Architecture

* [2. Architecture](02_architecture.md) - overall stack, node classes A through E, layered reference view.
* [3. Storage layer (L0)](03_storage.md) - libgit2 over SHA-256, content-addressed Merkle log, encrypted-RDF at rest, storage adapters, retrieval flow.
* [4. Network layer](04_network.md) - libp2p substrate, gossipsub, golden-ratio peer selection.
* [5. Consensus](05_consensus.md) - finality_digest, async quorum replay, BFT; Narwhal/Bullshark batch ingest.
* [6. Execution](06_execution.md) - Tier A data + wallet; Tier B composable contracts; layman guide.
* [15. Data model and interoperability](15_data_model.md) - RDF/HDT content model, vocabularies, encode + encrypt pipeline, SOLID compatibility.

# Part III — Identity and security

* [7. Identity and privacy](07_identity.md) - personhood nullifier, root Subject, device keys, unlinkable app pseudonyms, capabilities, SIOPv2; attestation for machines.
* [8. Security discipline](08_security.md) - crypto and consensus library policy, Linux hardening, post-quantum posture.

# Part IV — Engineering

* [9. Modularity and build](09_modularity_build.md) - CMake defconfig per class, Nix flakes, IPC.
* [10. Threat model](10_threat_model.md) - adversaries against the four conditions and their mitigations.
* [11. Performance and scaling](11_performance_scaling.md) - cost model, predicted throughput, scaling assumptions.
* [16. Deployment and operations](16_deployment.md) - edge app, install by node class, build/package, protocol surface, upgrade, CI.

# Part V — Governance and reference

* [12. Open questions](12_open_questions.md) - the design decisions that remain deliberately deferred.
* [13. Human-machine shared bill of rights](13_bill_of_rights.md) - the eight rights derived from the mission.
* [14. Glossary](14_glossary.md) - project-internal terms in one place.

