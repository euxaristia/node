## 2026-08-10 - SQL Injection via Unescaped LIKE Pattern
**Vulnerability:** The `list_ref_certificates_by_prefix` function constructs a SQL `LIKE` pattern using unescaped user input (`format!("{}%", prefix)`).
**Learning:** This allows wildcard injection. If a user provides `_` or `%` in the `prefix`, they act as wildcards rather than literal characters. While likely a minor DoS or logic bypass issue here, it's a structural flaw whenever user input flows directly into `LIKE` clauses without an `ESCAPE` clause and sanitization.
**Prevention:** Always escape SQL wildcards (`%`, `_`, `\`) in user input before using it in a `LIKE` pattern, and append ` ESCAPE '\'` to the SQL query to ensure wildcards are interpreted literally.
