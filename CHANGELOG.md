# Changelog

All notable changes to this project will be documented in this file.

The format is based on Keep a Changelog and this project adheres to Semantic Versioning.

## [Unreleased]

### Added

- Tests: added GitHub Actions workflow `test-merge-coverage.yml` to validate the composite action using synthetic nyc coverage files and assert merged totals.
- CI: added `check-action-yml.yml` to validate `action.yml` structure on PRs and pushes.
- Release tooling: added `set-required-checks.yml` and optional branch-protection steps to configure required status checks via `gh`/ADMIN_TOKEN.
- Action: ensure output directory is created before generating reports (fixes CI failure when output dir missing).

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
