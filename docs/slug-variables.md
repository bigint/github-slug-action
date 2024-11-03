# Slug Variables Reference

This document details the slug-formatted variables provided by GitHub Slug Action, which convert GitHub variables into URL and path-safe formats.

## Available Slug Variables

### Repository Variables

#### GITHUB_REPOSITORY_SLUG

Slugified version of `GITHUB_REPOSITORY` (owner/repository)

```yaml
# Examples
GITHUB_REPOSITORY: "octocat/Hello-World" → GITHUB_REPOSITORY_SLUG: "octocat-hello-world"
GITHUB_REPOSITORY: "rlespinasse/Hello-World.go" → GITHUB_REPOSITORY_SLUG: "rlespinasse-hello-world.go"
```

#### Repository Parts

- **GITHUB_REPOSITORY_OWNER_PART_SLUG**: Owner name in slug format
- **GITHUB_REPOSITORY_NAME_PART_SLUG**: Repository name in slug format

```yaml
# Example
GITHUB_REPOSITORY: "AnotherPerson/SomeRepository"
GITHUB_REPOSITORY_OWNER_PART_SLUG: "anotherperson"
GITHUB_REPOSITORY_NAME_PART_SLUG: "somerepository"
```

### Reference Variables

#### GITHUB_REF_SLUG

Slugified branch or tag reference that triggered the workflow

```yaml
# Examples
GITHUB_REF: "refs/heads/feat/new_feature" → GITHUB_REF_SLUG: "feat-new-feature"
GITHUB_REF: "refs/tags/product@1.0.0-rc.2" → GITHUB_REF_SLUG: "product-1.0.0-rc.2"
```

#### Pull Request References

Available during pull request events:

- **GITHUB_HEAD_REF_SLUG**: Source branch in slug format
- **GITHUB_BASE_REF_SLUG**: Target branch in slug format

```yaml
# Example
GITHUB_HEAD_REF: "feat/new_feature" → GITHUB_HEAD_REF_SLUG: "feat-new-feature"
GITHUB_BASE_REF: "main" → GITHUB_BASE_REF_SLUG: "main"
```

#### GITHUB_EVENT_REF_SLUG

Available during `create` and `delete` events, provides the slugified reference name

```yaml
# Example
github.event.ref: "refs/heads/New_Awesome_Product" → GITHUB_EVENT_REF_SLUG: "new-awesome-product"
```

## Slugification Rules

- Converts to lowercase
- Replaces spaces and special characters with hyphens
- Preserves dots and version numbers
- Removes leading/trailing special characters

For URL-safe versions of these variables, append `_URL` to access percent-encoded formats.

## Related Documentation

- [GitHub Events Documentation](https://docs.github.com/en/developers/webhooks-and-events/webhook-events-and-payloads)
- [Partial Variables Reference](partial-variables.md)
