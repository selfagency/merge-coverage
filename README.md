# Merge coverage reports GitHub Action

GitHub Action to merge coverage reports from parallelized test runners into a single report. 

## Inputs

- `source`*: Path to source code (usually `${{ github.workspace }}`)
- `coverage-reports`*: Path to coverage reports (usually `${{ github.workspace }}/coverage`)
- `output-folder`*: Where to output merged reports
- `formats`: Comma-separated list of formats to output (`text`, `json`, and `json-summary` are always included)
  - Options include `cobertura`, `clover`, `lcov`, `teamcity`, `text-loc`.

*Required field

## Outputs

- `report`: Full coverage report
- `json-summary`: JSON coverage summary
