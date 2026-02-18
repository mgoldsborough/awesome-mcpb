# Wanted: Servers That Need Packaging

These popular MCP servers do not have MCPB bundles yet. Pick one and package it.

## How to Claim

1. Open an [issue](https://github.com/mgoldsborough/awesome-mcpb/issues/new?template=claim-packaging.yml) to claim the server.
2. You will be assigned the issue to prevent duplicate work.
3. Package it following the [packaging guide](packaging-guide.md).
4. Submit a pull request adding it to the readme.

## Official MCP Servers

From [modelcontextprotocol/servers](https://github.com/modelcontextprotocol/servers):

| Server | Description | Difficulty |
|--------|-------------|------------|
| [filesystem](https://github.com/modelcontextprotocol/servers/tree/main/src/filesystem) | File operations with access controls. | Easy |
| [memory](https://github.com/modelcontextprotocol/servers/tree/main/src/memory) | Knowledge graph persistent memory. | Medium |
| [git](https://github.com/modelcontextprotocol/servers/tree/main/src/git) | Git repository operations. | Easy |
| [fetch](https://github.com/modelcontextprotocol/servers/tree/main/src/fetch) | Web content fetching. | Easy |
| [slack](https://github.com/modelcontextprotocol/servers/tree/main/src/slack) | Slack messaging and channels. | Medium |
| [puppeteer](https://github.com/modelcontextprotocol/servers/tree/main/src/puppeteer) | Browser automation. | Medium |
| [brave-search](https://github.com/modelcontextprotocol/servers/tree/main/src/brave-search) | Web search. | Easy |
| [google-drive](https://github.com/modelcontextprotocol/servers/tree/main/src/gdrive) | Google Drive file access. | Hard |
| [google-maps](https://github.com/modelcontextprotocol/servers/tree/main/src/google-maps) | Maps and places API. | Medium |
| [sentry](https://github.com/modelcontextprotocol/servers/tree/main/src/sentry) | Error tracking integration. | Medium |
| [sequential-thinking](https://github.com/modelcontextprotocol/servers/tree/main/src/sequentialthinking) | Step-by-step reasoning. | Easy |
| [everart](https://github.com/modelcontextprotocol/servers/tree/main/src/everart) | AI image generation. | Medium |
| [aws-kb-retrieval](https://github.com/modelcontextprotocol/servers/tree/main/src/aws-kb-retrieval) | AWS Bedrock knowledge bases. | Hard |

## Popular Community Servers

High-star repos from the community:

| Server | Stars | Description | Difficulty |
|--------|-------|-------------|------------|
| [browser-use](https://github.com/browser-use/browser-use) | 5k+ | Browser automation framework. | Medium |
| [obsidian-mcp](https://github.com/smithery-ai/obsidian-mcp) | 2k+ | Obsidian vault access. | Medium |
| [notion-mcp](https://github.com/makenotion/notion-mcp-server) | 1k+ | Notion pages and databases. | Medium |
| [blender-mcp](https://github.com/ahujasid/blender-mcp) | 1k+ | Blender 3D integration. | Hard |
| [linear-mcp](https://github.com/jerhadf/linear-mcp-server) | 500+ | Linear issue tracking. | Easy |
| [supabase-mcp](https://github.com/supabase-community/supabase-mcp) | 500+ | Supabase backend. | Medium |
| [docker-mcp](https://github.com/ckreiling/mcp-server-docker) | 300+ | Docker container management. | Medium |
| [sqlite-mcp](https://github.com/nicholasgriffintn/sqlite-mcp) | 300+ | SQLite database. | Easy |
| [redis-mcp](https://github.com/redis/mcp-redis) | 200+ | Redis key-value store. | Easy |
| [kubernetes-mcp](https://github.com/strowk/mcp-k8s-go) | 200+ | Kubernetes cluster operations. | Hard |

## Difficulty Guide

- **Easy.** Simple Node.js or Python server, few dependencies, straightforward config.
- **Medium.** Multiple dependencies, environment setup needed, API keys required.
- **Hard.** Complex dependencies, native bindings, tricky auth flows.

## In Progress

Servers currently being packaged:

| Server | Claimed By | Started |
|--------|------------|---------|
| (none yet) | | |

---

Do not see a server you want? Open an [issue](https://github.com/mgoldsborough/awesome-mcpb/issues/new?template=suggest-bundle.yml) to suggest it.
