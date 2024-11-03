# GitHub Slug Action

Generate slug and url-safe variables for your GitHub Actions workflows based on GitHub environment variables.

## 🚀 Quick Start

```yaml
steps:
  - uses: rlespinasse/github-slug-action@v5
  - name: Print slug variables
    run: |
      echo "Repository: ${{ env.GITHUB_REPOSITORY_SLUG }}"
      echo "Branch Name: ${{ env.GITHUB_REF_NAME }}"
      echo "Branch Ref: ${{ env.GITHUB_REF_SLUG }}"
      echo "SHA: ${{ env.GITHUB_SHA_SHORT }}"
```

## 📖 Table of Contents

- [GitHub Slug Action](#github-slug-action)
  - [🚀 Quick Start](#-quick-start)
  - [📖 Table of Contents](#-table-of-contents)
  - [✨ Features](#-features)
  - [🔧 Usage](#-usage)
  - [📋 Available Variables](#-available-variables)
  - [💡 Examples](#-examples)
    - [Branch Deployment](#branch-deployment)
  - [📚 Documentation](#-documentation)
  - [🤝 Contributing](#-contributing)
  - [📄 License](#-license)

## ✨ Features

- Generates clean, URL-safe slugs from GitHub variables
- Supports Windows and Linux runners
- Provides multiple variable formats:
  - Standard slugs
  - URL-safe slugs
  - Short SHA versions
- Zero configuration required
- Lightweight and fast execution

## 🔧 Usage

1. Add the action to your workflow
2. Access generated variables in subsequent steps
3. Use in conditions, environment names, or deployment URLs

See our [Getting Started Guide](docs/getting-started/quick-start.md) for detailed instructions.

## 📋 Available Variables

| Category   | Original            | Generated Slug           | URL-Safe                     |
| ---------- | ------------------- | ------------------------ | ---------------------------- |
| Repository | `GITHUB_REPOSITORY` | `GITHUB_REPOSITORY_SLUG` | `GITHUB_REPOSITORY_SLUG_URL` |
| Branch/Tag | `GITHUB_REF`        | `GITHUB_REF_SLUG`        | `GITHUB_REF_SLUG_URL`        |
| SHA        | `GITHUB_SHA`        | `GITHUB_SHA_SHORT`       | -                            |

[View all available variables →](docs/variables/overview.md)

## 💡 Examples

### Branch Deployment

```yaml
name: Deploy
on: push
jobs:
  deploy:
    runs-on: ubuntu-latest
    steps:
      - uses: rlespinasse/github-slug-action@v5
      - run: echo "Deploying to ${{ env.GITHUB_REF_SLUG }}"
```

[More examples →](docs/guides/)

## 📚 Documentation

- [Getting Started](docs/getting-started/)
- [Variable Reference](docs/variables/)
- [Usage Guides](docs/guides/)
- [Troubleshooting](docs/reference/troubleshooting.md)

## 🤝 Contributing

Contributions are welcome! Please read our [Contributing Guide](CONTRIBUTING.md) for details.

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

---

⭐ If this action helps you, please consider giving it a star!

[Report Bug](https://github.com/rlespinasse/github-slug-action/issues/new) · [Request Feature](https://github.com/rlespinasse/github-slug-action/issues/new)
