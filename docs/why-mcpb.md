# Why MCPB?

MCP servers are powerful, but getting them running is painful.

## The Problem

Today, using an MCP server means:

1. Find the repo on GitHub.
2. Clone it.
3. Figure out if it needs Node, Python, Rust, Go, or something else.
4. Install the right runtime version.
5. Install dependencies.
6. Read the README to understand configuration.
7. Debug why it does not work.
8. Finally run it.

That is 30 minutes for something that should take 30 seconds.

## The MCPB Solution

MCPB (MCP Bundle) packages everything into a single file:

```bash
mpak run @nimblebraininc/github
```

Done. No cloning, no installing, no debugging.

## What Is in a Bundle?

```
server.mcpb
  manifest.json    # Metadata, config, env vars
  src/             # Server code
  deps/            # All dependencies, bundled
```

Everything needed to run is included.

## Comparison

| Step | Traditional | MCPB |
|------|-------------|------|
| Find server | Browse GitHub | Browse mpak.dev |
| Install | Clone and setup | `mpak run` |
| Dependencies | Manual install | Included |
| Config | Read README | Declared in manifest |
| Runtime | Install Node or Python | Handled by mpak |
| Time to run | 10-30 minutes | 10 seconds |

## Benefits for Users

- **Instant setup.** One command to run any server.
- **No dependency conflicts.** Each bundle is isolated.
- **Discoverable.** Browse a registry instead of searching GitHub.
- **Consistent experience.** Same command for every server.

## Benefits for Server Authors

- **Distribution.** Publish once, users install instantly.
- **Versioning.** Semantic versions, users can pin.
- **Discoverability.** Listed on registries.
- **Less support.** No environment-specific issues.

## Learn More

- [MCPB Specification](https://github.com/modelcontextprotocol/mcpb) - Official format spec.
- [Packaging Guide](packaging-guide.md) - How to create a bundle.
- [mpak.dev](https://mpak.dev) - Browse available bundles.
