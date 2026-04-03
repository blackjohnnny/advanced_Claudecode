# Getting Started

Welcome to Claude Code Pro Max — a professionally configured Claude Code environment with an Agent Factory, MCP servers, and first-principles project rules.

## Prerequisites

Before you begin, ensure you have:

- **Node.js 18+** — [Download](https://nodejs.org/)
- **Git** — [Download](https://git-scm.com/)
- **Claude Code CLI** — Install with `npm install -g @anthropic-ai/claude-code`
- **VS Code** (recommended) — [Download](https://code.visualstudio.com/)

## Quick Start

### 1. Clone and Go

```bash
git clone https://github.com/your-username/claude-code-pro-max.git
cd claude-code-pro-max
claude
```

That's it. Claude automatically picks up:
- **CLAUDE.md** — the project rules and philosophy
- **.claude/settings.json** — permissions and model settings
- **.mcp.json** — MCP server configurations
- **.claude/agents/** — all factory agents

### 2. (Optional) Enable GitHub Integration

The GitHub MCP server needs a personal access token. Create one at [github.com/settings/tokens](https://github.com/settings/tokens), then set it:

**macOS / Linux:**
```bash
export GITHUB_TOKEN="your-token-here"
```

**Windows (PowerShell):**
```powershell
$env:GITHUB_TOKEN = "your-token-here"
```

To make it permanent, add it to your shell profile (`.bashrc`, `.zshrc`) or system environment variables. The other three MCP servers work without any configuration.

## What's Included

| Component | Description |
|-----------|-------------|
| `CLAUDE.md` | First-principles project rules, decision-making framework, quality standards |
| `.claude/settings.json` | Permissive permissions with safety guardrails |
| `.claude/agents/` | Agent Factory — 4 agents that build custom agent teams |
| `.mcp.json` | 4 pre-configured MCP servers |

## Next Steps

- **Build your first agent team** — See [Agent Factory Guide](agent-factory.md)
- **Configure MCP servers** — See [MCP Servers Guide](mcp-servers.md)
- **Customise the setup** — See [Customisation Guide](customisation.md)

## Troubleshooting

### Claude Code doesn't pick up CLAUDE.md

Make sure you're running `claude` from the root of this project directory. CLAUDE.md is loaded from the current working directory.

### MCP servers don't start

MCP servers install automatically via `npx` on first use. Ensure you have an internet connection and Node.js 18+. If the GitHub server fails, check that `GITHUB_TOKEN` is set.
