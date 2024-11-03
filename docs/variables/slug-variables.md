# Slug Variables

## Overview

GitHub Slug Action provides URL-safe versions of GitHub environment variables.

## Core Variables

| Variable                 | Description           | Input Example                 | Output Example         |
| ------------------------ | --------------------- | ----------------------------- | ---------------------- |
| `GITHUB_REF_SLUG`        | Current branch or tag | `refs/heads/feature/new-page` | `feature-new-page`     |
| `GITHUB_REPOSITORY_SLUG` | Full repository path  | `Octo-Corp/My-Project`        | `octo-corp-my-project` |
| `GITHUB_SHA_SHORT`       | Short commit SHA      | `a1b2c3d4e5f6g7h8`            | `a1b2c3d4`             |

## Transformation Rules

All variables undergo these transformations:

- Converts to lowercase
- Replaces spaces with hyphens
- Removes special characters
- Maintains alphanumeric characters
- Preserves existing hyphens

## Common Use Cases

- URL generation
- Docker image tagging
- Environment naming
- File path creation
- Resource identification

## Usage Examples

### Docker Images

```yaml
name: Build
steps:
  - uses: rlespinasse/github-slug-action@v5
  - run: docker build -t app:${{ env.GITHUB_SHA_SHORT }} .
```

### Deployment URLs

```yaml
name: Deploy
steps:
  - uses: rlespinasse/github-slug-action@v5
  - run: echo "URL=https://${{ env.GITHUB_REF_SLUG }}.dev.com" >> $GITHUB_ENV
```

## Best Practices

- Use consistent naming patterns
- Combine slugs for unique identifiers
- Validate transformed values
- Document usage in workflows
- Consider variable availability

## Related Documentation

- [Repository Variables](repository-variables.md)
- [Reference Variables](reference-variables.md)
- [Branch Variables](branch-variables.md)

Need help? [Open an issue](https://github.com/rlespinasse/github-slug-action/issues)
