---
name: deslop
description: >
  Cut over-explained and AI-sounding prose from drafts, comments, docs, PR bodies,
  and Slack or Jira text before finalizing them. Use when drafting or editing
  these texts. Apply local edits when allowed; in plan or review mode, or for
  outbound text, propose changes without applying them.
---

Cut the AI-sounding prose out of what was just written. Apply local edits when
allowed. In plan or review mode, or for outbound text, propose changes without
applying them.

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
- Do not use the word flying blind or blind to describe something
- AI vocabulary: crucially, delve, interplay, pivotal, tapestry, testament, seamless,
  robust, leverage, load-bearing, load bearing - plain equivalents
- Inflated copulas: "serves as", "stands as", "boasts", "features" - "is"/"has"
- Verbose phrases and filler words: "in order to" - "to", "due to the fact that" -
  "because", "utilize" - "use"
- Curly quotes - straight quotes
- Title Case Headings - sentence case, unless the surrounding document already
  established Title Case as its own heading convention (an existing README, Confluence
  page, or PR template with consistent Title Case headings throughout); match what's
  there instead of introducing a mismatched style
- Bold scattered inside sentences for emphasis (structural bold, meaning a lead phrase,
  a label, or a key figure, stays)
- Repeated or performative colon connectors, not ordinary explanatory colons or colons
  that are just syntax (URLs, timestamps, labels, code)

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
- Hollow -ing phrases: "highlighting", "ensuring", "showcasing" - delete or state the
  actual mechanism
- Puffery: "pivotal moment", "evolving landscape" - cut, state facts
- "Not just X, but Y" - state the point directly
- Synonym cycling: same thing called three different names - pick one, repeat it
- Over-hedging: "could potentially possibly" - "may"
- Passive voice where the actor is knowable: "queries are validated" - "the compiler
  validates queries"
- Weak verb + adverb: "runs quickly" - cut the vague adverb and state what actually
  makes it fast, or cite a number. ("is fast" alone just trades one unsupported claim
  for another.)
- Feelings-over-mechanism: describe the actual function or cut
- Abstract metaphor nouns: substrate, wedge, vector, nexus, endgame, flywheel -
  concrete terms. Exclude "harness" from this list, since it's a legitimate term in
  AI agent contexts (agent harness), flagging it would produce false positives.
- Header-restating lists: `**Performance:** Performance improved...` - convert to
  prose or fix the lead

**Keep the courtesies.** In outbound messages, scope-lock the content but leave the
professional norms: OOO disclosure, greetings, acknowledgments. Cut the padding around
a courtesy, never the courtesy.

**Keep the substance.** Data tables and enumerable lists are data presentation, not
slop. Short sentences are not slop, only telegraphic fragments or symbol-chain
formulas are. Established domain terms, identifiers, quoted text, and this repo's own
terminology are preserved even when they appear on the AI-vocabulary or
abstract-metaphor-noun lists above, those lists flag candidates for a second look, not
an automatic find-and-replace.

**Syntax.** Multi-line comments collapse to one `/* */` block, never stacked `//`. In
`#`-comment languages the fix is fewer and shorter lines.

**Markdown.** Cut the preamble when the first real section already orients, and cut
the closing summary.

**Nothing to cut is a valid result.** Say so in one line and stop.

**Hands off:** no logic changes, no test changes, no new comments, no rewording that
shifts meaning, nothing outside scope. In plan or review mode, return proposed
cuts or rewrites without editing files.

Do not run `gh pr edit`, `gh pr comment`, `gh api` with a write method,
`updateConfluencePage`, `editJiraIssue`, `slack_send_message`, or
`slack_update_canvas` during a pass. Approval is per-action and per-surface, and does
not carry to the next invocation. Local file edits need no gate.

For Jira comments and already-sent Slack messages, provide proposed text to paste.
Do not edit them during this pass.

Then report exactly this, and nothing extra:

**Cut** - only edits actually applied: `<file>:<line> - "<first few words>" -> <one-word reason>`

**Kept** - only the genuinely borderline ones, same format plus why it survived.

**Proposed** - outbound text or changes withheld in plan or review mode. Give each
proposed cut or rewrite with its location and how to apply it. Do not apply any of
them in this turn.

Keep the report tight. No preamble, no summary.
