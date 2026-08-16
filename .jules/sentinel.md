## 2025-02-14 - Fix SQL injection in LIKE clause
**Vulnerability:** SQL wildcard injection in `list_ref_certificates_by_prefix` due to unescaped user input in a `LIKE` clause.
**Learning:** `sqlx` parameters bound to `LIKE` clauses are literal strings but Postgres still parses `%` and `_` inside them as wildcards.
**Prevention:** Sanitize user input by escaping `%`, `_`, and `\` with `\` and append `ESCAPE '\\'` to the SQL query.
