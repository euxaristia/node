## 2024-08-11 - [SQLx LIKE wildcard injection vulnerability]
**Vulnerability:** SQL wildcard injection vulnerability in `list_ref_certificates_by_prefix`. User-provided prefix is appended with '%' and passed to `LIKE` without escaping other wildcard characters ('%', '_', '\').
**Learning:** SQLx parameterized queries do not escape SQL LIKE wildcards inside the string itself. When constructing a LIKE pattern from user input, we must manually escape the wildcards in Rust and append `ESCAPE '\'` to the SQL query.
**Prevention:** Always escape '\', '%', and '_' in user input when used inside a LIKE pattern, and explicitly specify the escape character in SQL (e.g. `LIKE  ESCAPE '\'`).
