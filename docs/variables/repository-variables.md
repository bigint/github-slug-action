# Repository Variables

## Overview

Repository variables provide URL-safe slugs for repository-related GitHub environment variables.

## Available Variables

| Variable                       | Description          | Input Example          | Output Example         |
| ------------------------------ | -------------------- | ---------------------- | ---------------------- |
| `GITHUB_REPOSITORY_SLUG`       | Full repository path | `Octo-Corp/My-Project` | `octo-corp-my-project` |
| `GITHUB_REPOSITORY_OWNER_SLUG` | Repository owner     | `Octo-Corp`            | `octo-corp`            |
| `GITHUB_REPOSITORY_NAME_SLUG`  | Repository name      | `My-Project`           | `my-project`           |

## Usage Examples

### Docker Image Naming

```yaml
name: Build Docker Image
steps:
  - uses: rlespinasse/github-slug-action@v5
  - name: Build
    run: |
      docker build -t ${{ env.GITHUB_REPOSITORY_SLUG }}:latest .
```

### Deployment Paths

```yaml
name: Deploy
steps:
  - uses: rlespinasse/github-slug-action@v5
  - name: Deploy
    run: |
      deploy --path="/${{ env.GITHUB_REPOSITORY_OWNER_SLUG }}/${{ env.GITHUB_REPOSITORY_NAME_SLUG }}"
```

### URL Generation

```yaml
name: Generate URLs
steps:
  - uses: rlespinasse/github-slug-action@v5
  - name: Set URLs
    run: |
      echo "APP_URL=https://${{ env.GITHUB_REPOSITORY_SLUG }}.example.com" >> $GITHUB_ENV
```

## Transformation Rules

- Converts all characters to lowercase
- Replaces spaces and underscores with hyphens
- Removes special characters
- Maintains hyphens between components
- Preserves alphanumeric characters

## Common Use Cases

- Docker image tagging
- Subdomain generation
- Storage path creation
- Environment naming
- Resource identification

## Best Practices

- Use full repository slug for unique identifiers
- Use owner slug for organization-level resources
- Use name slug for project-specific resources
- Combine with other slugs for more specific naming

## Related Variables

- [Reference Variables](reference-variables.md)
- [Branch Variables](branch-variables.md)
- [Event Variables](event-variables.md)

Need help? [Open an issue](https://github.com/rlespinasse/github-slug-action/issues/new)
