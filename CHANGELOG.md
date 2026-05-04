# Changelog

## [2.1.0] - 2026-05-04

### Bug Fixes

- **Guard against missing `coverage-final.json`** — Subdirectories under `coverage-reports` that do not contain a `coverage-final.json` file are now skipped with a warning instead of causing the action to fail. Only `ENOENT` errors are silently skipped; all other filesystem errors are still propagated. (#4)
- **Fix action author field** — Corrected the `author` field in `action.yml`.

### Improvements

- **Add CI status badge to README** — A test workflow status badge is now displayed in the README.
- **Strengthen test assertions** — The end-to-end test workflow now verifies the step exit status in addition to output content.

## [2.0.0] - 2026-02-21

### Breaking Changes

- Action outputs now use `$GITHUB_OUTPUT` (requires runner v2.298.2+). All modern GitHub-hosted runners support this.

### Security

- Fix command injection vulnerabilities — all user inputs are now passed via environment variables.
- Pin action dependencies to full commit SHAs.
- Validate reporter format names against a strict regex.

### Bug Fixes

- Fix broken action outputs (`report` and `json-summary` were always empty).
- Replace deprecated `::set-output` with `$GITHUB_OUTPUT`.
- Fix `.json.json` double extension when collecting coverage files.
- Fix `mkdir` failure on existing directory.
- Remove dead conditionals.

### Improvements

- Replace global `npm install` of `nyc` with `npx`.
- Use `path.join()` for path construction.
- Update `actions/setup-node` v5 → v6, `actions/github-script` v7 → v8, `actions/upload-artifact` v4 → v6.

## [1.2.0] - 2025-09-04

- Update Node 16 to Node 20.
- Update GitHub Actions dependencies to latest versions.
