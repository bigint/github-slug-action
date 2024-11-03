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

# Solution: Re-run action in each job
jobs:
  job2:
    steps:
      - uses: rlespinasse/github-slug-action@v5
      - run: echo ${{ env.GITHUB_REF_SLUG }}
```

## Debug Steps

### Enable Debug Logging

```yaml
steps:
  - uses: rlespinasse/github-slug-action@v5
    with:
      debug: true
```

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

- Case sensitivity on different OS
- Special character handling
- Unicode support limitations
- Environment variable persistence
- Action version compatibility

## Solutions

### Version Specific

```yaml
# Use specific version for stability
steps:
  - uses: rlespinasse/github-slug-action@v5.2.0
```

### OS Compatibility

```yaml
steps:
  - uses: rlespinasse/github-slug-action@v5
    with:
      platform: ${{ runner.os }}
```

## Support Resources

- [GitHub Issues](https://github.com/rlespinasse/github-slug-action/issues)
- [Documentation](https://github.com/rlespinasse/github-slug-action/blob/main/README.md)
- [Release Notes](https://github.com/rlespinasse/github-slug-action/releases)

Need more help? [Open an issue](https://github.com/rlespinasse/github-slug-action/issues/new)
