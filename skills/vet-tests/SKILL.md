---
name: vet-tests
description: Review and fix testing theater after writing tests, when tests look padded, or when asked to vet, trim, or tighten tests.
---

Critically review tests for the current change.

**Scope:** Use the requested scope; otherwise, the first applicable: tests written
in this conversation, uncommitted tests (staged, unstaged, and new), then the branch
diff against its known base. Flag incidentally touched pre-existing tests instead
of deleting them.

1. **What specific bug would this test catch?** Read the production code and
   requirements. Identify the assertion that would fail. Missing context warrants
   uncertainty, not deletion.
2. **Does it test our decisions?** Look for assertions that only confirm mocks,
   framework behavior, fixtures, or that code ran; expectations copied from the
   implementation; and mocks replacing the unit under test. These are clues, not
   automatic deletion rules. Keep configuration and integration tests protecting
   our requirements, such as a route requiring authentication.
3. **Does it earn its place?** Remove useless tests, consolidate genuine duplicates,
   and strengthen weak assertions. Preserve unique coverage. Add tests only for
   concrete gaps in the current change, never speculative cases or test counts.

Apply focused test edits when allowed; otherwise propose them. No production
changes or cosmetic cleanup. Report production bugs and preserve tests exposing
them. Never weaken checks or skip tests merely to get green results.

Run affected tests before and after edits when possible, plus required repository
checks. Confirm they executed. Briefly report test locations, changes and reasons,
commands and results, and verification limits. If the tests hold up, say so.
