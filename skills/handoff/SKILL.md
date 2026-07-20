---
name: handoff
description: >-
  Use BEFORE spawning a subagent, delegating to another agent, or moving work
  into a new, fresh, or separate session. Trigger on ANY request to hand off,
  delegate, spin off, offload, or transfer the current task or its remaining
  work — validation in a side agent, next phase in a fresh session, avoiding
  compaction, "give the next agent everything it needs", "write up where we
  are" — even when the word "handoff" never appears. Do NOT use for write-ups
  that stay in this session (PR descriptions, standup notes, progress files,
  READMEs) or for simply running commands in the background here.
argument-hint: "Focus of the next session (optional)"
---

# Handoff

A handoff moves the context you've built to whoever continues the work — as a
compact block, not a transcript.

## Pick the mechanism

Two things can receive the handoff. Choose from what the user is doing, not what
they literally said:

**Spawn a subagent** (via the Agent tool) when the result needs to come *back*
to this session. Validation, a spike, "is X actually true", answering a
bounded question — anything where the user said "I'll come back to this one" or
"check this and tell me". Pass the block as the subagent's prompt, prepended
with one line like "You're picking up a handoff. Execute the Next section and
report back findings + any blockers." Relay its result when it returns; this
session stays alive and uncompacted. Use `subagent_type: "general-purpose"`,
never `"fork"` — a fork inherits this session's context, defeating the offload.
(Other harnesses: any clean-context delegation tool.)

**Emit a paste-ready block** when the work is moving *forward* and won't return
to this session. Finished a phase, starting the next; or the context is big and
the user wants to continue in a fresh session they'll drive themselves. Output
the block as a single fenced code block — one clean copy, not buried in prose —
followed by one line: "Open a fresh session and paste this."

**Default is the paste block.** A bare `/handoff` with no other signal means the
user wants the handoff document — emit the block. Only choose the subagent path
on a positive come-back signal like those above. If signals genuinely conflict,
ask one short question: "Come back here after, or moving on?" Come-back →
subagent. Moving on → paste block. Both paths use the **same handoff block** —
only the recipient differs.

## Gather the state

Before writing, verify anything you're fuzzy on — read the files, run
`git diff`. A confident handoff built on stale memory is worse than none.

Keep it to what the *next* agent needs to act. Resist recapping the whole
journey; the dead ends you already ruled out are noise unless they'll be
re-tried. Don't restate what another artifact already captures — a spec, plan,
ADR, issue, commit message, or diff gets referenced by path or URL instead.

If the user passed arguments to the skill, they describe what the next session
will focus on — shape the block around that focus.

## Response format

The block is a deliberate distillation, not a transcript dump — exactly what
the next agent needs to start productive on its first turn, nothing more. Use
this structure; if a section is empty, drop it rather than padding it. Never
include secrets (API keys, passwords, PII); the block leaves this session.

```
# Handoff: <one-line task title>

## Goal & phase
<What we're ultimately doing, and where we are in it. If multi-phase, name the
phase just finished and the phase to start. One or two sentences.>

## Done
<What's complete and verified. Bullets. Include what was decided and *why* when
the reasoning isn't obvious from the code — that's the part the next agent can't
recover on its own. Only list what you're sure passed; anything uncertain goes
to Verify & gotchas instead — an overconfident handoff is worse than a short
one.>

## Next
<What the receiving agent should do first, then next. Concrete and ordered. If
this is a validation branch, state the exact question to answer and what a good
answer looks like.>

## Key files & pointers
<file:line references to the code that matters. Entry points, the function being
changed, the config that controls behavior. Point, don't paste.>

## Verify & gotchas
<How to check the work is right (the command to run, what output means success).
Traps, non-obvious constraints, assumptions already baked in. Highest-leverage
section and the one most often skipped.>

## Open questions
<Unresolved decisions the next agent may hit. Omit if none.>

## Suggested skills
<Skills the receiving agent should invoke, and for what. Omit if none.>
```
