# Pobo Page Builder — Claude Code plugin

[Pobo Page Builder](https://www.pobo.space) tools for Claude — nothing runs on
your machine, all logic lives on the backend:

- **AI styling of widgets** — Claude reads your e-shop's look (colors, fonts,
  buttons, border radius), generates matching styles, and deploys them through
  Pobo Page Builder.
- **Product labeling** — Claude takes a product list in any shape (EANs, product
  codes, URLs, or names — e.g. an xlsx from a client), resolves it to Pobo
  products, and labels them so you can filter the batch in the Pobo admin grid.

Supported platforms: Shoptet, Shopify, WooCommerce, PrestaShop, Upgates.

## Installation

In [Claude Code](https://claude.com/claude-code), run:

```
/plugin marketplace add pobo-builder/claude-plugin
/plugin install pobo@pobo-builder
```

## Connecting your Pobo Page Builder account

Run this once in your terminal:

```
claude mcp add -s user --transport http pobo https://api.pobo.space/mcp/client
```

Claude Code opens your browser — log in with your Pobo Page Builder account and
approve access. That's it: no tokens, no environment variables, no config files.
The connection persists across all your projects; if it ever expires, run `/mcp`
in Claude Code and re-authenticate.

### Claude.ai / ChatGPT (web)

The same server works without Claude Code. Add a custom connector with the URL
`https://api.pobo.space/mcp/client`:

- **Claude.ai**: Settings → Connectors → Add custom connector
- **ChatGPT**: Settings → Connectors → Create

Leave the OAuth Client ID/Secret fields empty — you will be asked to log in and
approve access in your browser.

## Usage

Just tell Claude, for example:

> Make my Pobo Page Builder widgets match my e-shop's design.

Claude picks the e-shop, reads its design, generates the styles, and deploys them.
You can then review the changes on your e-shop (hard refresh) and iterate with
feedback. Deployed AI styles are also visible in the Pobo Page Builder admin, where
you can remove them at any time.

Or hand Claude a product list from a client:

> Here is the client's xlsx with the products to rewrite — label them
> "Sportrec úprava 07/2026" in Pobo.

Claude resolves the products (URLs, EANs, codes, or names), creates the label, and
attaches it — ambiguous or unmatched items are reported back instead of guessed.
The labeled batch is then filterable in the Pobo Page Builder admin product grid.

## What's in the plugin

- `skills/style-widgets/` — the workflow for AI styling of widgets
- `skills/label-products/` — the workflow for labeling products from a client-supplied list

The connection to the Pobo Page Builder MCP server is set up by the `claude mcp add`
command above (OAuth login in the browser), not bundled in the plugin.

## About

Made by [Pobo Page Builder](https://www.pobo.space).
