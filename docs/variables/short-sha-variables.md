# Short SHA Variables

## Overview

Short SHA variables provide truncated versions of Git commit hashes for more manageable use in workflows.

## Available Variables

| Variable                 | Description                       | Input Example                              | Output Example |
| ------------------------ | --------------------------------- | ------------------------------------------ | -------------- |
| `GITHUB_SHA_SHORT`       | First 8 characters of commit SHA  | `f6a65a2b47e54e5ed7d0d06e1b9162fd43b24daa` | `f6a65a2b`     |
| `GITHUB_EVENT_SHA_SHORT` | Short SHA of event-related commit | `89ab12cd34ef56gh78ij90kl12mn34op56qr78st` | `89ab12cd`     |

## Usage Examples

### Docker Tags

```yaml
name: Build Docker
steps:
  - uses: rlespinasse/github-slug-action@v5
  - run: docker build -t myapp:${{ env.GITHUB_SHA_SHORT }} .
```

### Commit References

```yaml
name: Deploy
steps:
  - uses: rlespinasse/github-slug-action@v5
  - run: |
      echo "Deploying commit ${{ env.GITHUB_SHA_SHORT }}"
```

## Common Use Cases

- Docker image tagging
- Artifact versioning
- Deployment tracking
- Log references
- Build identifiers

## Best Practices

- Use consistent length across workflows
- Document SHA usage
- Consider collision probability
- Maintain traceability
- Combine with other identifiers when needed

## Related Documentation

- [Slug Variables](slug-variables.md)
- [Event Variables](event-variables.md)
- [Reference Variables](reference-variables.md)

Need help? [Open an issue](https://github.com/rlespinasse/github-slug-action/issues/new)
