---
type: Chapter
title: "API classes"
description: "Verticals in the tree today, then later classes that are only a map."
tags: [design-spec]
timestamp: 2026-09-22T00:00:00Z
---

# 10. API classes

[System](./system.md) is specified in full. This chapter names the other verticals the generator already emits, then the ones that are still only a map.

The five verticals in the tree today are system, identity, storage, security, and wasm. Each has a public header under `include/vi/class/`, a message file under `proto/vedam/`, and a library body that returns success. Identity and storage are addressed by `key`. System, security, and wasm have one object and an empty key.

Subscribe on each of them registers a watch and returns once. Notify, in the message file, is the stream of later changes. The node does not push that stream yet. Logging is not a file path on System.

A later vertical should gain a section here, or its own chapter, in the shape of [Proto layout and codegen](./proto-codegen.md): purpose, types, attribute enum, verbs, and the walk from the public call to the library.

The sections from wallet onward describe work that is **not** in this tree. They stay so the map is visible. They are not a claim that those headers exist.

---

## 10.0 Verticals in this tree

| Vertical | Key | Public attributes | Role in this generation |
|----------|-----|-------------------|-------------------------|
| **identity** | Required | `IDENTITY_ATTR_KIND`, `IDENTITY_ATTR_STATE` | A keyed object. Kind is read only. State is read only and subscribable. |
| **storage** | Required | `STORAGE_ATTR_SIZE`, `STORAGE_ATTR_STATE` | A keyed object. Size is read only. State is read only and subscribable. |
| **security** | Empty | `SECURITY_ATTR_PROFILE`, `SECURITY_ATTR_STATE` | One object. Profile is read only. State is read only and subscribable. |
| **wasm** | Empty | `WASM_ATTR_ENGINE_STATE`, `WASM_ATTR_WORKERS` | Configuration only. No engine is linked. Engine state is read only and subscribable. Workers is read only. |

The longer identity story in the next section is the account-owner design. It is not what `identity.yaml` stores today.

---

## 10.1 Identity

The shipping identity vertical is the table in section 10.0. The paragraphs below are the later account-owner design. They are not attributes in `identity.yaml`.

Register root Subject (human: nullifier gate; machine: attestation), device delegations, app-scoped pseudonyms, revocations. **Use** is get and set with a pseudonym. **Register** is rare.

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
