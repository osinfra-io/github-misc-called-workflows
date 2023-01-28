# <img align="left" width="45" height="45" src="https://user-images.githubusercontent.com/1610100/201473670-e0e6bdeb-742f-4be1-a47a-3506309620a3.png"> Miscellaneous Called Workflows

Reusing workflows avoids duplication. This makes workflows easier to maintain and allows you to create new workflows
more quickly by building on the work of others, just as you do with actions.

Workflow reuse also promotes best practice by helping you to use workflows that are well designed, have already been
tested, and have been proved to be effective. Your organization can build up a library of reusable workflows that can
be centrally maintained.

## Reusing Workflows

Rather than copying and pasting from one workflow to another, you can make workflows [reusable](https://docs.github.com/en/actions/learn-github-actions/reusing-workflows). You and anyone with access to the reusable workflow can then call the reusable workflow from another workflow.

### Workflows

- [add-to-project.yml](.github/workflows/add-to-project.yml)
- [dependabot.yml](.github/workflows/dependabot.yml)

### Example Add to Project Usage

```yaml
name: Add To GitHub Projects

on:
  issues:
    types:
      - opened
  pull_request:
    types:
      - opened

jobs:
  add-to-osinfra-project:
    name: Open Source Infrastructure (as Code)
    uses: osinfra-io/github-misc-called-workflows/.github/workflows/add-to-project.yml@v0.0.0
    with:
     project_id: 1
    secrets:
     add_to_project_pat: ${{ secrets.ADD_TO_PROJECT_PAT }}
```

### Example Dependabot Usage

```yaml
name: Dependabot

on: pull_request_target

jobs:
  dependabot:
    name: Dependabot
    uses: osinfra-io/github-misc-called-workflows/.github/workflows/dependabot.yml@v0.0.0
    secrets:
      pr_approve_and_merge_pat: ${{ secrets.PR_APPROVE_AND_MERGE_PAT }}
```
