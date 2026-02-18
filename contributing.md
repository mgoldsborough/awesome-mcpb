# Contributing to Awesome MCPB

Thanks for helping grow the MCPB ecosystem. This list curates the best MCPB bundles available.

## Adding a Bundle

To add a bundle to the list:

1. Fork this repository.
2. Add your entry in the correct category, maintaining **alphabetical order**.
3. Use the standard format: `- [Name](https://repo-url) - Short description ending with a period.`
4. Submit a pull request.

### Entry Requirements

Bundles must meet these criteria:

- **Published and functional.** The bundle must be available to install and run.
- **Has a public repository.** Source code must be accessible on GitHub or similar.
- **Actively maintained.** Updated within the last 12 months with no critical unresolved issues.
- **Accurate metadata.** Name, description, and version are correct.
- **Clean stdout.** Only JSON-RPC on stdout; logs go to stderr.

### Entry Format

```markdown
- [Bundle Name](https://github.com/org/repo) - One sentence describing what it does.
```

- Description starts with a capital letter.
- Description ends with a period.
- Do not repeat the bundle name in the description.
- Do not use badges or emoji in entries.
- Keep descriptions under 120 characters.

## Packaging a New Server

Want to create a new MCPB bundle for an existing MCP server?

1. Check the [wanted list](docs/wanted.md) for servers that need packaging.
2. Open an issue to claim the server (prevents duplicate work).
3. Follow the [packaging guide](docs/packaging-guide.md).
4. Test your bundle locally.
5. Submit a pull request adding it to the readme.

## Suggesting a Server

Know a popular MCP server that should be bundled? Open an issue with:

- Server name and repository link.
- Why it is valuable (use case, popularity).
- Estimated difficulty (Easy, Medium, Hard).

## Reporting Issues

Found a problem with a listed bundle? Open an issue with:

- Bundle name and version.
- What happened vs. what you expected.
- Steps to reproduce.
- Error output.

## Quality Over Quantity

This is a curated list, not a comprehensive directory. Not every MCPB bundle belongs here. We prioritize bundles that are well-maintained, solve real problems, and work reliably.
