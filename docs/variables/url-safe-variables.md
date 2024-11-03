# URL-Safe Variables

## Overview

URL-safe variables ensure GitHub environment variables can be safely used in URLs and file paths.

## Available Variables

| Variable                     | Description     | Input Example         | Output Example        |
| ---------------------------- | --------------- | --------------------- | --------------------- |
| `GITHUB_EVENT_NAME_URL_SAFE` | Event name      | `pull_request`        | `pull-request`        |
| `GITHUB_ACTOR_URL_SAFE`      | Actor username  | `john.doe`            | `john-doe`            |
| `GITHUB_REPOSITORY_URL_SAFE` | Repository path | `My-Org/Project.Name` | `my-org/project-name` |

## Transformation Rules

The following rules are applied to create URL-safe values:

- Replaces underscores with hyphens
- Converts to lowercase
- Removes special characters
- Preserves forward slashes
- Maintains alphanumeric characters

## Usage Examples

### URL Generation

```yaml
name: Generate URLs
steps:
  - uses: rlespinasse/github-slug-action@v5
  - run: |
      echo "DEPLOY_URL=https://${{ env.GITHUB_ACTOR_URL_SAFE }}.example.com" >> $GITHUB_ENV
```

### File Path Creation

```yaml
name: Create Paths
steps:
  - uses: rlespinasse/github-slug-action@v5
  - run: |
      mkdir -p "artifacts/${{ env.GITHUB_EVENT_NAME_URL_SAFE }}"
```

## Common Use Cases

- Web endpoint creation
- Storage path generation
- Resource naming
- URL routing
- File organization

## Best Practices

- Validate transformed values
- Use consistent patterns
- Document transformations
- Test edge cases
- Consider URL length limits

## Related Documentation

- [Slug Variables](slug-variables.md)
- [Repository Variables](repository-variables.md)
- [Event Variables](event-variables.md)

Need help? [Open an issue](https://github.com/rlespinasse/github-slug-action/issues)
