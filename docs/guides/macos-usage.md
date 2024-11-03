# macOS Usage Guide

## Overview

Guidelines for using GitHub Slug Action in macOS environments with specific considerations and best practices.

## macOS-Specific Setup

### Basic Configuration

```yaml
name: macOS Build
runs-on: macos-latest
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

## Common macOS Scenarios

### Bash Usage

```yaml
steps:
  - uses: rlespinasse/github-slug-action@v5
  - shell: bash
    run: |
      echo "Current branch: ${GITHUB_REF_SLUG}"
      echo "Working directory: ${GITHUB_WORKSPACE}/${GITHUB_REF_SLUG}"
```

### Xcode Integration

```yaml
steps:
  - uses: rlespinasse/github-slug-action@v5
  - run: |
      xcodebuild -scheme "MyApp" \
        -configuration Release \
        -derivedDataPath "build/${GITHUB_REF_SLUG}"
    shell: bash
```

## Best Practices

- Handle case sensitivity
- Use proper file permissions
- Quote path variables
- Consider Unicode support
- Follow POSIX compliance

## Shell Features

- Variable expansion
- Command substitution
- Path manipulation
- File operations
- Environment variables

## Related Documentation

- [Linux Usage](linux-usage.md)
- [Windows Usage](windows-usage.md)
- [URL Usage](url-usage.md)

Need help? [Open an issue](https://github.com/rlespinasse/github-slug-action/issues/new)
