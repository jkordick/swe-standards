# 🏛️ SWE Standards

Centralized software engineering standards and compliance automation.

This repository defines baseline standards that all projects should follow. A daily GitHub Actions workflow checks configured target repositories and opens PRs to fix any drift — **no setup needed in the target repos**.

## How it works

```
┌───────────────────────┐
│  swe-standards repo     │
│                         │         ┌──────────────────────┐
│  repos.yml              │──check─▶│  programmier_bar      │
│  standards/             │         │  (opens PR if drift)  │
│  templates/             │         └──────────────────────┘
│  .github/workflows/    │
│    compliance-check.yml │         ┌──────────────────────┐
│                         │──check─▶│  another-project      │
│  Daily cron + manual    │         │  (opens PR if drift)  │
└───────────────────────┘         └──────────────────────┘
```

1. **Standards live here** — YAML rules and Markdown templates
2. **`repos.yml` lists target repos** — add any repo you want to govern
3. **Daily workflow runs** — checks each repo in parallel via matrix strategy
4. **Auto-fix PRs** — pushed directly to target repos when drift is found

## Setup

### 1. Create a Personal Access Token

The workflow needs cross-repo access. Create a **fine-grained PAT** with:
- **Repository access**: All target repos listed in `repos.yml`
- **Permissions**: Contents (read/write), Pull Requests (read/write)

Add it as a repository secret named `COMPLIANCE_TOKEN` in this repo.

### 2. Add repos to `repos.yml`

```yaml
repositories:
  - owner: jkordick
    repo: programmier_bar
    description: Space Devs project
```

### 3. Trigger manually or wait for schedule

Go to **Actions > Standards Compliance Check > Run workflow**.

Optionally filter to a single repo: `jkordick/programmier_bar`.

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
