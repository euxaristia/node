## 2024-05-24 - [SQL LIKE Injection]
**Vulnerability:** Unescaped wildcards in user-provided prefix for LIKE query.
**Learning:** `sqlx` `bind` does not escape `LIKE` wildcards (`%`, `_`), allowing broader search scopes.
**Prevention:** Always escape `\`, `%`, and `_` and append `ESCAPE '\\'` clause to the SQL query when user input is used in `LIKE` filters.
