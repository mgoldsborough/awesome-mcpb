# MCPB Packaging Guide

How to create an MCPB bundle from an existing MCP server.

## Tools

| Tool | Purpose | Install |
|------|---------|---------|
| **mcpb** | Build bundles | `npm i -g @anthropic-ai/mcpb` |
| **mpak** | Run and test bundles | `npm i -g @nimblebrain/mpak` |

## Quick Start

```bash
# Clone the server you want to package
git clone https://github.com/example/mcp-server
cd mcp-server

# Initialize manifest
mcpb init

# Validate your manifest
mcpb validate manifest.json

# Pack the bundle
mcpb pack . my-server.mcpb

# Test it locally
mpak run ./my-server.mcpb
```

## Bundle Structure

An MCPB bundle is a single file containing:

```
your-server.mcpb
  manifest.json    # Metadata and config
  src/             # Server source code
  deps/            # Bundled dependencies
```

## Creating manifest.json

Initialize with `mcpb init` or create manually:

```json
{
  "name": "my-server",
  "version": "1.0.0",
  "description": "What this server does",
  "author": "Your Name",
  "license": "MIT",
  "repository": "https://github.com/you/my-server",

  "mcp_config": {
    "command": "node",
    "args": ["${__dirname}/dist/index.js"]
  },

  "env": {
    "API_KEY": {
      "description": "Your API key",
      "required": true
    }
  }
}
```

Validate with:

```bash
mcpb validate manifest.json
```

## Node.js Servers

```json
{
  "mcp_config": {
    "command": "node",
    "args": ["${__dirname}/dist/index.js"]
  }
}
```

Steps:

1. Build the server: `npm run build`.
2. Ensure the entry point is correct.
3. Pack: `mcpb pack . my-server.mcpb`.

## Python Servers

```json
{
  "mcp_config": {
    "command": "python",
    "args": ["-m", "package_name.server"]
  }
}
```

Use module execution (`-m`) to handle relative imports correctly.

Steps:

1. Include all Python files.
2. Bundle dependencies in `deps/`.
3. mpak auto-sets `PYTHONPATH=deps/`.

## Environment Variables

Declare required env vars in the manifest:

```json
{
  "env": {
    "API_KEY": {
      "description": "API key for the service",
      "required": true
    },
    "DEBUG": {
      "description": "Enable debug logging",
      "required": false,
      "default": "false"
    }
  }
}
```

Users provide these when running:

```bash
API_KEY=xxx mpak run @nimblebraininc/my-server
```

## Testing Your Bundle

Before publishing, test locally:

```bash
# Validate the manifest
mcpb validate manifest.json

# Pack and inspect
mcpb pack . my-server.mcpb
mcpb info my-server.mcpb

# Run the bundle
mpak run ./my-server.mcpb

# Test with environment variables
API_KEY=test mpak run ./my-server.mcpb

# Verify tools are exposed
echo '{"jsonrpc":"2.0","method":"tools/list","params":{},"id":1}' | mpak run ./my-server.mcpb
```

## CI/CD with GitHub Actions

Use the `mcpb-pack` action to build bundles in CI:

```yaml
name: Build MCPB

on:
  push:
    tags:
      - 'v*'

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4

      - name: Build bundle
        uses: nimblebraininc/mcpb-pack@v1
        with:
          manifest: manifest.json
          output: my-server.mcpb

      - name: Upload artifact
        uses: actions/upload-artifact@v4
        with:
          name: bundle
          path: my-server.mcpb
```

## Best Practices

### Keep stdout clean

MCP uses JSON-RPC over stdout. Any non-JSON output breaks the protocol.

```python
# Wrong - prints to stdout
print("Starting server...")

# Right - prints to stderr
import sys
print("Starting server...", file=sys.stderr)
```

### Pin dependencies

Include exact versions to ensure reproducibility.

### Test on a fresh machine

Before publishing, test on a machine without your dev environment to catch missing dependencies.

### Version semantically

- Patch (1.0.x): Bug fixes.
- Minor (1.x.0): New features, backward compatible.
- Major (x.0.0): Breaking changes.

## mcpb Commands

| Command | Description |
|---------|-------------|
| `mcpb init` | Create a new manifest. |
| `mcpb validate <manifest>` | Validate manifest. |
| `mcpb pack <dir> <output>` | Pack into .mcpb file. |
| `mcpb unpack <mcpb> [dir]` | Extract bundle contents. |
| `mcpb info <mcpb>` | Show bundle metadata. |
| `mcpb clean <mcpb>` | Validate and minimize. |
| `mcpb sign <mcpb>` | Sign bundle. |
| `mcpb verify <mcpb>` | Verify signature. |

## mpak Commands

| Command | Description |
|---------|-------------|
| `mpak run <package>` | Run a bundle. |
| `mpak search <query>` | Search registry. |
| `mpak bundle show <package>` | Show bundle details. |
| `mpak bundle pull <package>` | Download bundle. |

## Troubleshooting

### Module not found

Dependencies are not bundled correctly. Check that `deps/` includes all required packages.

### Invalid JSON-RPC

Something is printing to stdout. Redirect logs to stderr.

### Connection refused

The server is not starting. Check the command and args in your manifest.

## Examples

See these bundles for reference:

- [echo](https://github.com/NimbleBrainInc/mcp-echo) - Simple Python server.
- [ipinfo](https://github.com/NimbleBrainInc/mcp-ipinfo) - Python with API key.

## Need Help?

- Open an issue on [awesome-mcpb](https://github.com/mgoldsborough/awesome-mcpb/issues).
- Read the [MCPB spec](https://github.com/modelcontextprotocol/mcpb).
