# Chapters

Reading order is also listed on [vedam.md](../vedam.md). Files use semantic names; numbers live only in headings inside each chapter.

# Part I — Foundations

* [Mission](foundations/mission.md) - the four-condition thesis, golden-ratio symbology, mission-hardening primitives, and the universal scope.
* [Motivation](foundations/motivation.md) - The structural problems Vedam exists to address.

# Part II — Architecture

* [Introduction](architecture/introduction.md) - why the architecture part exists, who it is for, layering, and what it covers.
* [Terminology](architecture/terminology.md) - words used in the architecture; the full glossary lives in Part VII.
* [Viewpoints](architecture/viewpoints.md) - who the architecture is for, what they need to know, and where those answers live.
* [High-level architecture](architecture/high-level-architecture.md) - source tree, call layers, public interfaces, inner modules, vedamd, and how a node runs.

# Part III — Interfaces

* [Proto layout and codegen](interfaces/proto-codegen.md) - YAML source of truth; Jinja templates; generated C headers and the published messages.
* [System class](interfaces/system.md) - First vertical: one object, attributes, verbs, and the walk from the public call to the library.
* [Transport and datastore](interfaces/transport-datastore.md) - How a call moves in-process, on a queue, and over temporary HTTP, and where git sits later.
* [API classes](interfaces/api-classes.md) - Verticals in the tree today, then later classes that are only a map.

# Part IV — Modules

* [Module inventory](modules/inventory.md) - Libraries clustered A–L: process, events, transport and git, identity, RDF, WebAssembly, network, neural libraries, chanting, security, build, and operations.

# Part V — Identity, security, and terms

* [Identity, security, and terms](identity-security/external.md) - account-owner view of identity, grants, threats, acceptable use, and upgrade consent.

# Part VI — Engineering

* [Engineering](engineering/engineering.md) - CMake, defconfig, Nix, tests, event-log, ops module, testnet, and GPU-versus-phone analysis.

# Part VII — Governance and reference

* [Open questions](governance/open-questions.md) - design decisions deliberately deferred, including honest Happyness gaps.
* [Human-machine shared bill of rights](governance/bill-of-rights.md) - the eight rights derived from the mission.
* [Glossary](governance/glossary.md) - project-internal terms in one place.
* [References](governance/references.md) - aggregated citations for the Vedam Design Spec.
