# <img align="left" width="45" height="45" src="https://user-images.githubusercontent.com/1610100/201473670-e0e6bdeb-742f-4be1-a47a-3506309620a3.png"> Terraform Google Cloud Platform Called Workflows

Reusing workflows avoids duplication. This makes workflows easier to maintain and allows you to create new workflows
more quickly by building on the work of others, just as you do with actions.

Workflow reuse also promotes best practice by helping you to use workflows that are well designed, have already been
tested, and have been proved to be effective. Your organization can build up a library of reusable workflows that can
be centrally maintained.

## Reusing Workflows

Rather than copying and pasting from one workflow to another, you can make workflows [reusable](https://docs.github.com/en/actions/learn-github-actions/reusing-workflows). You and anyone with access to the reusable workflow can then call the reusable workflow from another workflow.

### Example Usage

```yaml
name: Dependabot

on: pull_request_target

permissions:
  pull-requests: write
  contents: write

jobs:
  dependabot:
    name: Pull Request Approve and Merge
    uses: osinfra-io/github-misc-called-workflows/.github/workflows/dependabot.yml@v0.0.0
    secrets:
      github_token: ${{ secrets.GITHUB_TOKEN }}
```
