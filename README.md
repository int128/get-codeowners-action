# find-codeowners-action [![ts](https://github.com/int128/find-codeowners-action/actions/workflows/ts.yaml/badge.svg)](https://github.com/int128/find-codeowners-action/actions/workflows/ts.yaml)

This action finds the owners from CODEOWNERS.

## Getting Started

### Notify a workflow run event to the owners

```yaml
on:
  workflow_run:
    types:
      - completed

jobs:
  notify-workflow-run:
    runs-on: ubuntu-latest
    steps:
      - id: codeowners
        uses: int128/find-codeowners-action@v1
        with:
          codeowners: .github/CODEOWNERS
          find-by-path: ${{ github.event.workflow.path }}
      - run: echo '${{ steps.codeowners.outputs.owner-teams }}'
```

### Inputs

| Name           | Default    | Description             |
| -------------- | ---------- | ----------------------- |
| `codeowners`   | (required) | Filename of CODEOWNERS  |
| `find-by-path` | (required) | Path to find the owners |

### Outputs

| Name                               | Description                            |
| ---------------------------------- | -------------------------------------- |
| `owners`                           | Owners                                 |
| `team-owners`                      | Team owners in the form of `@org/team` |
| `team-owners-without-organization` | Team owners in the form of `@team`     |
