# Windows Usage Guide

## Overview

Guidelines for using GitHub Slug Action in Windows environments with specific considerations and best practices.

## Windows-Specific Setup

### Environment Configuration

```yaml
name: Windows Build
runs-on: windows-latest
steps:
  - uses: rlespinasse/github-slug-action@v5
    env:
      ACTIONS_ALLOW_UNSECURE_COMMANDS: true  # If required for legacy systems
```

### Path Handling

```yaml
steps:
  - uses: rlespinasse/github-slug-action@v5
  - run: |
      echo "Path: ${{ env.GITHUB_REF_SLUG }}"
      echo "Full Path: %GITHUB_WORKSPACE%\${{ env.GITHUB_REF_SLUG }}"
    shell: cmd
```

## Common Windows Scenarios

### PowerShell Usage

```yaml
steps:
  - uses: rlespinasse/github-slug-action@v5
  - run: |
      Write-Host "Branch: $env:GITHUB_REF_SLUG"
      Write-Host "Path: $env:GITHUB_WORKSPACE\$env:GITHUB_REF_SLUG"
    shell: pwsh
```

### Batch Script Integration

```yaml
steps:
  - uses: rlespinasse/github-slug-action@v5
  - run: |
      echo Branch: %GITHUB_REF_SLUG%
      echo Path: %GITHUB_WORKSPACE%\%GITHUB_REF_SLUG%
    shell: cmd
```

## Best Practices

- Use appropriate shell syntax
- Handle path separators correctly
- Consider case sensitivity
- Test variable expansion
- Validate file paths

## Known Limitations

- Path length restrictions
- Character encoding differences
- Shell-specific escaping
- Environment variable persistence
- Command prompt limitations

## Related Documentation

- [URL Usage](url-usage.md)
- [Version Variables](version-variables.md)
- [Migration Guide](migration-guide.md)

Need help? [Open an issue](https://github.com/rlespinasse/github-slug-action/issues/new)
