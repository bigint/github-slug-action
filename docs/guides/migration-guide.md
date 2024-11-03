# Migration Guide

## Overview

This guide helps you migrate between different versions of the GitHub Slug Action.

## v4 to v5 Migration

### Key Changes

- Removed deprecated variables
- Updated transformation rules
- Enhanced URL-safe handling
- Added new environment variables
- Improved performance

### Required Updates

1. Replace deprecated variables:

    ```diff
    - ${{ env.GITHUB_REF_SLUG_URL }}
    + ${{ env.GITHUB_REF_SLUG }}
    ```

2. Update workflow syntax:

    ```yaml
    steps:
      - uses: rlespinasse/github-slug-action@v5  # Update version
    ```

## v3 to v4 Migration

### Key Changes

- Standardized variable naming
- Simplified transformation rules
- Removed legacy support
- Added validation checks

### Required Updates

1. Update variable references:

    ```diff
    - ${{ env.URL_SAFE_BRANCH }}
    + ${{ env.GITHUB_REF_SLUG }}
    ```

2. Review transformation outputs:

    - Lowercase conversion is now default
    - Special characters handling updated
    - Hyphen usage standardized

## Best Practices

- Test migrations in staging environment
- Update documentation references
- Review dependent workflows
- Validate transformed values
- Monitor for edge cases

## Troubleshooting

- Check logs for deprecation warnings
- Verify variable availability
- Test transformations
- Review GitHub Actions documentation

## Related Documentation

- [Slug Variables](slug-variables.md)
- [URL-Safe Variables](url-safe-variables.md)
- [Short SHA Variables](short-sha-variables.md)

Need help? [Open an issue](https://github.com/rlespinasse/github-slug-action/issues/new)
