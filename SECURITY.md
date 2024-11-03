# Security Policy

## Supported Versions and Branches

| Version | Supported          | End of Support | Branch | Specific Tags |
| ------- | ------------------ | -------------- | ------ | ------------- |
| 5.x     | :white_check_mark: |                | v5.x   | v5            |
| 4.x     | :white_check_mark: | 2025-01-31     | v4.x   | v4            |
| 3.x     | :x:                | 2024-01-31     |        | v3.x, v3      |
| 2.x     | :x:                | 2021-04-05     |        | v2.x, 2.2.0   |
| 1.x     | :x:                | 2021-04-05     |        | v1.1.x, 1.2.0 |
| 1.0.x   | :x:                | 2019-11-07     |        | 1.0.2         |

GitHub workflows can use any available branch as an action.

## Branch End-of-Life Policy

Since `2023-10-20`, when a new major version is released:

- The previous version continues to receive security patches for 3 months
- After these 3 months, the branch is deleted and only tags are retained

## Vulnerability Reporting

To report a vulnerability, please create a [draft security advisory](https://github.com/rlespinasse/github-slug-action/security/advisories).

If the vulnerability is confirmed:

- A fix will be developed
- The security advisory will be published
