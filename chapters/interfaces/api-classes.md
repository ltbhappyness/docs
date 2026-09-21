---
type: Chapter
title: "API classes"
description: "remaining generated classes after System; Event, Ops, and later verticals."
tags: [design-spec]
timestamp: 2026-09-22T00:00:00Z
---

# 10. API classes

Generated public headers will live under `include/vi/class/`. **System** is specified in full in [System class](./system.md). This chapter lists the rest so the map stays visible while their YAML and libraries are still ahead.

Subscribe on every class is an Event stream (or a filter on the Event class) when Event ships. **Logging is the Event class**, never a file path attribute.

Each new class should gain a dedicated chapter (or an expanded section here) using the template in [Proto layout and codegen](./proto-codegen.md#76-per-class-documentation-pattern): types, attributes, verbs, and the layer walk.

---

## 10.1 Identity

Register root Subject (human: nullifier gate; machine: attestation), device delegations, app-scoped pseudonyms, revocations. **Use** is get/set with a pseudonym; **register** is rare.

Create: only for truly new chapter / extra subject objects. Device stub may exist after System create.

Mission: no central issuer; SIOPv2 assertions are attrs, not an `id.vedam.net` service.

---

## 10.2 Wallet

Keys, signing, nonce tracking live in client-side wallet code linked to this class. Simple native **Transfer** is Tier A. Custom token rules are Tier B (Compute / contract call). Stub exists after System create; funding and transfers are sets.

No fee market / token at MVP as a substrate requirement.

---

## 10.3 Profile

Empty stub after create. Public chapter profile is RDF behind Content. Private fields stay encrypted. No happyness or engagement attrs.

---

## 10.4 Content

Public and capability-gated objects. Create is **rare**; key-based upsert via set is the common path. Bodies are RDF (or blob refs). Encryption default on; sharing is an explicit set.

---

## 10.5 Compute

Sessions and collective groups **have create** — System create does **not** enrol a swarm. Generate / train / infer / distribute are platform library services behind this class. Class E **uses** them remotely; it does not run training locally as a requirement.

Offload plugin bind is a set when capability advertises an accelerator.

---

## 10.6 Chanting

Chanting is not an API class in this tree. It will be a separate application repository that uses Content, Event, and Identity. No like, follower, or dwell fields at the substrate.

---

## 10.7 Plugin

Optional plugins are loaded by **registered identifier** on System set (`load_plugin_id`), not by a filesystem path. Mandatory libraries are present after System create. Signing and revocation: [Part V](../identity-security/external.md).

---

## 10.8 Capability

No create. Probed and verified at the owner node. UCAN-style: signed, delegable, revocable, **attenuating only**. Agents cannot mint a wider grant than the master issued. No platform-issued grant that bypasses the account owner.

---

## 10.9 Locate / Fetch

No create for the index. `Locate(hash)`, `Fetch(hash)`, `RequestAccess` → wrapped CEK. Integrity by hash. Plaintext only in authorized app memory.

---

## 10.10 Event (the log)

No create. The bus exists after System create in the full design.

| Attr family | Examples |
|-------------|----------|
| Envelope | key, time, producer plugin, correlation |
| Severity | debug / info / warn / error / fatal — **not** a ranking |
| Component | class name |
| Audience | who may see this event (handoff rule) |
| Stack digest | optional; not a core dump file requirement |
| Thermal / duty-cycle | body-kept-well hooks |
| Poisoned-memory / starvation | agent isolation hooks |

Handlers (plugins): persist batch to git, notify subscribers, feed **Ops**, optional debug sink that **consumes events** (early human years). There is no `syslog` / `vedam.log` as the design.

Events are **unranked**. Sort order is local policy of the account owner.

---

## 10.11 Ops

Self-heal spine. Issue objects are key-based; typical path is upsert from events, not a separate “ticket file.”

Pipeline verbs appear as attrs and notify: observe, normalize, track (open / reproducing / patch-proposed / reviewing / merged / verifying / shipped / closed), reproduce, change, review, integrate, qualify, upgrade.

Optional adapter plugins: GitHub, JIRA, Jenkins / GitHub Actions, chat. The module does not require them. Early years: humans. Later: policy engines and test oracles — not a person-shaped agent as substrate.

Upgrade notify leads to System set on nodes. Personal devices: account-owner consent. Builder nodes may auto-apply. Self-heal is not a silent worldwide push.

Full detail: [Module inventory](../modules/inventory.md) and [Engineering](../engineering/engineering.md).

---

## 10.12 Validator-facing families

Consensus proposals, votes, and epoch control are **not** all account-owner CRUD. They share the codec and transports but live in validator plugins. Client-visible outcome is still finalized / rejected on the submitting class (Content, Identity, Compute, and later apps).

---

## 10.13 References

[Proto layout and codegen](./proto-codegen.md) · [System class](./system.md) · [High-level architecture](../architecture/high-level-architecture.md)
