# ai-agent-config

Configs for AI agents - using as a backup, and sharing in case it's helpful to someone else

## What's here

- `skills/` - reusable instruction sets for AI coding agents
  - `deslop` - cut over-explained, AI-sounding prose from comments, docs, PR bodies, and drafts
  - `vet-plan` - second pass over a plan before acting on it: correctness, problem fit, over-engineering
  - `vet-review` - second pass over code review findings: verify each one against the actual code before acting
- `mcp.json` - MCP server config

## Usage

Each skill is a folder with a `SKILL.md` of plain markdown instructions - no code, no credentials. If your agent supports skills or custom commands, drop the folder into its skills directory and invoke it by name; otherwise the instructions work as a plain prompt to paste in.
