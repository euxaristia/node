
## 2026-08-18 - Axum Header String Literal Panic
**Vulnerability:** Application crashes (Denial of Service) when inserting custom headers into Axum HTTP responses using uppercase string literals (e.g., `"X-Total-Count"`).
**Learning:** Axum uses `HeaderName` which implicitly converts string literals via `IntoHeaderName`. The conversion expects all string literals to be entirely lowercase. If any uppercase letters are present, the conversion panics at runtime. This can lead to unhandled crashes if an endpoint receives requests triggering this path.
**Prevention:** Always use lowercase string literals (e.g., `"x-total-count"`) when inserting headers manually, or preferably use `axum::http::header::*` constants.
