# Agent Factory Guide

The Agent Factory is a team of four specialist agents that design and build custom agent teams for any project. Instead of shipping pre-built agents that might not fit your needs, the factory builds exactly what you require.

## The Factory Team

| Agent | Role | What It Does |
|-------|------|-------------|
| **Agent Architect** | Designer | Analyses your project and designs a team of agents tailored to your needs |
| **Prompt Engineer** | Builder | Writes the agent files with proper frontmatter and focused prompts |
| **Systems Engineer** | Integrator | Configures tool permissions, model selection, and inter-agent integration |
| **QA Reviewer** | Quality Gate | Reviews the team for gaps, vague prompts, and permission issues |

## Building Your First Agent Team

### Step 1: Design with the Architect

Start by telling Claude to use the Agent Architect:

```
Use the agent-architect to design a team of agents for this project
```

The Architect will:
1. Explore your codebase to understand the tech stack
2. Identify workflows that would benefit from specialist agents
3. Design a team with clear roles, tools, and boundaries
4. Present the design for your review

### Step 2: Build with the Prompt Engineer

Once you're happy with the design:

```
Use the prompt-engineer to build the agents from the architect's design
```

The Prompt Engineer will:
1. Create `.claude/agents/*.md` files for each agent
2. Write focused system prompts with clear instructions
3. Set up correct frontmatter (name, description, model, tools)

### Step 3: Review with the Systems Engineer

```
Use the systems-engineer to review the agent configurations
```

The Systems Engineer will:
1. Audit tool permissions (principle of least privilege)
2. Validate model selection (Opus vs Sonnet per task)
3. Check for conflicts between agents
4. Ensure the team works together seamlessly

### Step 4: Quality Check with QA

```
Use the qa-reviewer to review the complete agent team
```

The QA Reviewer will:
1. Check every agent for prompt quality and technical correctness
2. Verify team coverage — no gaps, no overlap
3. Produce a detailed review with actionable recommendations

## Modifying Existing Agents

The factory can also improve agents you've already built:

```
Use the prompt-engineer to improve the code-reviewer agent — make it check for security issues too
```

```
Use the systems-engineer to review my agents and tighten their permissions
```

## Agent File Format

Every agent follows this structure:

```markdown
---
name: Display Name
description: One-line description shown in agent selection
model: claude-opus-4-6
tools:
  - Read
  - Glob
  - Grep
---

# Agent Name

[System prompt with role, process, output format, and rules]
```

### Available Models

| Model | Best For | Trade-off |
|-------|----------|-----------|
| `claude-opus-4-6` | Complex reasoning, architecture, debugging | Slower, more expensive, highest quality |
| `claude-sonnet-4-6` | Code review, testing, documentation, routine tasks | Faster, cheaper, very capable |

### Available Tools

| Tool | Access Level | Use Case |
|------|-------------|----------|
| `Read` | Read-only | Reading files |
| `Glob` | Read-only | Finding files by pattern |
| `Grep` | Read-only | Searching file contents |
| `Edit` | Write | Modifying existing files |
| `Write` | Write | Creating new files |
| `Bash` | Execute | Running shell commands |
| `WebSearch` | External | Searching the web |
| `WebFetch` | External | Fetching web pages |
| `Agent` | Meta | Launching sub-agents |

## Tips

- **Start with the Architect** — don't skip the design step. A well-designed team is far more effective than ad-hoc agents.
- **Right-size your team** — every agent should earn its place. Don't create agents for the sake of it.
- **Use Sonnet for speed** — reserve Opus for agents that need deep reasoning.
- **Set boundaries** — every agent should know what it should NOT do.
- **Iterate** — run the QA Reviewer after changes and refine based on feedback.
