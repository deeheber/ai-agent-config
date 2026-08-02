---
name: vet-review
description: >
  Critically reviews code-review findings for false positives, missed
  issues, and noise, validating every finding against the actual code
  rather than trusting the reported verdict. Use when a review has produced
  findings and you want them challenged before acting on them.
disable-model-invocation: true
---

# Vet Review

A second pass over review findings before you act on them.

## Instructions

Critically review the current code-review result (findings from a code-review command or similar). Do not edit the code or the review — return recommendations only, so they can be relayed to whoever owns it.

Check, validating every finding with tools (read the file, reproduce the failure scenario — never take the description at face value):
1. Is each finding actually correct?
2. Is the severity right for the *verified* impact, not just how alarming it reads?
3. Anything the review should have caught but missed, given what you now know about the code?

Then report exactly this, and nothing extra:

**Verdict** — one line: does the review hold up, or does the finding set need changes first? Call out up front if nothing changed.

**Checked** — a compact table, one row per finding:

| Finding | How checked | Holds? |
|---|---|---|
| ... | read foo.ts / reproduced X | yes / no / severity wrong |

**Revised findings** — one numbered list, most-important-first, including anything the review missed. Each item:
`N. [blocking|minor] <finding> -> <what changed: kept / dropped / re-severitized / added, and why>`

Keep it tight. No extra prose, no severity catalog.
