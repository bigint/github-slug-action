# Conflict Resolution Guide

## Overview

Guidelines for resolving conflicts when using GitHub Slug Action in your workflows, particularly when dealing with multiple actions or variable naming conflicts.

## Common Conflicts

### Environment Variable Conflicts

```yaml
# Potential conflict with existing variables
steps:
  - name: Previous step setting variables
    run: |
      echo "GITHUB_REF_SLUG=custom-value" >> $GITHUB_ENV
    shell: bash

  - uses: rlespinasse/github-slug-action@v5  # Will override previous values
```

### Action Order Conflicts

```yaml
# Order matters for variable availability
steps:
  - name: Step requiring slug variables
    run: echo ${{ env.GITHUB_REF_SLUG }}  # Will be empty if placed before the action
    shell: bash

  - uses: rlespinasse/github-slug-action@v5
```

## Resolution Strategies

### Custom Variable Names using prefix

```yaml
steps:
  - name: Previous step setting variables
    run: |
      echo "GITHUB_REF_SLUG=custom-value" >> $GITHUB_ENV
    shell: bash

  - uses: rlespinasse/github-slug-action@v5
    with:
      prefix: CUSTOM_

  - name: Step requiring slug variables
    run: echo ${{ env.CUSTOM_GITHUB_REF_SLUG }}  # Will be empty if placed before the action
    shell: bash
```

### Variable Preservation

```yaml
steps:
  - name: Save original value
    run: echo "ORIGINAL_REF=${{ env.GITHUB_REF_SLUG }}" >> $GITHUB_ENV
    shell: bash

  - uses: rlespinasse/github-slug-action@v5
```

### Manual Custom Variable Names

```yaml
steps:
  - uses: rlespinasse/github-slug-action@v5
  - name: Use custom variables
    run: |
      echo "CUSTOM_SLUG=${GITHUB_REF_SLUG}" >> $GITHUB_ENV
    shell: bash
```

## Best Practices

- Document variable usage
- Check for existing variables
- Use descriptive custom names
- Maintain consistent naming
- Follow workflow order dependencies

## Troubleshooting

- Verify action version compatibility
- Check environment variable scope
- Review workflow execution order
- Validate variable naming conventions
- Monitor for override warnings

## Related Documentation

- [GitHub Variables](reference/github-variables.md)
- [Migration Guide](reference/migration-guide.md)
- [Troubleshooting](reference/troubleshooting.md)

Need help? [Open an issue](https://github.com/rlespinasse/github-slug-action/issues/new)
