## 2024-05-24 - Command Injection in Git Clone
**Vulnerability:** User-controlled paths passed to `std::process::Command::new("git").arg("clone")` could be interpreted as flags if they started with `-`.
**Learning:** `git clone` arguments parsed from external sources (e.g. database values, user inputs) can trigger unexpected behavior or arbitrary command execution if a path resembling a flag is supplied.
**Prevention:** Always use `--` to signify the end of options before passing positional arguments to `git clone` (and similar commands) within `std::process::Command`.
