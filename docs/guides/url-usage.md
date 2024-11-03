# URL Usage Guide

## Overview

Learn how to use URL-safe variables for web-friendly references in your workflows.

## Available URL Variables

| Variable               | Description             | Input Example                  | Output Example         |
| ---------------------- | ----------------------- | ------------------------------ | ---------------------- |
| `GITHUB_REF_SLUG`      | URL-safe reference name | `refs/heads/feature/new-stuff` | `feature-new-stuff`    |
| `GITHUB_HEAD_REF_SLUG` | URL-safe head reference | `feature/user/testing`         | `feature-user-testing` |
| `GITHUB_BASE_REF_SLUG` | URL-safe base reference | `main/prod`                    | `main-prod`            |

## Usage Examples

### Dynamic URLs

```yaml
name: Deploy Preview
steps:
  - uses: rlespinasse/github-slug-action@v5
  - run: |
      echo "Preview URL: https://preview-${{ env.GITHUB_REF_SLUG }}.example.com"
    shell: bash
```

### Artifact Naming

```yaml
name: Build Assets
steps:
  - uses: rlespinasse/github-slug-action@v5
  - uses: actions/upload-artifact@v3
    with:
      name: build-${{ env.GITHUB_REF_SLUG }}
      path: dist/
```

## Transformation Rules

- Converts to lowercase
- Replaces spaces with hyphens
- Removes special characters
- Trims leading/trailing hyphens
- Collapses multiple hyphens

## Common Use Cases

- Preview environments
- Artifact identification
- URL routing
- Branch-specific deployments
- Resource naming

## Best Practices

- Validate URL length limits
- Test with special characters
- Consider case sensitivity
- Document URL patterns
- Handle URL collisions

## Related Documentation

- [Slug Variables](slug-variables.md)
- [Version Variables](version-variables.md)
- [Migration Guide](migration-guide.md)

Need help? [Open an issue](https://github.com/rlespinasse/github-slug-action/issues)
