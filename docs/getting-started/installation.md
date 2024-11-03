# Installation Guide

## Requirements

- GitHub Actions workflow
- GitHub-hosted or self-hosted runner

## Basic Installation

Add this step to your workflow:

```yaml
steps:
  - uses: rlespinasse/github-slug-action@v5
```

## Version Selection

### Latest Version (Recommended)

```yaml
- uses: rlespinasse/github-slug-action@v5
```

### Specific Version

```yaml
- uses: rlespinasse/github-slug-action@v5.2.0
```

### Main Branch (Not Recommended)

```yaml
- uses: rlespinasse/github-slug-action@v5.x
```

## Installation Options

### Minimal Setup

```yaml
steps:
  - uses: rlespinasse/github-slug-action@v5
```

### With Error Handling

```yaml
steps:
  - uses: rlespinasse/github-slug-action@v5
    id: slug
    continue-on-error: true
```

## Verification

Add this step after installation to verify:

```yaml
steps:
  - name: Verify Installation
    shell: bash
    run: |
      echo "GITHUB_REPOSITORY_SLUG: ${{ env.GITHUB_REPOSITORY_SLUG }}"
      echo "GITHUB_REF_SLUG: ${{ env.GITHUB_REF_SLUG }}"
    shell: bash
```

## Next Steps

1. Review the [Quick Start Guide](quick-start.md)
2. Explore [Available Variables](../variables/overview.md)
3. Check [Common Patterns](../guides/common-patterns.md)

## Troubleshooting

If you encounter issues:

1. Verify your workflow syntax
2. Check runner compatibility
3. Ensure proper permissions
4. Review [Troubleshooting Guide](../reference/troubleshooting.md)

Need help? [Open an issue](https://github.com/rlespinasse/github-slug-action/issues/new)
