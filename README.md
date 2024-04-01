<!-- omit in toc -->
# Check Semantic Release

<!-- omit in toc -->
## Content

- [Overview](#overview)
- [Environments](#environments)
- [Environment mapping](#environment-mapping)
- [Usage](#usage)
  - [Examples](#examples)

## Overview

This GitHub Action facilitates setting checking if tag follow our convention.

> ⚠️ This action is tailored for our specific needs and development workflow,
> at this moment, you cannot change the triggering events or the environment
> tag. Only use if you can adapt it on your workflow!

## Environments

This action can output the following environment names:

- `stage`
- `uat`
- `production`

## Environment mapping

The environment name mapping is as follows:

- Push event on a branch with name `main` -> Outputs environment **stage**.
- Tag push matching `v[0-9].[0-9].[0-9]-uat.[0-9]` -> Outputs **uat**.
- Tag matching `v[0-9].[0-9].[0-9]` -> Outputs **production**.

The Action uses `github.ref_name` to determine the branch or tag name.

## Usage

See [action.yml](action.yml) for more info about the action.

```yaml
- uses: gbh-tech/check-semantic-release@v0.0.1
  id: env
```

### Examples

```yaml
jobs:
  deploy:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - uses: gbh-tech/check-semantic-release@v0.1.0
        id: env
      # Using outputs
      - name: Show the selected environment name using output
        env:
          ENVIRONMENT: ${{ steps.env.outputs.environment }}
        run: echo "Environment is ${ENVIRONMENT}"
      # Using env. context
      - name: Show the selected environment name using env context
        run: echo "Environment is ${{ env.ENVIRONMENT }}"
```
