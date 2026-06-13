# Pobo Page Builder — Claude Code plugin

AI styling of [Pobo Page Builder](https://www.pobo.space) widgets to match your
e-shop's design. Claude reads your e-shop's look (colors, fonts, buttons, border
radius), generates matching styles, and deploys them through Pobo Page Builder —
nothing runs on your machine, all logic lives on the backend.

Supported platforms: Shoptet, Shopify, WooCommerce, PrestaShop, Upgates.

## Installation

In [Claude Code](https://claude.com/claude-code), run:

```
/plugin marketplace add pobo-builder/claude-plugin
/plugin install pobo@pobo-builder
```

## Connecting your Pobo Page Builder account

In the Pobo Page Builder admin, open the **"Connect Claude"** page and copy the
ready-made command (it already contains your personal token). Paste it into your
terminal:

```
claude mcp add -s user --transport http pobo https://api.pobo.space/mcp/client \
    --header "Authorization: Bearer <token>"
```

That's it — no environment variables, no config files to edit. The connection persists
across all your projects. The token is shown only once; if you ever need to reconnect,
generate a new one on the same page and run the command again (it overwrites the old
connection).

Never commit the token to any repository — it is a per-user secret.

## Usage

Just tell Claude, for example:

> Make my Pobo Page Builder widgets match my e-shop's design.

Claude picks the e-shop, reads its design, generates the styles, and deploys them.
You can then review the changes on your e-shop (hard refresh) and iterate with
feedback. Deployed AI styles are also visible in the Pobo Page Builder admin, where
you can remove them at any time.

## What's in the plugin

- `skills/style-widgets/` — the workflow for AI styling of widgets

The connection to the Pobo Page Builder MCP server is set up by the `claude mcp add`
command above, not bundled in the plugin (the token is per-user, so it cannot ship in
a public repo).

## About

Made by [Pobo Page Builder](https://www.pobo.space).
