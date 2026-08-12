## 2024-08-12 - [SQL Wildcard Injection in LIKE Clause]
**Vulnerability:** Found a SQL injection vector in `list_ref_certificates_by_prefix` where the user-provided `prefix` string was interpolated into a `LIKE` pattern (`format!("{}%", prefix)`) without escaping SQL wildcard characters (`%`, `_`, `\`).
**Learning:** In PostgreSQL (via sqlx), if user input is passed into a `LIKE` clause, an attacker can input wildcards (like `%` or `_`) to alter the matching logic, potentially causing performance degradation (DoS via expensive wildcard matching) or unintended data exposure.
**Prevention:** Always escape `%`, `_`, and `\` in user inputs before appending wildcards in application code, and append `ESCAPE '\'` to the `LIKE` clause in the SQL statement.
