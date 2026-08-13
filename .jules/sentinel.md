## 2024-05-24 - LIKE Injection via unescaped string
**Vulnerability:** User input passed into SQL `LIKE` queries without escaping can act as wildcards (`%`, `_`), bypassing intended prefix constraints.
**Learning:** `sqlx` parameters do not automatically escape `LIKE` wildcards. Also, when appending `ESCAPE '\'` to the query string in Rust, the correct Rust string literal is `ESCAPE '\\'` (two backslashes). Using `ESCAPE '\''` is incorrect and actually evaluates to `ESCAPE ''` which causes a SQL syntax error.
**Prevention:** Always sanitize user input passing into a `LIKE` pattern with `s.replace('\\', "\\\\").replace('%', "\\%").replace('_', "\\_")` and append `ESCAPE '\\'` to the query.
