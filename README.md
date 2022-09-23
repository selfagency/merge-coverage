# Merge Istanbul coverage reports GitHub Action

Merge Istanbul coverage reports into a single report.

Outputs:

## Inputs

All fields are required.

- `coverage-reports`: Path to coverage reports (usually `${{ github.workspace }}/coverage`);
- `output-folder`: Where to output merged reports
- `formats`: Comma-separated list of report formats (ie., `json,lcov`)
  - Options include `cobertura`, `clover`, `json`, `lcov`, `teamcity`, `text-loc`, `text`. `text-summary` and `json-summary` are always included.

## Outputs

- `summary`: Coverage summary
- `json`: JSON coverage summary
