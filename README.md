# 🏛️ SWE Standards

Organization-wide software engineering standards and templates.

This repository defines the baseline standards that all projects should comply with. A daily GitHub Actions workflow checks target repositories against these rules and opens PRs to fix any drift.

## How it works

1. **Standards are defined here** — in structured YAML rules and Markdown templates
2. **Target repos include the compliance workflow** — a scheduled GitHub Actions job
3. **The workflow fetches standards** — clones this repo and runs checks
4. **Drift is auto-fixed** — if a repo is out of compliance, a PR is opened with the necessary changes

## Standards

| Standard | File | Description |
|----------|------|-------------|
| Required files | [`standards/required-files.yml`](standards/required-files.yml) | Files every repo must have |
| README structure | [`standards/readme-rules.yml`](standards/readme-rules.yml) | Required sections in README |
| Architecture docs | [`standards/architecture-rules.yml`](standards/architecture-rules.yml) | Architecture diagram requirements |
| Naming conventions | [`standards/naming-rules.yml`](standards/naming-rules.yml) | Package/class naming rules |

## Templates

| Template | File |
|----------|------|
| CONTRIBUTING.md | [`templates/CONTRIBUTING.md`](templates/CONTRIBUTING.md) |
| SECURITY.md | [`templates/SECURITY.md`](templates/SECURITY.md) |
| copilot-instructions.md | [`templates/copilot-instructions.md`](templates/copilot-instructions.md) |
| Architecture doc | [`templates/architecture.md`](templates/architecture.md) |

## Adding compliance to a repo

Copy `.github/workflows/compliance-check.yml` from this repo into your target repository and configure the schedule.
