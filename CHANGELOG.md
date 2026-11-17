# Changelog

All notable changes to api.live. Versions follow [semantic versioning](https://semver.org/).

## [0.1.0] - 2026-11-14

The first public release: **macOS** (Apple silicon and Intel), **Windows** (setup .exe and .msi, x64) and
**Linux** (.deb and AppImage, x64), plus the `api` CLI for all three.

The macOS app is signed with an Apple Developer ID and notarized by Apple, so it opens with a plain
double-click. The Windows installers are not code-signed yet (SmartScreen asks once: More info → Run anyway).

### The desktop app

- **API client.** Params, headers, JSON / form / multipart / GraphQL bodies, auth (Basic, Bearer,
  API key, Digest, AWS SigV4, JWT, OAuth 2.0 client credentials / authorization code / password /
  device code), chaining (`$.token → env.TOKEN`), history with no entry cap, and code snippets for
  22 targets in 14 languages.
- **Your files, in your repo.** One small YAML file per request under `.apilive/`, secrets in
  git-ignored files, and live reload when teammates pull.
- **Format version on `.apilive` files.** Saved YAML files carry `format_version`; older and newer
  files mix in one workspace, a newer file loads with a warning, and saves keep fields this build
  doesn't understand.
- **Environments as one table** (⌘E): variables × environments, an "All environments" column every
  environment inherits from, and per-variable secret toggles.
- **Secrets from where they already live:** 1Password, HashiCorp Vault, AWS Secrets Manager, Azure
  Key Vault, Google Secret Manager, Infisical, Bitwarden, the OS keychain, env vars or `.env` files,
  resolved at send time and never written to disk in clear.
- **Import** from Postman, Bruno, Insomnia, HAR, OpenAPI / Swagger, `.http`, Hurl and cURL.
  **Export** to OpenAPI 3.1, Postman v2.1, `.http` and HTML, plus a static docs site.
- **Last Known Good.** Every 2xx request and response is snapshotted; restore the request that
  worked, or diff against the good response.
- **API simulator.** Each simulated API runs as its own service on its own port; static or
  templated responses, stateful CRUD, delays and chaos; mock a whole OpenAPI spec; turn any saved
  request or history entry into a running service in one click.
- **Load testing built in.** Virtual users, weighted requests, whole collections or complete flows,
  fixed-rate or concurrent, ramp / spike / stress / soak stages, pass/fail thresholds for CI. Measured
  at 90k+ requests per second from a laptop against a local target. Load tests against public hosts
  are capped at 2,000 req/s unless you explicitly lift the cap.
- **Flows.** Automated multi-step tests with checks, baselines with classified diffs, failure triage
  (flake rate, the commit it broke on, CODEOWNERS owner), 38 starter templates, and export to 20 test
  frameworks (Karate, REST Assured, pytest, Jest, Playwright, k6, Go, xUnit, RSpec and more).
- **Codebase discovery.** Finds OpenAPI specs and routes in 125 frameworks across 28 languages and
  turns them into requests.
- **API design.** Edit your OpenAPI 3.1 file visually with a live YAML preview and a linter;
  breaking-change review against a base branch; consumer contracts derived from your flows.
- **Monitors.** Run a request, folder or flow on a schedule and alert the desktop or a webhook when
  it breaks and when it recovers.
- **More protocols and tools:** an MCP server debugger, Socket.IO, Redis steps in flows and a capture
  proxy that records real traffic. Database features (seeding, test data sets, `db` flow steps) are
  switched off in this release.
- **Fast at scale.** A 10,000-request workspace opens in under a second; ⌘K searches in under 2 ms;
  a 100 MB JSON response shows its first screen in under 0.4 s without blocking the UI.
- A full native menu bar, keyboard shortcuts for everything (⌘/ lists them), light and dark themes.

### The `api` command-line tool

- One binary for macOS (arm64, x64), Windows (x64) and Linux (x64, arm64): `api run`, `api load`, `api flow run`, `api mock`,
  `api index`, `api capture`, `api review`, `api spec`, `api docs build`, `api monitor`, and more.
  `api --help` lists every command.
- JUnit, TAP, Allure and HTML reports and exit codes for CI.
- `api mcp` gives AI agents (Claude, Cursor, Windsurf) 61 tools to run, test, mock and benchmark
  your APIs.

### Privacy

No account, no cloud, no telemetry. api.live talks only to the hosts you send requests to and the
alert webhook you configure.

### Known limitations

- macOS is signed and notarized; the Windows installers are not code-signed yet (SmartScreen asks
  first: More info → Run anyway).
- Not yet on Homebrew, npm, PyPI or crates.io; download from the release page.
