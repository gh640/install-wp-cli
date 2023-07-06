# `gh640/install-wp-cli`

A simple reusable GitHub Actions action to install [WP-CLI](https://wp-cli.org/), the command-line interface for [WordPress](https://wordpress.org/).

## Usage

```yaml
jobs:
  update:
    runs-on: ubuntu-latest
    steps:
      # (Prior steps)
      - uses: gh640/install-wp-cli@main
      # (Posterior steps)
```
