## 2024-05-24 - SQL Wildcard Injection in Prefix Search
**Vulnerability:** SQL wildcard injection where a user-provided search prefix was concatenated directly into a `LIKE "{}%"` query without escaping.
**Learning:** Even simple prefix searches (`prefix%`) are vulnerable if `_`, `%`, or `\` are present in the input. While not a typical command injection, it can be abused for broad matches. Furthermore, `ESCAPE '\'` needs to be represented as `ESCAPE '\\'` in Rust string literals (otherwise it resolves to an empty string escape).
**Prevention:** Always escape user input strings using `.replace()` before appending them to `LIKE` wildcard searches, and ensure the `ESCAPE` clause is used securely.
