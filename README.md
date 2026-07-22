# yarn-playwright

Composite GitHub Action that installs Playwright browsers, runs yarn e2e tasks, and uploads reports.

## Usage

```yaml
- name: Run Playwright e2e tests
  uses: equisoft-actions/yarn-playwright@v1
  with:
    working-directory: ./path/to/frontend/web
    pre-command: yarn <optional-setup-task>
```

Assumes dependencies are already installed (`yarn-install`) and Node is available (`with-asdf-vm`).

## Inputs

| Input | Default | Description |
|-------|---------|-------------|
| `working-directory` | `.` | Project directory |
| `pre-command` | `""` | Optional shell command before tests |
| `install-task-name` | `test:e2e:install` | Yarn task to install browsers |
| `task-name` | `test:e2e` | Yarn task to run tests |
| `report-name` | `typescript-e2e-results.junit.xml` | JUnit artifact name |
| `debug-report-name` | `typescript-e2e-debug` | HTML report and trace artifact name |
| `report-retention-days` | `5` | Artifact retention in days |

## Reports

Paths are relative to `working-directory`.

| Artifact | Path | If missing |
|----------|------|-------------------|
| JUnit | `build/playwright/junit.xml` | fails the step |
| HTML report | `build/playwright/report/` | skipped |
| Traces | `build/playwright/results/` | skipped |

Configure Playwright reporters in `{working-directory}` to write under `build/playwright/`.
