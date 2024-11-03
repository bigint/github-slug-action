# Short SHA Variables Reference

This document details the shortened SHA hash variables provided by GitHub Slug Action, which provide convenient abbreviated versions of commit hashes.

## Available Short Variables

### GITHUB_SHA_SHORT

Shortened version of the commit SHA that triggered the workflow

```yaml
# Example
GITHUB_SHA: "ffac537e6cbbf934b08745a378932722df287a53"
→ GITHUB_SHA_SHORT: "ffac537e"
```

### GITHUB_EVENT_PULL_REQUEST_HEAD_SHA_SHORT

Shortened version of the latest commit SHA from pull request events

```yaml
# Example
github.event.pull_request.head.sha: "ffac537e6cbbf934b08745a378932722df287a53"
→ GITHUB_EVENT_PULL_REQUEST_HEAD_SHA_SHORT: "ffac537e"
```

## Usage Details

- Short variables contain the first 8 characters of the full SHA
- Useful for:
  - Display purposes
  - Brief references in logs or messages
  - Creating concise artifact names
  - Generating unique identifiers

## Availability

- `GITHUB_SHA_SHORT`: Available in all workflow runs
- `GITHUB_EVENT_PULL_REQUEST_HEAD_SHA_SHORT`: Only available during pull request events

## Related Documentation

- [GitHub SHA Documentation](https://docs.github.com/en/actions/reference/environment-variables#default-environment-variables)
- [Pull Request Events](https://docs.github.com/en/developers/webhooks-and-events/webhook-events-and-payloads#pull_request)
