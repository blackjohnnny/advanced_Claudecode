# Claude Code Pro Max

[![MIT Licence](https://img.shields.io/badge/licence-MIT-blue.svg)](LICENSE)
[![Node.js](https://img.shields.io/badge/node-%3E%3D18-brightgreen.svg)](https://nodejs.org/)
[![Claude Code](https://img.shields.io/badge/Claude%20Code-Pro%20Max-blueviolet.svg)](https://claude.com/claude-code)

A professionally configured Claude Code environment that gives you a pro-level setup out of the box. Clone it, open it, and start building with an Agent Factory, MCP servers, and a first-principles CLAUDE.md.

---

## Quick Start

```bash
git clone https://github.com/your-username/claude-code-pro-max.git
cd claude-code-pro-max
claude
```

That's it. Everything is picked up automatically — the project rules, permissions, MCP servers, and agents are all ready to go.

> **Optional:** To enable the GitHub MCP server, set your token: `export GITHUB_TOKEN="your-token"` (Unix) or `$env:GITHUB_TOKEN = "your-token"` (Windows). The other three MCP servers work without any configuration.

---

## What's Inside

| Component | Description |
|-----------|-------------|
| **CLAUDE.md** | First-principles project rules — decision-making framework, root cause debugging, proactive mentoring, quality standards |
| **Agent Factory** | Four specialist agents that design and build custom agent teams for any project |
| **MCP Servers** | Pre-configured sequential-thinking, GitHub, context7, and filesystem servers |
| **Permissions** | Permissive defaults with safety guardrails — no destructive commands |

## The Agent Factory

Instead of shipping pre-built agents that might not fit your project, Claude Code Pro Max includes an **Agent Factory** — a team of four agents that design and build custom agent teams tailored to your needs.

| Agent | Role |
|-------|------|
| **Agent Architect** | Analyses your project and designs a team of agents |
| **Prompt Engineer** | Writes the agent files with proper prompts and frontmatter |
| **Systems Engineer** | Configures tools, permissions, and model selection |
| **QA Reviewer** | Reviews the team for quality, gaps, and issues |

### Build a Team in Four Steps

```
1. "Use the agent-architect to design a team for this project"
2. "Use the prompt-engineer to build the agents from the design"
3. "Use the systems-engineer to review the configurations"
4. "Use the qa-reviewer to do a final quality check"
```

The factory can build individual agents or entire coordinated teams — a full-stack development team, a testing pipeline, a documentation squad, or anything else your project needs.

## MCP Servers

Four servers pre-configured and ready to use:

| Server | Purpose | Setup Required |
|--------|---------|----------------|
| **Sequential Thinking** | Structured reasoning for complex problems | None |
| **GitHub** | Repository, issues, and PR integration | `GITHUB_TOKEN` |
| **Context7** | Live documentation lookup | None |
| **Filesystem** | Advanced file operations | None |

All servers install automatically via `npx` on first use — no manual installation needed.

## CLAUDE.md Philosophy

The CLAUDE.md is built on first principles, not a list of rules:

- **Understand before acting** — read existing code before making changes
- **Explore before building** — search for existing solutions before writing new code
- **Root cause resolution** — treat the sickness, not the symptom
- **Tiered decision-making** — low impact: decide and move on; medium: research and explain; high: present options to the user
- **Proactive mentoring** — surface knowledge gaps and better approaches
- **Be resourceful** — exhaust all options before asking

## Project Structure

```
.
├── CLAUDE.md                          # Project rules and philosophy
├── .claude/
│   ├── settings.json                  # Permissions and model config
│   └── agents/
│       ├── agent-architect.md         # Designs agent teams
│       ├── prompt-engineer.md         # Writes agent prompts
│       ├── systems-engineer.md        # Configures tools and integration
│       └── qa-reviewer.md            # Reviews agent quality
├── .mcp.json                          # MCP server configurations
├── .vscode/
│   └── extensions.json                # Recommends Claude Code extension
├── docs/
│   ├── getting-started.md             # Setup and first steps
│   ├── agent-factory.md               # Agent Factory usage guide
│   ├── mcp-servers.md                 # MCP server configuration
│   ├── customisation.md               # How to customise everything
│   └── contributing.md                # Contributing guide
├── LICENSE                            # MIT licence
└── README.md
```

## Customisation

Everything is designed to be modified. See the [Customisation Guide](docs/customisation.md) for details on:

- Editing CLAUDE.md to match your team's conventions
- Adjusting permissions for your security requirements
- Building and modifying agents
- Adding MCP servers
- Changing the Git workflow

## Documentation

| Guide | Description |
|-------|-------------|
| [Getting Started](docs/getting-started.md) | Prerequisites, setup, and first steps |
| [Agent Factory](docs/agent-factory.md) | How to use the factory to build agent teams |
| [MCP Servers](docs/mcp-servers.md) | Server configuration and troubleshooting |
| [Customisation](docs/customisation.md) | How to modify every part of the setup |
| [Contributing](docs/contributing.md) | How to contribute to the project |

## Requirements

- **Node.js 18+**
- **Claude Code CLI** (`npm install -g @anthropic-ai/claude-code`)
- **Git**

## Licence

This project is licensed under the [MIT Licence](LICENSE).

---

Built as a Gold DofE Skills project (IT section).
