# Quick Start Guide

## Installation

```yaml
- uses: rlespinasse/github-slug-action@v5
```

## Basic Example

```yaml
name: Example Workflow
on: [push]

jobs:
  example:
    runs-on: ubuntu-latest
    steps:
      - uses: rlespinasse/github-slug-action@v5
      - name: Print Slugs
        run: |
          echo "Repository: ${{ env.GITHUB_REPOSITORY_SLUG }}"
          echo "Branch: ${{ env.GITHUB_REF_SLUG }}"
          echo "SHA: ${{ env.GITHUB_SHA_SHORT }}"
        shell: bash
```

## Key Features

- 🔄 Automatic slug generation
- 🔒 URL-safe variable creation
- 💨 Zero configuration needed
- ⚡ Instant availability

## Common Variables

| Original              | Slug Version             | Example               |
| --------------------- | ------------------------ | --------------------- |
| `feature/new-page`    | `GITHUB_REF_SLUG`        | `feature-new-page`    |
| `octocat/Hello-World` | `GITHUB_REPOSITORY_SLUG` | `octocat-hello-world` |
| `a1b2c3d4e5f6`        | `GITHUB_SHA_SHORT`       | `a1b2c3d4`            |

## Next Steps

1. Check [available variables](../variables/overview.md)
2. See [usage examples](../guides/common-patterns.md)
3. Review [best practices](../guides/best-practices.md)

Need help? [Open an issue](https://github.com/rlespinasse/github-slug-action/issues/new)
