<!-- omit in toc -->
# Check Semantic Release

<!-- omit in toc -->
## Content

- [Overview](#overview)
- [Environment pattern](#environment-pattern)
- [Usage](#usage)
  - [Examples](#examples)

## Overview

This GitHub Action facilitates setting checking if tag follow our convention.

> ⚠️ This action is tailored for our specific needs and development workflow,
> at this moment, you cannot change the triggering events or the environment
> tag. Only use if you can adapt it on your workflow!

## Environment pattern

The environment tag should follow one of these patterns to match our convention:

- `v[0-9].[0-9].[0-9]`
- `v[0-9].[0-9].[0-9]-uat.[0-9]`

The Action uses `github.ref_name` to determine the tag name.

## Usage

See [action.yml](action.yml) for more info about the action.

```yaml
- uses: gbh-tech/check-semantic-release@v0.1.2
```

### Examples

```yaml
jobs:
  deploy:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - uses: gbh-tech/check-semantic-release@v0.1.2
```
