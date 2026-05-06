# Claude Skills Manager

Track Claude Code plugins, skills, and marketplaces across multiple machines.

## Structure

```
machines/
  strongstrong2.yaml   # MacBook Air
  <hostname>.yaml      # Add more machines here
```

Each YAML file is a full inventory of one machine: marketplaces, plugins, standalone skills, and where each came from.

## Adding a Machine

1. Create `machines/<hostname>.yaml` using an existing file as template
2. List all marketplaces, plugins, and skills installed on that machine
3. Commit

## Re-installing on a Fresh Machine

Tell Claude Code:

> Read `machines/<hostname>.yaml` and install everything listed.

It will:
1. Add marketplaces: `claude plugin marketplace add github:<repo>`
2. Install plugins: `claude plugin install <name>`
3. Enable plugins: `claude plugin enable <name>`
4. Standalone skills are auto-installed when their source marketplace is added

## Comparing Machines

Diff any two YAML files to see what one machine has that another doesn't.

## Sources

| Source | Install mechanism | What it provides | Installed on |
|---|---|---|---|
| [googleworkspace/cli](https://github.com/googleworkspace/cli) | `~/.agents` skill installer (separate from Claude plugin system). Symlinks into `~/.claude/skills/`. Lock file: `~/.agents/.skill-lock.json` | 107 skills (GWS core, recipes, personas) | strongstrong2 |
| [anthropics/skills](https://github.com/anthropics/skills) | Claude plugin marketplace: `claude plugin marketplace add github:anthropics/skills` | 16 skills (document processing, design, dev tools) | strongstrong2 |
| [anthropics/claude-plugins-official](https://github.com/anthropics/claude-plugins-official) | Claude plugin marketplace (built-in): `claude plugin install clangd-lsp@claude-plugins-official` | clangd-lsp plugin (LSP, no skills) | strongstrong2 |
| [obra/superpowers](https://github.com/obra/superpowers) | Claude plugin marketplace: `claude plugin install superpowers@claude-plugins-official` | 14 dev workflow skills (TDD, debugging, planning, code review) | strongstrong2 |
| [kepano/obsidian-skills](https://github.com/kepano/obsidian-skills) | Claude plugin marketplace: `claude plugin install obsidian@obsidian-skills` | 5 Obsidian vault skills | strongstrong2 |
| Manual install | Manually created in `~/.claude/skills/` | 2 skills (notebooklm, nano-banana) | strongstrong2 |
| Claude Code built-in | Ships with Claude Code binary, not installable/removable | 6 utility skills (loop, schedule, simplify, etc.) | strongstrong2 |
