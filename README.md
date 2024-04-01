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

The environment tag should follow one of these patterns:

- `v[0-9].[0-9].[0-9]` -> **production**.
- `v[0-9].[0-9].[0-9]-uat.[0-9]` -> **uat**.

The Action uses `github.ref_name` to determine the branch or tag name.

## Usage

See [action.yml](action.yml) for more info about the action.

```yaml
- uses: gbh-tech/check-semantic-release@v0.1.0
```

### Examples

```yaml
jobs:
  deploy:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - uses: gbh-tech/check-semantic-release@v0.1.0
```
