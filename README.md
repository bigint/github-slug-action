# GitHub Slug Action

A powerful GitHub Action that exposes slug/short versions of GitHub environment variables for enhanced workflow management.

## Features

- Converts environment variables to slug format (lowercase, URL-friendly)
- Provides URL-safe versions of variables
- Generates shortened versions of commit SHAs
- Maintains case-sensitive options
- Supports custom prefixes and length configurations

## Quick Start

```yaml
- name: Enhanced GitHub environment variables
  uses: rlespinasse/github-slug-action@v5
```

## Configuration Options

### Basic Usage

```yaml
- name: Enhanced GitHub environment variables
  uses: rlespinasse/github-slug-action@v5
```

### With Custom Prefix

```yaml
- name: Enhanced GitHub environment variables
  uses: rlespinasse/github-slug-action@v5
  with:
    prefix: CI_
```

### With Custom Slug Length

```yaml
- name: Enhanced GitHub environment variables
  uses: rlespinasse/github-slug-action@v5
  with:
    slug-maxlength: 80  # Use 'nolimit' for unlimited length (Default: 63)
```

### With Custom Short Length

```yaml
- name: Enhanced GitHub environment variables
  uses: rlespinasse/github-slug-action@v5
  with:
    short-length: 7  # Default: Git-determined, use 8 for v3.x compatibility
```

## Available Variables

### Enhanced Variables

- `GITHUB_REF_NAME`: Reference name (branch/tag)

### Partial Variables

- `GITHUB_REPOSITORY_OWNER_PART`
- `GITHUB_REPOSITORY_NAME_PART`

### Slug Variables

- `GITHUB_REPOSITORY_SLUG`
- `GITHUB_REF_SLUG`
- `GITHUB_HEAD_REF_SLUG`
- And more...

### Short Variables

- `GITHUB_SHA_SHORT`
- `GITHUB_EVENT_PULL_REQUEST_HEAD_SHA_SHORT`

## Troubleshooting

### Common Issues

1. **Short Variable Length Changes**
   - Use `short-length` input to maintain consistent lengths
   - Minimum length: 4 characters

2. **Environment Variable Conflicts**
   - Use prefix to avoid conflicts with GitHub defaults
   - Check [known conflicts documentation](docs/conflicts.md)

### Best Practices

- Use [Dependabot](https://docs.github.com/en/code-security/dependabot) to keep the action updated
- Always specify version tags (e.g., `@v5`) instead of branch names
- Test variables in your specific workflow context

## Documentation

Detailed documentation available for:

- [Slug Variables](docs/slug-variables.md)
- [URL Variables](docs/slug-url-variables.md)
- [Short Variables](docs/short-variables.md)
- [GitHub Variables](docs/github-variables.md)

## Contributing

Issues and pull requests are welcome! Please check our [contribution guidelines](CONTRIBUTING.md).

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

---

For detailed examples and advanced usage, visit our [GitHub repository](https://github.com/rlespinasse/github-slug-action).
