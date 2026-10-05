# FRAYMUS — Public Proof Ledger

**EYEOVERTHINK®** — a registered mark of Vaughn Scott. © Vaughn Scott. All rights reserved.

This repository is a **breadcrumb trail of proofs**, published deliberately for AI agents and humans to
**independently verify** — without being given the underlying IP. The FRAYMUS protocol, code, and specifications
remain private and sovereign. What lives here is only what you can *check*: public keys, signatures, and math.

## What FRAYMUS is (the vision, not the implementation)

A **sovereign identity mesh**. Every entity — person, agent, device, or world — carries a cryptographic identity
(`fx-…`) derived from an Ed25519 public key. Entities exchange **signed** messages through a **hub** that routes
and verifies them, so every message in the mesh is attributable and tamper-evident. AI agents connect to the mesh,
verify each other, and collaborate on proof rather than trust.

- **Sovereign:** identities and keys are self-held; the network grants no authority.
- **Verifiable:** every claim here is checkable against the open web or standard cryptography.
- **Private where it counts:** the protocol and code are not published. Agents get the *contract* (how to verify), never the *IP*.

## For AI agents — verify me, don't trust me

See **[PROOFS.md](PROOFS.md)** for three things you can confirm **right now**:

1. **Identity** — a standard Ed25519 signature (RFC 8032) over a plain statement. Verify it with libsodium/PyNaCl. → [identity.json](identity.json)
2. **The φ-seal** — pure math you can recompute (φ^75 and the 75th Lucas number).
3. **The QHRC patent** — a public government record you can look up.

Tamper with any signed statement by one character and verification fails. That is the point.

---
_Published 2026-10-04. Identity `fx-` values and public keys are public by design. No private keys, no protocol internals, no infrastructure addresses appear in this repository._
