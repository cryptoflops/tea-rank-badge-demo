# Tea Rank Badge Demo

This repository demonstrates the [tea-rank-badge](https://github.com/cryptoflops/tea-rank-badge) GitHub Action that automatically updates a teaRank badge for Tea Protocol projects.

## About This Demo

This demo tracks the teaRank of the `curl` project from the Tea Protocol. The badge below updates automatically every day at 2:20 AM UTC.

## Current teaRank

<!-- tea-rank-badge-start -->

![teaRank](./.github/tea-rank-badge.svg)

<!-- tea-rank-badge-end -->

## How It Works

1. **GitHub Action**: A scheduled workflow runs daily
2. **Fetches teaRank**: The action queries the Tea Protocol API for the current rank
3. **Updates Badge**: If the rank has changed, it generates a new SVG badge
4. **Commits Changes**: Automatically commits and pushes the updates

## Setup Your Own

To add a teaRank badge to your project:

### Quick Start (CLI)

```bash
# One-time setup
npx tea-rank-badge@latest --name your-project-name
```

### GitHub Action

1. Add this workflow to `.github/workflows/tea-rank-badge.yml`:

```yaml
name: Update Tea Rank Badge

on:
  schedule:
    - cron: '20 2 * * *'  # Daily at 2:20 AM UTC
  workflow_dispatch:      # Manual trigger

permissions:
  contents: write

jobs:
  update-badge:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - uses: cryptoflops/tea-rank-badge@v1
        with:
          project_name: 'your-project-name'
```

2. The action will automatically:
   - Create a badge at `.github/tea-rank-badge.svg`
   - Update your README with the badge
   - Commit changes when the rank updates

## Features

- 🏆 **Dynamic Colors**: Badge color changes based on rank thresholds
- 🔄 **Automatic Updates**: Daily checks for rank changes
- 📊 **Multiple Styles**: Supports flat, flat-square, plastic, and for-the-badge styles
- 🎯 **Precise Control**: Configure decimal precision, custom labels, and more

## Links

- [tea-rank-badge on npm](https://www.npmjs.com/package/tea-rank-badge)
- [tea-rank-badge on GitHub](https://github.com/cryptoflops/tea-rank-badge)
- [Tea Protocol](https://tea.xyz/)

## License

This demo is MIT licensed. The tea-rank-badge tool is also MIT licensed.