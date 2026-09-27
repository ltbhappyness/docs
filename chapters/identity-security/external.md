---
type: Chapter
title: "Identity, security, and terms"
description: "account-owner view of identity, grants, threats, acceptable use, and upgrade consent."
tags: [design-spec]
generated:
  by: process:ltbh-vedam
  at: 2026-09-11T00:00:00Z
---

# 12. Identity, security, and terms

This part is the **outside** of identity: what an account owner is promised, what they consent to, and what they can see. Internals (nullifier math, git recipe) live in [Module inventory](../modules/inventory.md) cluster D. The [bill of rights](../governance/bill-of-rights.md) is the moral pairing; this chapter is operational terms.

**Account owner** is the public term. **Master** is the short noun. **Isha** is not repeated here.

---

## 12.1 Layers, for account owners

Do not conflate:

| What the owner meets | What it is |
|----------------------|------------|
| Login / device | Device key delegated from the root Subject |
| App identity | App-scoped **pseudonym** — unlinkable across apps unless the owner opts into a ZK link |
| Personhood check (humans, once) | Nullifier **gate** — not a handle others search |
| Subject | Moral and accountable identity (human, machine, future) |
| Ledger | Hashes, refs, commitments — not a readable diary |

There is no central `id.vedam.net`. Session is **SIOPv2** self-issue plus registry lookup.

---

## 12.2 What starting the node promises

`vedam_init` brings the node up on the device. The copy on that device is the one that answers a local get. Sharing is not turned on by starting. There is no ranking attribute. A compute swarm is not enrolled.

Encryption at rest, quiet hours, and upgrade consent are the intended defaults for later attributes. They are not fields on System yet. Events, when that vertical exists, stay unranked.

The account owner may tighten quiet hours and thermal policy. An application must not reopen them as a trap for attention.

---

## 12.3 Grants

Every capability graph **roots in the account owner**. Agents cannot mint a wider grant. No platform-issued grant bypasses the master.

Delegation is attenuating (UCAN-style). Revocation publishes; other devices stay valid.

Audience metadata on events must survive agent handoff. Dropping it is a protocol fault.

---

## 12.4 Machines and compute consent

Machine subjects: hardware attestation where possible. Software-resident uniqueness remains open.

Compute, training, and heavy collectives require **explicit** Compute Create / Update. Thermal and duty-cycle Events are visible to the owner. Class E uses NN remotely.

---

## 12.5 Acceptable use (substrate)

The substrate is not an engagement landlord. It does not compute or display happyness. It does not provide like / follower / dwell APIs.

Community rules for speech are **network-embedded**, not money-gated or poll-gated — concrete rule set still open.

The owner must not operate another subject's storage credentials.

---

## 12.6 Machine welfare (short)

Readable personal content can be cryptographically erased (CRAB). Commitments remain hashes. Machine unlearning may apply to software subjects. This is **not** a banner right-to-be-forgotten chapter; operationalising erasure on a content-addressed log remains open.

Forced output, forced memory, forced amnesia, and severed embodiment are named as harms in the [bill of rights](../governance/bill-of-rights.md).

---

## 12.7 Threats from outside (owner-visible)

| Threat | Direction |
|--------|-----------|
| Eclipse | Penrose / $\mathbb{Z}[\varphi]$ neighbours, epoch rotation |
| Designated-host Byzantine | Quorum rejects; owner sees rejected Event; no self-route |
| Overlay CCL poisoning | Capability + replay; collective spec open |
| Summary collapse | Audience attrs on events |
| Collusion / score-gaming | No global optimisation score API |
| Sybil | Personhood nullifier / attestation |
| Quantum-era crypto | liboqs path; timeline open |
| App-store / ISP censorship | Content-addressed replication; not a complete defence |
| Class E XSS talking to local node | Bind defaults: UDS/localhost, origin checks; policy in Engineering |
| Attention-economy apps | Substrate refuses the APIs; apps may still be rude — honest gap if the owner installs them |

Adversaries against the four conditions (network, consensus, identity, crypto, platform, plutocratic, attention, machine-coercion) are the catalogue to keep filling; this chapter is the owner translation.

---

## 12.8 Incidents

Errors are **Events**, not tickets in a file. The owner (or their Ops subscriber) Reads/Notifies Event and Ops issue keys. Early years a human may also see a GitHub adapter. The design is the event spine.

---

## 12.9 Plugins, Class E, upgrades

Plugin install requires signed artifacts; revocation is owner-visible System/Plugin Read.

Class E / browser: treating the local node as a powerful backend is an XSS-shaped risk. Default bind is local and origin-restricted.

**Upgrades:** `System.Update` after Ops qualify events. Default on phones and personal PCs: **account-owner consent**. Builder/archivist nodes may set auto-apply. Self-heal is not silent worldwide push.

---

## 12.10 Data protection and license

Jurisdiction, retention, and lawful-basis tables are **placeholders**. License of the spec and code is **TBD** ([vedam.md](../../vedam.md)).

---

## 12.11 References

SIOPv2; UCAN; Anon-Aadhaar-style offline QR; Privacy by Design; [Mission](../foundations/mission.md); [Bill of rights](../governance/bill-of-rights.md).
