# Repository Part Variables Reference

This document details the variables that provide individual components of the repository name from the GitHub Slug Action.

## Available Part Variables

### GITHUB_REPOSITORY_OWNER_PART

Extracts the owner (user or organization) name from `GITHUB_REPOSITORY`

```yaml
# Examples
GITHUB_REPOSITORY: "octocat/Hello-World"
→ GITHUB_REPOSITORY_OWNER_PART: "octocat"

GITHUB_REPOSITORY: "rlespinasse/Hello-World.go"
→ GITHUB_REPOSITORY_OWNER_PART: "rlespinasse"
```

### GITHUB_REPOSITORY_NAME_PART

Extracts the repository name from `GITHUB_REPOSITORY`

```yaml
# Examples
GITHUB_REPOSITORY: "octocat/Hello-World"
→ GITHUB_REPOSITORY_NAME_PART: "Hello-World"

GITHUB_REPOSITORY: "rlespinasse/Hello-World.go"
→ GITHUB_REPOSITORY_NAME_PART: "Hello-World.go"
```

## Usage Details

- Variables preserve the original case and special characters
- Useful for:
  - Accessing repository components separately
  - Creating custom naming patterns
  - Repository-specific configurations

## Related Variables

- For URL-safe versions, see [Slug URL Variables](slug-url-variables.md)
- For slug versions, see [Slug Variables](slug-variables.md)

## Related Documentation

- [GitHub Environment Variables](https://docs.github.com/en/actions/reference/environment-variables)
