---
name: vet-plan
description: >
  Critically reviews a plan or proposal for correctness, problem fit, and
  over-engineering, validating every claim with tools rather than assuming.
  Use when an agent has produced a plan and wants it challenged before
  executing on it.
disable-model-invocation: true
---

# Vet Plan

A second pass over a plan before you act on it.

## Instructions

Critically review your current plan/proposal:

1. Is it correct - will it actually work? Validate every claim with tools
   (read the code, run checks). Do not assume.
2. Does it solve the stated problem, fully?
3. Is it over-engineered? We don't want that - flag anything that can be cut
   or simplified.

If you find problems, correct the plan and say what changed. If it holds up,
say why you're confident.

## Notes

Instructions only. No network access, no file writes, no credentials.
