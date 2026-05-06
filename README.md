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

| Source | What it provides | Installed on |
|---|---|---|
| [googleworkspace/cli](https://github.com/googleworkspace/cli) | 107 skills (GWS core, recipes, personas) via ~/.agents | strongstrong2 |
| [anthropics/skills](https://github.com/anthropics/skills) | 16 skills (document processing, design, dev tools) | strongstrong2 |
| [anthropics/claude-plugins-official](https://github.com/anthropics/claude-plugins-official) | clangd-lsp plugin | strongstrong2 |
| [obra/superpowers](https://github.com/obra/superpowers) | 14 dev workflow skills (TDD, debugging, planning, code review) | strongstrong2 |
| [kepano/obsidian-skills](https://github.com/kepano/obsidian-skills) | 5 Obsidian vault skills | strongstrong2 |
| Manual install | 2 skills (notebooklm, nano-banana) | strongstrong2 |
| Claude Code built-in | 6 utility skills (loop, schedule, simplify, etc.) | strongstrong2 |
