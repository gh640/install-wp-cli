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

In Posterior steps, `wp` command can be used.

## Prerequisites

- `runs-on: ubuntu-latest`
- PHP needs to be installed beforehand.

Excerpt from my working sample:

```yaml
jobs:
  update:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout
        uses: actions/checkout@v3
      - name: Setup PHP
        uses: shivammathur/setup-php@v2
        with:
          php-version: 8.2
      - uses: gh640/install-wp-cli@main
      - name: Create wp-config.php
        run: >
          wp config create
          --allow-root
          --dbname=$MYSQL_DATABASE
          --dbuser=$MYSQL_USER
          --dbpass=$MYSQL_PASSWORD
          --locale=ja
          --force
        working-directory: public_html
```
