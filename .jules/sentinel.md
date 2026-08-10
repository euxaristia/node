## 2024-08-08 - [Use strict Ed25519 signature verification]
**Vulnerability:** Signature verification in `gitlawb-core/src/identity.rs` used `verifying_key.verify(msg, &sig)`, which is permissive and susceptible to signature malleability.
**Learning:** `ed25519-dalek` v2.0+ provides `verify_strict` to enforce strict RFC 8032 compliance, rejecting non-canonical signatures.
**Prevention:** Always use `verify_strict` for Ed25519 signature validation to prevent malleability attacks.
