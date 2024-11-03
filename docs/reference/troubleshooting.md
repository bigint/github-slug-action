# Troubleshooting Guide

## Common Issues

### Missing Variables

```yaml
# Problem: Variables not available
steps:
  - run: echo ${{ env.GITHUB_REF_SLUG }}  # Empty output
  - uses: rlespinasse/github-slug-action@v5

# Solution: Correct order
steps:
  - uses: rlespinasse/github-slug-action@v5
  - run: echo ${{ env.GITHUB_REF_SLUG }}
    shell: bash
```

### Variable Scope Issues

```yaml
# Problem: Variables not persisting between jobs
jobs:
  job1:
    steps:
      - uses: rlespinasse/github-slug-action@v5
  job2:
    steps:
      - run: echo ${{ env.GITHUB_REF_SLUG }}  # Empty
        shell: bash

# Solution: Re-run action in each job
jobs:
  job2:
    steps:
      - uses: rlespinasse/github-slug-action@v5
      - run: echo ${{ env.GITHUB_REF_SLUG }}
        shell: bash
```

## Debug Steps

### Enable Debug Logging

Add the variable (or secret) `ACTIONS_STEP_DEBUG` set to true to activate the debug of your workflow.

### Variable Inspection

```yaml
steps:
  - uses: rlespinasse/github-slug-action@v5
  - name: Debug variables
    run: |
      echo "REF_SLUG: ${{ env.GITHUB_REF_SLUG }}"
      echo "SHA_SHORT: ${{ env.GITHUB_SHA_SHORT }}"
      env | grep GITHUB_
    shell: bash
```

## Known Issues

- Special character handling
- Unicode support limitations
- Environment variable persistence
- Action version compatibility

## Solutions

### Version Specific

```yaml
# Use specific version for stability
steps:
  - uses: rlespinasse/github-slug-action@v5.0.0
```

## Support Resources

- [GitHub Issues](https://github.com/rlespinasse/github-slug-action/issues)
- [Documentation](https://github.com/rlespinasse/github-slug-action/blob/v5.x/README.md)
- [Release Notes](https://github.com/rlespinasse/github-slug-action/releases)

Need more help? [Open an issue](https://github.com/rlespinasse/github-slug-action/issues/new)
