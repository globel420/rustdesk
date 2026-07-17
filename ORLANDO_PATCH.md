# Orlando Family Support RustDesk patch

This branch is based on RustDesk 1.4.9 and adds one Windows-only command:

```text
rustdesk.exe --get-temporary-password
```

The command asks the already-running RustDesk process for its built-in temporary
password through RustDesk's existing local IPC channel. On success it writes one
line to standard output and exits with code 0. It exits without password output
when IPC is unavailable or the request is invalid.

The command exists so the consent-first Orlando Family Support launcher can send
the temporary password to a password-protected family dashboard only after the
parent explicitly clicks **Allow Orlando**. The launcher and dashboard are
designed not to persist or log the password.

The included GitHub Actions workflow performs an unsigned Windows x64 Flutter
portable build. RustDesk remains licensed under the GNU AGPL v3; see `LICENCE`.
