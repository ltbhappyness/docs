---
type: Chapter
title: "Viewpoints"
description: "who the architecture is for, what they need to know, and where those answers live."
tags: [design-spec]
generated:
  by: process:ltbh-vedam
  at: 2026-09-11T00:00:00Z
---

# 4. Viewpoints

Different people will read this spec for different reasons. This chapter names those people, the questions they are allowed to ask of the design, and which later chapter must answer them. If a question in the tables below has no home, that is a hole in the spec — not a virtue of being brief.

---

## 4.1 Who the architecture is for

| Who | What they need from Vedam |
|-----|---------------------------|
| **Account owner** | Keys that they hold, grants that only shrink, quiet-hours, encryption on by default, a yes-or-no to upgrades, and no ranking landlord. |
| **Human subject** | The four conditions as a real constraint on the platform, and chanting that is not a feed. |
| **Machine or agent subject** | The same identity and event rules as a human subject. No coerced output. A grant that cannot be widened by the agent itself. |
| **Application author** | Generated headers. A clear choice: link and start a node inside the app, or attach to **vedamd**. A WebAssembly subset for the browser. |
| **Library or plugin author** | The same message shapes for linked code and for modules loaded at run time. A list of which plugins are mandatory. |
| **Operator of an archive or validator** | How finality works, what they are allowed to pin, thermal limits, and that automatic upgrades are a **policy they set**, not a silent fleet capture. |
| **Steward (ltbh.org)** | That the design still matches the mission, and that Vedam never computes a happyness score. |
| **Auditor or researcher** | Provenance, the no-self-route rule, and honest gaps written down. |
| **Indirect parties** (families, future subjects, public law) | Placeholders for data-protection duties, and a watch on machine welfare — people who never opened an account and can still be harmed by the platform. |

---

## 4.2 Questions the design must survive

| Concern | Typical question |
|---------|------------------|
| **Mission-hardening** | Which block makes a four-condition goal harder to violate? |
| **Device first** | After System create, does the instance work with the network unplugged? |
| **Privacy default** | Is sharing an Update — a later choice — rather than something Create already gave away? |
| **Grant root** | Can an agent mint a wider grant than the master issued? |
| **Liveness and safety** | Does the client always see finalized or rejected, never a hang with no Event? |
| **No self-route** | Does the operator’s node sequence the operator’s own work? It must not. |
| **Ordinary devices** | Can a phone take part without being asked to train a giant model? |
| **Emergence** | Are neighbour tables local rules, or a growth target in disguise? |
| **Ops** | Are errors events? Who consents to an upgrade? |
| **Honest gap** | If there is no platform hook for a mission claim, is that written down? |

---

## 4.3 Where those questions are answered

| Way of looking | What it frames | Primary home in this spec |
|----------------|----------------|---------------------------|
| **Composition** | Libraries, plugins, vedamd, product apps | [High-level architecture](./high-level-architecture.md) |
| **Instance lifecycle** | System create, delete, notify | [System class](../interfaces/system.md) |
| **Interface** | Proto files, generated headers, transports | [Part III](../interfaces/proto-codegen.md) |
| **Data in the owner’s hands** | RDF, chapters, encryption | [Module inventory](../modules/inventory.md) |
| **Rules strangers can check** | Native checks, WebAssembly, wallet | Same inventory, programmable-rules cluster |
| **Agreement** | Designated host, quorum, tiered finality | Network cluster in the inventory |
| **Collective compute** | Neural libraries, vedam-ccl, offload door | Neural cluster in the inventory |
| **Mission-hardening** | Four-condition checklist versus blocks | Section below, and [Mission](../foundations/mission.md#mission-hardening-on-the-platform) |
| **Account-owner terms** | Login, grants, acceptable use, upgrade consent | [Part V](../identity-security/external.md) |
| **Engineering** | CMake, events, ops pipeline | [Part VI](../engineering/engineering.md) |

Every row in the mission-hardening map must name a **block** in the high-level architecture and an **API default** in Part III, or be listed as an honest gap in [Open questions](../governance/open-questions.md).

---

## 4.4 Mission-hardening as a viewpoint

This is a checklist for the architecture, not a sermon. Each condition must land on a block.

| Condition | Where the high-level design carries the hook |
|-----------|-----------------------------------------------|
| Body kept well | Event priority, quiet-hours on System, thermal governor plugin, duty-cycle events |
| Mind kept free | No ranking class; unranked Event; encryption default; device-first System; grants that only shrink; audience attributes; pseudonyms; no central issuer |
| Bonds kept warm | Chanting as a separate first application; shared identity rules; git provenance without leaderboards |
| Action kept meaningful | Compute is opt-in (not implied by System create); no fee APIs; wallet and WebAssembly when strangers must trust a rule |
| Emergence | Geometry plugin, Fibonacci backoff, a small mandatory plugin set |
| Agents | Grant root; Event for poisoned memory; no global score API |

Honest gaps remain as in Part I (clinical care, civic truth, the warmth of a particular bond, vocabulary for machine experience).
