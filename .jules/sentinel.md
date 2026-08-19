## 2024-05-24 - [CRITICAL] Fix uppercase header causing runtime panic
**Vulnerability:** In `crates/gitlawb-node/src/api/repos.rs`, `"X-Total-Count"` was used as a string literal when inserting a header in Axum.
**Learning:** Axum panics at runtime if a string literal containing uppercase letters is used for a header name due to implicit `IntoHeaderName` conversion, creating a DoS vulnerability.
**Prevention:** Always use `axum::http::header::*` constants or lowercase string literals (e.g. `"x-total-count"`) for custom headers.
