# Changelog

All notable changes to this project will be documented in this file.

The format is based on Keep a Changelog and this project adheres to Semantic Versioning.

## [Unreleased]

## [2.1.0] - 2026-05-04

### Bug Fixes
- **Guard against missing `coverage-final.json`** — Subdirectories under `coverage-reports` that do not contain a `coverage-final.json` file are now skipped with a warning instead of causing the action to fail. Only `ENOENT` errors are silently skipped; all other filesystem errors are still propagated. (#4)
- **Fix action author field** — Corrected the `author` field in `action.yml`.

### Improvements
- **Add CI status badge to README** — A test workflow status badge is now displayed in the README.
- **Strengthen test assertions** — The end-to-end test workflow now verifies the step exit status in addition to output content.

## [2.0.0] - 2026-02-21

- Add `test-merge-coverage.yml` workflow that:
  - Generates synthetic Istanbul/nyc coverage files for multiple services
  - Runs the composite action in-repo to merge coverage
  - Validates `coverage-summary.json` totals and textual report contents
  - Optionally configures branch protection via `gh` when `ADMIN_TOKEN` secret is present
- Add `check-action-yml.yml` workflow to validate `action.yml` keys and required inputs.
- Add `set-required-checks.yml` workflow to programmatically set required status checks (requires admin token).
- Improve `action.yml` composite action: create output folder before running `nyc report`.

### Fixed

- Ensure fake coverage files produced during tests are nyc-compatible (statementMap/s counts) so `npx nyc merge` succeeds.

### Notes

- To enable automatic branch-protection configuration from CI, add a repository secret `ADMIN_TOKEN` containing a personal access token with `repo` (admin) scope. The test workflow will skip configuration if the secret is missing.

---

This changelog entry was generated automatically by tooling in the repository.
