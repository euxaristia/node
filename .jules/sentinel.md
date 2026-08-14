## 2025-02-28 - Escape LIKE clauses
**Vulnerability:** SQL Injection in list_ref_certificates_by_prefix where user-controlled prefix was passed directly into a LIKE clause.
**Learning:** Using untrusted data without escaping allows wildcards like % and _ to bypass filtering. The Rust escaping syntax for ESCAPE in sqlx query is two backslashes.
**Prevention:** Always escape wildcards (\, %, _) in the user input and append ESCAPE '\' when using LIKE clauses.
