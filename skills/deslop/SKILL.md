---
name: deslop
description: Cut over-explained and AI-sounding prose from anything I just wrote - comments, docs, PR bodies, Slack drafts - apply the cuts, then report what went and what stayed
disable-model-invocation: true
---

Cut the AI-sounding prose out of what was just written. Edit local files directly. For
anything that leaves the machine, propose the rewrite and wait.

**Scope**, in order: prose written this session, then the current change, then the
branch's open PR. Stay on files related to the current ticket, not the whole diff.

**The cut test. Delete is the default, not rewrite.** If it can be figured out by
reading the code, delete it. The comment goes, the doc section goes, the file goes.
Rewriting an inferable comment into a tighter inferable comment is the failure this
exists to prevent. Only a non-obvious WHY or a hidden constraint survives, and
shortening comes after, in the trim pass below.

For prose generally: does this carry information a reader cannot get from the thing it
describes, or is it performing?

**Trim survivors clause by clause.** Passing the cut test earns a sentence its
place, not its length. Cut:

- Restatement: two sentences carrying one fact keep the more concrete one
- Detail the artifact already shows, like a parameter's valid values
- Steps the remaining steps imply: "open a PR and merge to main" is "merge to main"
- Clauses that are true but off-point where they sit

**Mechanical tells.** Check every time, before reading for anything else.

- Em dashes, anywhere
- "lands" and "lands in" - use "shows up in" or "goes to"
- Walls of text. Break them up.
- `--` as a separator becomes `-`
- Jira keys like `ABC-1234` as a comment prefix. State the why without the key. A key
  doing real work stays, like a TODO naming the ticket that tracks its removal. When
  unsure, flag instead of cutting.
- "kill switch" in audience-facing text - use "on/off toggle"

**Judgment tells.** Read for these.

- Punchy sentence fragments for rhetorical effect
- Victory-lap framing that explains why a result is impressive
- Closers that tie a bow on the thesis. End on the fact.
- Escalating three-clause builds
- Instructional voice where past-tense first person fits: "I used a scratch thread",
  not "Use a scratch thread"
- Stock openers and filler: "Good point", "turns out", "just to clarify",
  "essentially". No bullet recap, no closing summary.
- Step-by-step privilege-escalation chains. Keep the decision and the control.

**Keep the courtesies.** In outbound messages, scope-lock the content but leave the
professional norms: OOO disclosure, greetings, acknowledgments. Cut the padding around
a courtesy, never the courtesy.

**Syntax.** Multi-line comments collapse to one `/* */` block, never stacked `//`. In
`#`-comment languages the fix is fewer and shorter lines.

**Markdown.** Cut the preamble when the first real section already orients, and cut
the closing summary.

**Nothing to cut is a valid result.** Say so in one line and stop.

**Hands off:** no logic changes, no test changes, no new comments, no rewording that
shifts meaning, nothing outside scope. In plan mode, say edits are blocked and stop
rather than degrading into a suggestion list.

Do not run `gh pr edit`, `gh pr comment`, `gh api` with a write method,
`updateConfluencePage`, `editJiraIssue`, `slack_send_message`, or
`slack_update_canvas` during a pass. Approval is per-action and per-surface, and does
not carry to the next invocation. Local file edits need no gate.

Jira comments and already-sent Slack messages have no edit tool at all, so hand those
over as text to paste.

Then report exactly this, and nothing extra:

**Cut** - `<file>:<line> - "<first few words>" -> <one-word reason>`

**Kept** - only the genuinely borderline ones, same format plus why it survived.

**Proposed** - only if there was outbound text. Each rewrite in full, tagged with how
to apply it. Do not apply any of them in this turn.

Keep the report tight. No preamble, no summary.
