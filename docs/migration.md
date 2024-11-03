# Migration Guide

This guide helps you migrate between different versions of GitHub Slug Action.

## Migrating to v5.x

### Key Changes

1. **GITHUB_REF_NAME Behavior Change**
   - Now follows GitHub Actions default behavior
   - Returns `<PR-number>/merge` during pull request workflows
   - Previous branch name behavior available via `GITHUB_HEAD_REF`

### Required Actions

#### Update Pull Request Workflows

```yaml
# Before (v4.x)
${{ env.GITHUB_REF_NAME }}  # Returns branch name

# After (v5.x)
${{ env.GITHUB_HEAD_REF }}  # Returns branch name
${{ env.GITHUB_REF_NAME }}  # Returns <PR-number>/merge
```

#### Review Dependent Workflows

1. Identify workflows using `GITHUB_REF_NAME`
2. Update variable references based on intended behavior:

   ```yaml
   # For branch name in pull requests
   - name: Use branch name
     run: echo ${{ env.GITHUB_HEAD_REF }}

   # For PR reference
   - name: Use PR reference
     run: echo ${{ env.GITHUB_REF_NAME }}
   ```

### Other Improvements

- Enhanced prefix support
- Improved slug generation consistency
- Better error handling

## Migrating from v3.x

### Breaking Changes

1. **Short SHA Length**
   - Default: Git-determined length
   - For v3.x compatibility:

     ```yaml
     with:
       short-length: 8
     ```

2. **Variable Naming**
   - More consistent naming patterns
   - Better alignment with GitHub Actions standards

### Recommended Updates

1. Review and update workflow files
2. Test in a non-production environment
3. Update action version reference:

   ```yaml
   uses: rlespinasse/github-slug-action@v5
   ```

## Need Help?

- [Open an issue](https://github.com/rlespinasse/github-slug-action/issues)
- Review [documentation](https://github.com/rlespinasse/github-slug-action)
- Check [known conflicts](docs/conflicts.md)
