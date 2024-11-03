# Available Variables

## Core Variables

| Environment Variable     | Description           | Example Input                 | Example Output        |
| ------------------------ | --------------------- | ----------------------------- | --------------------- |
| `GITHUB_REF_SLUG`        | Current branch or tag | `refs/heads/feature/new-page` | `feature-new-page`    |
| `GITHUB_REPOSITORY_SLUG` | Repository name       | `octocat/Hello-World`         | `octocat-hello-world` |
| `GITHUB_SHA_SHORT`       | Short commit SHA      | `a1b2c3d4e5f6g7h8`            | `a1b2c3d4`            |

## Reference Variables

### Branch Related

| Variable               | Description                     | Example                           |
| ---------------------- | ------------------------------- | --------------------------------- |
| `GITHUB_REF_NAME_SLUG` | Branch name without refs/heads/ | `main` → `main`                   |
| `GITHUB_HEAD_REF_SLUG` | PR source branch                | `feature/login` → `feature-login` |
| `GITHUB_BASE_REF_SLUG` | PR target branch                | `develop` → `develop`             |

### Repository Related

| Variable                       | Description      | Example                       |
| ------------------------------ | ---------------- | ----------------------------- |
| `GITHUB_REPOSITORY_OWNER_SLUG` | Repository owner | `Octo-Corp` → `octo-corp`     |
| `GITHUB_REPOSITORY_NAME_SLUG`  | Repository name  | `My-Project` → `my-project`   |
| `GITHUB_EVENT_REF_SLUG`        | Event reference  | `refs/tags/v1.0.0` → `v1-0-0` |

## Slug Transformation Rules

- Converts to lowercase
- Replaces spaces with hyphens
- Removes special characters
- Shortens SHA to 8 characters
- Makes URLs safe

## Usage Examples

### Branch Deployments

```yaml
environment: ${{ env.GITHUB_REF_SLUG }}
url: https://${{ env.GITHUB_REF_SLUG }}.staging.com
```

### Docker Images

```yaml
image: ${{ env.GITHUB_REPOSITORY_SLUG }}:${{ env.GITHUB_SHA_SHORT }}
```

### PR Environments

```yaml
preview_url: https://pr-${{ env.GITHUB_HEAD_REF_SLUG }}.dev.com
```

## Variable Availability

- Available after action execution
- Persists within the same job
- Must be re-run in new jobs
- Accessible in:
  - Workflow files
  - Shell commands
  - Scripts
  - Other actions

## Related Documentation

- [Basic Usage](../guides/basic-usage.md)
- [Advanced Patterns](../guides/advanced-patterns.md)
- [Troubleshooting](../reference/troubleshooting.md)

Need help? [Open an issue](https://github.com/rlespinasse/github-slug-action/issues)
