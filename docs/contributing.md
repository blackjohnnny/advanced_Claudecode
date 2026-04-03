# Contributing

Thank you for your interest in contributing to Claude Code Pro Max! This guide explains how to contribute effectively.

## How to Contribute

### Reporting Issues

If you find a bug or have a suggestion:

1. Check [existing issues](../../issues) to avoid duplicates
2. Open a new issue with a clear title and description
3. Include steps to reproduce (for bugs) or a use case (for features)

### Submitting Changes

1. **Fork** the repository
2. **Create a branch** from `main`:
   ```bash
   git checkout -b feature/your-feature-name
   ```
3. **Make your changes** following the conventions below
4. **Test your changes** (see Testing section)
5. **Commit** using Conventional Commits:
   ```bash
   git commit -m "feat: add new agent for SQL review"
   ```
6. **Push** and open a pull request

## Conventions

### Language

- **British English throughout** — colour, behaviour, licence, organise, centre
- This is a UK-based project (DofE Gold Skills) and consistency matters

### File Naming

- Agent files: `kebab-case.md` in `.claude/agents/`
- Documentation: `kebab-case.md` in `docs/`
- Scripts: `setup.sh` / `setup.ps1` naming pattern

### Commit Messages

Follow [Conventional Commits](https://www.conventionalcommits.org/):

- `feat:` — new feature or agent
- `fix:` — bug fix
- `docs:` — documentation changes
- `refactor:` — restructuring without behaviour change
- `chore:` — maintenance tasks

### Agent Quality

If you're contributing an agent or modifying the factory:

- Follow the frontmatter format exactly (see [Agent Factory Guide](agent-factory.md))
- Apply the principle of least privilege for tools
- Write specific, actionable instructions (not vague)
- Define boundaries — what the agent should NOT do
- Include output format where applicable

### Documentation

- Keep guides practical and scannable
- Use tables for structured information
- Include code examples for anything non-obvious
- Link to related guides where relevant

## Testing Your Changes

### Testing CLAUDE.md Changes

1. Start Claude Code in the project directory
2. Try a few interactions to verify the new rules take effect
3. Test edge cases — does the decision framework work as expected?

### Testing Agent Changes

1. Invoke the agent: ask Claude to use it
2. Verify it stays within its defined role
3. Check it uses only its permitted tools
4. Confirm the output format matches the spec

### Testing MCP Server Changes

1. Start Claude Code and check the MCP server initialises
2. Try using a tool provided by the server
3. Verify environment variable placeholders work

### Testing Setup Scripts

**Unix:**
```bash
chmod +x setup.sh
./setup.sh
```

**Windows:**
```powershell
.\setup.ps1
```

Verify the script:
- Correctly detects installed/missing prerequisites
- Handles the GitHub token prompt gracefully
- Displays the welcome summary

## What We're Looking For

Contributions that would be particularly welcome:

- **New MCP server configurations** — well-tested, useful servers with clear documentation
- **Improvements to CLAUDE.md** — better rules, clearer principles, or new sections based on real-world usage
- **Agent Factory improvements** — making the factory team smarter and more effective
- **Documentation** — better guides, more examples, clearer explanations
- **Bug fixes** — anything that doesn't work as described

## Code of Conduct

Be respectful, constructive, and professional. We're all here to build something useful.
