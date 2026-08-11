## 2024-08-11 - Use `verify_strict` for Ed25519 signature verification
**Vulnerability:** Signature malleability in Ed25519 signatures due to `verify` instead of `verify_strict`.
**Learning:** `ed25519-dalek` provides a standard `verify` method that doesn't strictly adhere to RFC 8032 requirements for non-malleability, leading to multiple valid signatures for the same message.
**Prevention:** Use `verify_strict` when verifying Ed25519 signatures using `ed25519-dalek` to ensure RFC 8032 compliance.
