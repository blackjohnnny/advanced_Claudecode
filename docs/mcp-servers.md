# MCP Servers Guide

This project comes with four pre-configured [Model Context Protocol (MCP)](https://modelcontextprotocol.io/) servers. MCP servers extend Claude Code's capabilities by providing additional tools and data sources.

## Included Servers

### Sequential Thinking

**Package:** `@anthropic-ai/sequential-thinking`
**Configuration required:** None

Provides structured reasoning capabilities. Claude can use this server to break down complex problems into sequential steps, making its thinking process more transparent and methodical.

**When it's useful:**
- Complex debugging sessions
- Architecture decisions
- Multi-step problem solving

### GitHub

**Package:** `@modelcontextprotocol/server-github`
**Configuration required:** `GITHUB_TOKEN` environment variable

Provides direct access to GitHub's API — repositories, issues, pull requests, and more. Claude can read issues, review PRs, check CI status, and interact with your GitHub repositories.

**When it's useful:**
- Reviewing pull requests
- Reading and creating issues
- Checking CI/CD status
- Browsing repository contents on GitHub

**Setup:**

1. Create a personal access token at [github.com/settings/tokens](https://github.com/settings/tokens)
2. Set the environment variable:

   **macOS / Linux:**
   ```bash
   export GITHUB_TOKEN="your-token-here"
   ```

   **Windows (PowerShell):**
   ```powershell
   $env:GITHUB_TOKEN = "your-token-here"
   ```

   To make it permanent, add it to your shell profile (`.bashrc`, `.zshrc`) or system environment variables.

### Context7

**Package:** `@upstash/context7-mcp`
**Configuration required:** None

Provides live documentation lookup for libraries and frameworks. Instead of relying on potentially outdated training data, Claude can fetch current documentation directly.

**When it's useful:**
- Working with unfamiliar libraries
- Checking API changes in newer versions
- Verifying function signatures and parameters

### Filesystem

**Package:** `@modelcontextprotocol/server-filesystem`
**Configuration required:** None (scoped to project directory)

Provides advanced filesystem operations beyond Claude Code's built-in tools. Useful for bulk file operations and directory management.

**When it's useful:**
- Complex file operations
- Directory tree analysis
- Bulk file management

## How MCP Servers Work

MCP servers are defined in `.mcp.json` at the project root. When Claude Code starts, it reads this file and launches the configured servers. Each server runs as a separate process and communicates with Claude via the MCP protocol.

```json
{
  "mcpServers": {
    "server-name": {
      "command": "npx",
      "args": ["-y", "package-name"],
      "env": {
        "OPTIONAL_VAR": "${ENV_VAR_NAME}"
      }
    }
  }
}
```

- `command` + `args` — how to start the server (usually via `npx`)
- `env` — environment variables passed to the server
- `${VAR_NAME}` syntax reads from your system environment variables

## Adding More Servers

To add a new MCP server, edit `.mcp.json` and add a new entry:

```json
{
  "mcpServers": {
    "existing-server": { ... },
    "new-server": {
      "command": "npx",
      "args": ["-y", "@scope/mcp-server-name"],
      "env": {}
    }
  }
}
```

Browse available MCP servers at [github.com/modelcontextprotocol/servers](https://github.com/modelcontextprotocol/servers).

## Troubleshooting

### Server fails to start

- Ensure Node.js 18+ is installed
- Check your internet connection (servers install via `npx` on first use)
- Run `npx -y <package-name>` manually to see error messages

### GitHub server returns 401

- Verify `GITHUB_TOKEN` is set: `echo $GITHUB_TOKEN`
- Check the token hasn't expired
- Ensure the token has the required scopes (repo, read:org)

### Server is slow on first use

This is normal — `npx` downloads and installs the package on first run. Subsequent launches are faster.
