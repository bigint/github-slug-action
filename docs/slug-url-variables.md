# URL-Safe Slug Variables Reference

This document details the URL-safe versions of slug variables provided by GitHub Slug Action. These variables are specially formatted for use in URLs and paths, with proper percent-encoding of special characters.

## Repository URL Variables

### GITHUB_REPOSITORY_SLUG_URL

URL-safe version of repository name, combining owner and repository

```yaml
# Examples
GITHUB_REPOSITORY: "octocat/Hello-World"
→ GITHUB_REPOSITORY_SLUG_URL: "octocat-hello-world"

GITHUB_REPOSITORY: "rlespinasse/Hello-World.go"
→ GITHUB_REPOSITORY_SLUG_URL: "rlespinasse-hello-world-go"
```

### Repository Part Variables

#### Owner and Name Components

- **GITHUB_REPOSITORY_OWNER_PART_SLUG_URL**: URL-safe owner name
- **GITHUB_REPOSITORY_NAME_PART_SLUG_URL**: URL-safe repository name

```yaml
# Example
GITHUB_REPOSITORY: "AnotherPerson/Some.Repository"
GITHUB_REPOSITORY_OWNER_PART_SLUG_URL: "anotherperson"
GITHUB_REPOSITORY_NAME_PART_SLUG_URL: "some-repository"
```

## Reference URL Variables

### GITHUB_REF_SLUG_URL

URL-safe version of the triggering reference

```yaml
# Examples
GITHUB_REF: "refs/heads/feat/new_feature"
→ GITHUB_REF_SLUG_URL: "feat-new-feature"

GITHUB_REF: "refs/tags/v1.0.0"
→ GITHUB_REF_SLUG_URL: "v1-0-0"

GITHUB_REF: "refs/pull/42-merge"
→ GITHUB_REF_SLUG_URL: "42-merge"
```

> **Note**: Version 3.3.0 fixed incorrect handling of pull request references (previously `refs-pull-42-merge` instead of `42-merge` in v3.0.0-v3.2.0)

### Pull Request Reference Variables

Available during pull request events:

- **GITHUB_HEAD_REF_SLUG_URL**: URL-safe source branch name
- **GITHUB_BASE_REF_SLUG_URL**: URL-safe target branch name

```yaml
# Example
GITHUB_HEAD_REF: "feat/new_feature"
→ GITHUB_HEAD_REF_SLUG_URL: "feat-new-feature"
```

### GITHUB_EVENT_REF_SLUG_URL

Available during `create` and `delete` events, provides URL-safe reference name

```yaml
# Example
github.event.ref: "refs/heads/New_Awesome_Product"
→ GITHUB_EVENT_REF_SLUG_URL: "new-awesome-product"
```

## URL-Safe Formatting Rules

- Converts to lowercase
- Replaces special characters with hyphens
- Encodes remaining special characters using percent-encoding
- Removes leading/trailing special characters
- Converts periods to hyphens (unlike regular slug variables)

## Related Documentation

- [GitHub Events Documentation](https://docs.github.com/en/developers/webhooks-and-events/webhook-events-and-payloads)
- [Partial Variables Reference](partial-variables.md)
