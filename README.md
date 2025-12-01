# Augmented Code Configuration

Reusable AI agent configurations for development workflows. Designed for XP/TDD practitioners who want consistent, high-quality AI assistance.

## Repository Structure

```
.
├── .agents/rules/
│   └── base.md             # 📌 TypeScript rules (single source of truth)
├── .vscode/                # VS Code configuration
│   ├── tasks.json          # npm script tasks
│   ├── settings.json       # TypeScript/ESLint/Prettier settings
│   └── extensions.json     # Recommended extensions
├── .cursor/                # Optional: Cursor IDE commands
│   ├── commands/           # Slash commands
│   └── rules/              # Rule that references base.md
├── AGENTS.md → base.md     # Symlink for OpenAI Codex
├── CLAUDE.md → base.md     # Symlink for Claude
└── GEMINI.md → base.md     # Symlink for Gemini
```

### Key Concept

**One ruleset (TypeScript), multiple entry points.** All AI agents use the same TypeScript rules defined in `.agents/rules/base.md`. The symlinks (AGENTS.md, CLAUDE.md, GEMINI.md) allow each tool to find the rules in its expected location.

## Available Commands

Cursor IDE slash commands. Copy to `.cursor/commands/` or adapt for other tools:

| Command | Purpose |
|---------|---------|
| `fe-code-review` | Review pending changes (tests, maintainability, rules) |
| `fe-increase-coverage` | Identify and test high-value untested code |
| `fe-plan-untested-code` | Create actionable plan to cover untested code |
| `fe-predict-problems` | Predict likely production failures |
| `fe-mikado-method` | Guide safe, incremental refactoring |
| `fe-technical-debt` | Catalog and prioritize technical debt |
| `fe-xp-simple-design-refactor` | Apply XP Simple Design principles |
| `fe-security-analysis` | Pragmatic security risk analysis |

## Usage

### For TypeScript Projects (VS Code)

```bash
# Copy VS Code configuration
cp -r .vscode /path/to/your/project/
cp CLAUDE.md /path/to/your/project/

# See TYPESCRIPT_SETUP.md for complete setup guide
```

See [TYPESCRIPT_SETUP.md](TYPESCRIPT_SETUP.md) for detailed instructions.

### For Other AI Tools

Copy the symlink:

```bash
# Example: for Claude
ln -s .agents/rules/base.md CLAUDE.md
```

## Philosophy

These configurations enforce:
- **TDD**: Test-first, one failing test at a time
- **Baby Steps**: Small, incremental changes
- **Simple Design**: Clarity over cleverness
- **High Quality**: Strict validation before commits

## License

[Unlicense](https://unlicense.org) — Public Domain
