# Basic Usage Guide

## Overview

GitHub Slug Action converts GitHub environment variables into URL-safe slugs. Here's how to use them effectively.

## Core Variables

```yaml
steps:
  - uses: rlespinasse/github-slug-action@v5
  - name: Example Usage
    run: |
      # Branch or tag slug
      echo ${{ env.GITHUB_REF_SLUG }}

      # Repository slug
      echo ${{ env.GITHUB_REPOSITORY_SLUG }}

      # Short SHA
      echo ${{ env.GITHUB_SHA_SHORT }}
```

## Common Patterns

### Environment Names

```yaml
environment: ${{ env.GITHUB_REF_SLUG }}
```

### Dynamic URLs

```yaml
url: https://${{ env.GITHUB_REF_SLUG }}.example.com
```

### Docker Tags

```yaml
tags: ${{ env.GITHUB_REPOSITORY_SLUG }}:${{ env.GITHUB_SHA_SHORT }}
```

## Platform-Specific Usage

### Linux/macOS

```bash
echo $GITHUB_REF_SLUG
```

### Windows CMD

```cmd
echo %GITHUB_REF_SLUG%
```

### PowerShell

```powershell
Write-Host $env:GITHUB_REF_SLUG
```

## Variable Availability

- Variables are available after the action runs
- Accessible within the same job
- Must re-run action in different jobs
- Available in both scripts and workflow files

## Examples

### Pull Request Environments

```yaml
name: Deploy Preview
on: pull_request

jobs:
  deploy:
    runs-on: ubuntu-latest
    steps:
      - uses: rlespinasse/github-slug-action@v5
      - name: Deploy
        run: |
          deploy --env="pr-${{ env.GITHUB_HEAD_REF_SLUG }}"
```

### Branch Deployments

```yaml
name: Deploy Branch
on: push

jobs:
  deploy:
    runs-on: ubuntu-latest
    steps:
      - uses: rlespinasse/github-slug-action@v5
      - name: Deploy
        run: |
          deploy --env="${{ env.GITHUB_REF_SLUG }}"
```

## Best Practices

- Run the action early in your workflow
- Use consistent variable references
- Consider error handling for critical steps
- Cache slugs for reuse when possible

## Related Resources

- [Available Variables](../variables/overview.md)
- [Advanced Usage](../guides/advanced-usage.md)
- [Troubleshooting](../reference/troubleshooting.md)

Need help? [Open an issue](https://github.com/rlespinasse/github-slug-action/issues)
