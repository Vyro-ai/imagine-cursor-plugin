# ImagineArt for Cursor

Generate images, videos, music, ads, and complete creative workflows using the ImagineArt MCP from Cursor.

## Installation

### Cursor Marketplace

In Cursor, type `/add-plugin` in chat, search for **ImagineArt**, and install it.

You can also install directly from [Cursor Marketplace](https://cursor.com/marketplace/imagineart).

### From source (local development)

Cursor scans `~/.cursor/plugins/local/<plugin-name>/` for local plugins. Copy this repo into that directory:

```bash
git clone https://github.com/Vyro-ai/imagine-cursor-plugin.git
mkdir -p ~/.cursor/plugins/local
rsync -a --delete --exclude='.git' imagine-cursor-plugin/ ~/.cursor/plugins/local/imagineart/
```

Reload Cursor: `Cmd-Shift-P → Developer: Reload Window`.

Verify:

- `Customize → Plugins` lists **ImagineArt**.
- `Customize → MCPs` shows `ImagineArt`. The first connection prompts authentication.

The copy-based setup above matches the packaged Marketplace layout. Current Cursor versions also support symlinking the repository for local iteration.

#### Updating

After pulling new commits, re-run the rsync and reload Cursor:

```bash
cd imagine-cursor-plugin && git pull
rsync -a --delete --exclude='.git' ./ ~/.cursor/plugins/local/imagineart/
```

#### Uninstall

```bash
rm -rf ~/.cursor/plugins/local/imagineart
```

then reload Cursor.

## Usage

The plugin adds a single entrypoint command that routes your request to the right ImagineArt MCP tool:

```
/imagine <request>
```

Examples:

```
/imagine Generate an image of a ginger cat sitting on an orange sofa in 9:16 format
/imagine Animate this image using seedance 2.5 for 5s in 1080p
/imagine Make a UGC ad of this product <url>/<image>
/imagine List my generations
/imagine What is my credit balance?
```

You can also ask in plain chat once the MCP is connected — the `/imagine` command mainly helps Cursor pick the correct tool and preserve your original wording.

If your account has more than one organization, you will be asked to pick one at the start of a chat. With a single organization it is selected automatically.

## What's in this plugin

| File | Purpose |
| --- | --- |
| `.cursor-plugin/plugin.json` | Plugin manifest (name, version, publisher, logo) |
| `mcp.json` | Registers the hosted ImagineArt MCP server at `https://mcp.imagine.art` |
| `commands/imagine.md` | The `/imagine` slash command and its tool-routing instructions |
| `assets/logo.svg` | Plugin icon shown in Cursor |

## Troubleshooting

- **Plugin not listed after install** — confirm the directory name under `~/.cursor/plugins/local/` and that `.cursor-plugin/plugin.json` sits at its root, then reload the window.
- **MCP shows as disconnected** — open `Customize → MCPs`, click `ImagineArt` to re-run authentication, and check that `https://mcp.imagine.art` is reachable from your network.
- **`/imagine` not offered in chat** — the command file must be at `commands/imagine.md`; reload Cursor after adding or renaming it.

## License

MIT. See [LICENSE](./LICENSE).

## Support

- Issues: [github.com/Vyro-ai/imagine-cursor-plugin/issues](https://github.com/Vyro-ai/imagine-cursor-plugin/issues)
- Contact: [support@imagine.art](mailto:support@imagine.art)
