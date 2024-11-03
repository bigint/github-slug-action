# GitHub Variables Reference

This document outlines the GitHub variables available in your workflows, including those provided by GitHub Slug Action.

## Default Environment Variables

For a complete list of default variables, see the [GitHub Actions Environment Variables documentation][1].

### Action-Enhanced Variables

The following default GitHub variables can be enhanced with additional formats:

| Base Variable     | Available Enhancements |
| ----------------- | ---------------------- |
| GITHUB_REPOSITORY | `_SLUG`, `_SLUG_URL`   |
| GITHUB_REF        | `_SLUG`, `_SLUG_URL`   |
| GITHUB_HEAD_REF   | `_SLUG`, `_SLUG_URL`   |
| GITHUB_BASE_REF   | `_SLUG`, `_SLUG_URL`   |
| GITHUB_SHA        | `_SHORT`               |

Example:

```yaml
# Original: refs/heads/feature/new.branch
${{ env.GITHUB_REF_SLUG }}     # feature-new.branch
${{ env.GITHUB_REF_SLUG_URL }} # feature-new-branch
```

## Event-Specific Variables

Additional variables are available based on the triggering event. See [Events that trigger workflows][2] for details.

### Available Event Variables

#### Create and Delete Events

Reference: [Create][3] and [Delete][4] webhook payloads

| Event Variable   | Enhanced Format                                      |
| ---------------- | ---------------------------------------------------- |
| github.event.ref | `GITHUB_EVENT_REF_SLUG`, `GITHUB_EVENT_REF_SLUG_URL` |

#### Pull Request Events

Applies to: `pull_request`, `pull_request_review`, `pull_request_review_comment`, and `pull_request_target`

Reference: [Pull Request webhook payload][5]

| Event Variable                     | Enhanced Format                            |
| ---------------------------------- | ------------------------------------------ |
| github.event.pull_request.head.sha | `GITHUB_EVENT_PULL_REQUEST_HEAD_SHA_SHORT` |

Example:

```yaml
# Original SHA: 8f166fd75f36c896c63a9a0c0ccd2b42f5b0c040
${{ env.GITHUB_EVENT_PULL_REQUEST_HEAD_SHA_SHORT }} # 8f166fd7
```

[1]: https://docs.github.com/en/actions/reference/environment-variables#default-environment-variables
[2]: https://docs.github.com/en/actions/reference/events-that-trigger-workflows
[3]: https://docs.github.com/en/developers/webhooks-and-events/webhook-events-and-payloads#create
[4]: https://docs.github.com/en/developers/webhooks-and-events/webhook-events-and-payloads#delete
[5]: https://docs.github.com/en/developers/webhooks-and-events/webhook-events-and-payloads#pull_request
