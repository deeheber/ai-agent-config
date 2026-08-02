# ai-agent-config

Configs for AI agents - using as a backup, and sharing in case it's helpful to someone else

## What's here

- `skills/` - reusable instruction sets for AI coding agents
  - `better-documents` - generate and review effective business documents; copied from Anil Dash's [`better-documents`](https://github.com/anildash/better-documents) (GPL-3.0), based on [Make better documents](https://www.anildash.com/2024/03/10/make-better-documents/)
  - `deslop` - cut over-explained, AI-sounding prose from comments, docs, PR bodies, and drafts
  - `vet-plan` - second pass over a plan before acting on it: correctness, problem fit, over-engineering
  - `vet-review` - second pass over code review findings: verify each one against the actual code before acting
- `mcp.json` - MCP server config

## Usage

Each skill is a folder with a `SKILL.md` of plain markdown instructions - no code, no credentials. If your agent supports skills or custom commands, drop the folder into its skills directory and invoke it by name; otherwise the instructions work as a plain prompt to paste in.

## License

This repository is MIT-licensed except `skills/better-documents`, which is by Anil Dash and distributed under GPL-3.0. See its [source repository](https://github.com/anildash/better-documents), [notice](skills/better-documents/NOTICE.md), and [license](skills/better-documents/LICENSE).
