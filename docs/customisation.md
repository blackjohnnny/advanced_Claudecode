# Customisation Guide

Everything in Claude Code Pro Max is designed to be customised. This guide explains how to modify each component to suit your workflow.

## Customising CLAUDE.md

`CLAUDE.md` is the core configuration — it shapes how Claude behaves in your project. Edit it freely to match your team's conventions.

### Adding Project-Specific Rules

Add a section for your project's specific conventions:

```markdown
## Project-Specific Rules

- This project uses React with TypeScript
- All components must be functional components with hooks
- State management uses Zustand — no Redux
- API calls go through the `src/api/` layer, never directly in components
```

### Changing Response Style

Modify the **Response Style** section to match your preference:

- Want shorter responses? Add: "Maximum 3 sentences per explanation"
- Want more detail? Change "concise" to "thorough with examples"
- Want a different language? Replace "British English" with your preference

### Adjusting the Decision Framework

The tiered decision-making framework (low/medium/high impact) can be tuned:

- If you want Claude to be more autonomous, raise the threshold for what counts as "high impact"
- If you want more control, lower it

## Customising Permissions

Edit `.claude/settings.json` to change what Claude can do without asking.

### Making It More Restrictive

Remove tools from the `allow` list to require manual approval:

```json
{
  "permissions": {
    "allow": [
      "Read", "Glob", "Grep"
    ],
    "deny": [
      "Bash(rm -rf /*)",
      "Bash(git push --force *)",
      "Bash(git reset --hard *)"
    ]
  }
}
```

### Adding More Bash Commands

Whitelist additional commands:

```json
"Bash(docker *)",
"Bash(make *)",
"Bash(cargo *)"
```

### Denying Specific Actions

Add patterns to the `deny` list:

```json
"deny": [
  "Bash(rm -rf /*)",
  "Bash(git push --force *)",
  "Bash(git reset --hard *)",
  "Bash(DROP TABLE *)",
  "Bash(kubectl delete *)"
]
```

## Customising Agents

### Editing an Agent

Open any file in `.claude/agents/` and modify:

- **`model`** — switch between `claude-opus-4-6` and `claude-sonnet-4-6`
- **`tools`** — add or remove tools from the list
- **System prompt** — change the instructions, add rules, modify the output format

### Creating Agents Manually

If you prefer not to use the Agent Factory, create a file in `.claude/agents/`:

```markdown
---
name: My Custom Agent
description: Does something specific and useful
model: claude-sonnet-4-6
tools:
  - Read
  - Glob
  - Grep
---

# My Custom Agent

You are a specialist in [domain]. Your role is to [specific task].

## Process
1. [Step one]
2. [Step two]
3. [Step three]

## Output Format
[What the agent should produce]

## Rules
- [Constraint one]
- [Constraint two]
```

### Removing Agents

Simply delete the `.md` file from `.claude/agents/`. There's no registry to update.

## Customising MCP Servers

### Adding a Server

Edit `.mcp.json` and add a new entry. See the [MCP Servers Guide](mcp-servers.md) for details.

### Removing a Server

Delete the server's entry from `.mcp.json`. Claude Code will stop launching it.

### Changing Server Configuration

Each server's `env` block passes environment variables. Update these to change the server's behaviour (e.g., different API tokens, different scopes).

## Customising Git Workflow

The Git rules in CLAUDE.md use Conventional Commits by default. To change this:

### Using a Different Commit Format

Replace the Git Workflow section in CLAUDE.md with your team's format:

```markdown
## Git Workflow

### Commits
- Start with a ticket number: `PROJ-123: description`
- Use past tense: "Added feature" not "Add feature"
- Keep subject under 72 characters
```

### Changing Branch Naming

Update the branch prefixes to match your convention:

```markdown
### Branches
- `PROJ-123/description` — ticket-based naming
- `username/description` — developer-based naming
```

## Tips

- **Start with the defaults** — use the setup as-is for a few days before customising
- **Change one thing at a time** — makes it easier to identify what works
- **Keep CLAUDE.md focused** — it's a system prompt, not documentation
- **Test your changes** — after modifying an agent or CLAUDE.md, run a quick test to verify it behaves as expected
