## 2024-05-24 - [Command Argument Injection in Git Clone]
**Vulnerability:** User-controlled repository paths were passed directly to `git clone` without a `--` separator.
**Learning:** `git clone` can interpret paths starting with `-` as options. Since repository names and DIDs are derived from user input, an attacker could potentially inject arbitrary arguments (e.g., `-u` for upload-pack, or `--upload-pack`) leading to command execution or unauthorized file reads.
**Prevention:** Always use `--` before passing paths to command-line utilities like `git` to explicitly signal the end of command-line options.
