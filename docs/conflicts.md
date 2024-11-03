# Known Environment Variable Conflicts

This document details known conflicts between GitHub Slug Action variables and GitHub Actions default environment variables.

## GITHUB_REF_NAME

> [!CAUTION]
> This conflict happen with the version 3 and 4 for GitHub Slug Action.
> For a smooth transition, check our [migration guide to v5](docs/migration.md).

### Issue Description

A conflict exists in the behavior of `GITHUB_REF_NAME` during `pull_request*` workflows.

### Behavior Differences

- **GitHub Slug Action**: Returns the branch name
- **GitHub Actions Default**: Returns `<PR-number>/merge`

### Usage Impact

```yaml
# Different behaviors:
${{ env.GITHUB_REF_NAME }}  # GitHub Slug Action behavior
$GITHUB_REF_NAME            # GitHub Actions default behavior
```

### Recommended Solution

Use the `prefix` input to avoid conflicts:

```yaml
- name: Enhanced GitHub environment variables
  uses: rlespinasse/github-slug-action@v5
  with:
    prefix: CI_

# Then use:
${{ env.CI_GITHUB_REF_NAME }}  # GitHub Slug Action behavior
$CI_GITHUB_REF_NAME            # GitHub Slug Action behavior
$GITHUB_REF_NAME               # GitHub Actions default behavior
```

## General Conflict Prevention

### Best Practices

1. Always use the `prefix` input when working with sensitive variables
2. Test variable behavior in your specific workflow context
3. Document any custom prefixes in your workflow files
4. Consider using explicit variable references (`${{ env.VAR_NAME }}`) for clarity

### Default Variables Protection

GitHub Actions prevents overriding default environment variables. If you attempt to set a variable that matches a default name:

- The assignment will be ignored
- The default behavior will be preserved
- No error message will be displayed

For a complete list of protected variables, see [GitHub's Default Environment Variables](https://docs.github.com/en/actions/learn-github-actions/environment-variables#default-environment-variables).

## Reporting New Conflicts

If you discover a new conflict:

1. Create an issue in the [GitHub repository](https://github.com/rlespinasse/github-slug-action/issues)
2. Include:
   - The conflicting variable name
   - Expected vs. actual behavior
   - Your workflow context
   - Steps to reproduce

This helps maintain documentation and find appropriate solutions for the community.
