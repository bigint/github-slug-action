# Linux Usage Guide

## Overview

Guidelines for using GitHub Slug Action in Linux environments with specific considerations and best practices.

## Linux-Specific Setup

### Basic Configuration

```yaml
name: Linux Build
runs-on: ubuntu-latest
steps:
  - uses: rlespinasse/github-slug-action@v5
```

### Shell Integration

```yaml
steps:
  - uses: rlespinasse/github-slug-action@v5
  - run: |
      echo "Branch: ${{ env.GITHUB_REF_SLUG }}"
      echo "Path: $GITHUB_WORKSPACE/${{ env.GITHUB_REF_SLUG }}"
    shell: bash
```

## Common Linux Scenarios

### Bash Usage

```yaml
steps:
  - uses: rlespinasse/github-slug-action@v5
  - shell: bash
    run: |
      echo "Current branch: ${GITHUB_REF_SLUG}"
      echo "Working directory: ${GITHUB_WORKSPACE}/${GITHUB_REF_SLUG}"
    shell: bash
```

### File Operations

```yaml
steps:
  - uses: rlespinasse/github-slug-action@v5
  - run: |
      mkdir -p "build/${GITHUB_REF_SLUG}"
      touch "build/${GITHUB_REF_SLUG}/build.log"
    shell: bash
```

## Best Practices

- Use proper file permissions
- Handle path separators
- Implement error checking
- Quote variable expansions
- Follow shell scripting standards

## Shell Features

- Variable expansion
- Command substitution
- Path manipulation
- File operations
- Environment variables

## Related Documentation

- [Windows Usage](windows-usage.md)
- [URL Usage](url-usage.md)
- [Version Variables](version-variables.md)

Need help? [Open an issue](https://github.com/rlespinasse/github-slug-action/issues/new)
