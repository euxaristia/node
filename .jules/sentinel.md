## 2026-08-10 - [Fix SQL LIKE Wildcard Injection in Profile Lookup]
**Vulnerability:** Unescaped wildcard characters in the `did` input for the `LIKE '%:' || $1` clause inside `get_profile`.
**Learning:** The SQL `LIKE` clause doesn't automatically escape '%' and '_' even if they are passed as bound parameters via sqlx. This can lead to wildcard injection attacks and unexpected query matches.
**Prevention:** Whenever user input is dynamically included within a `LIKE` condition, explicitly escape '%', '_', and '\' characters in Rust, and use `ESCAPE '\\'` explicitly within the query.
