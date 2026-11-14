# Security policy

## Reporting a vulnerability

Please report security problems privately, **not** in a public issue:

- Email: `security@<domain>` <!-- TODO(owner): replace with the real mailbox once the domain is set up (release.env SECURITY_EMAIL, then `node scripts/release-config.mjs apply`). -->
- Or use GitHub's private reporting: **Security → Report a vulnerability** on this repository.

Include the api.live version (`api --version`, or **Help → Copy Diagnostics** in the app), your operating
system (macOS, Windows or Linux, version and chip), what you did, what happened, and the impact you see. A proof of concept helps.

What to expect (we aim for):

- an acknowledgement within 3 working days,
- an assessment and a planned fix date within 10 working days,
- credit in the release notes when the fix ships, if you want it.

Please give us a reasonable time to ship a fix before disclosing publicly.

## Supported versions

Security fixes go into the latest release. Update to it before reporting if you can.

## Scope

In scope: the api.live desktop app, the `api` CLI and its MCP server (`api mcp`), as published in this
repository's releases.

Especially interesting: anything that sends your data somewhere you did not ask for, leaks secrets
(secret files, OS keychain, provider credentials) into files, logs, history or exports, lets a
workspace you open or a server you call run code on your machine without your consent, or weakens
TLS verification you configured.

Out of scope: problems in the third-party APIs you call with api.live, and findings that need an
attacker who already controls your user account.
