---
name: external-docs
description: Write, review, or edit a document that must stand alone for a reader outside the team, who cannot see your internal documentation. Use it even for one short answer, because most of the value is in what the rules remove.
---

# external-docs

The document stands alone. A reader outside the team reaches a complete understanding of
the subject from this text and the sources it cites, and from nothing else.

It fails two ways:

- **Gap** — the text leans on something the reader cannot see: an internal document, a
  foreign specification, a test name, an earlier decision.
- **Noise** — the text carries detail the subject does not need. Each irrelevant fact
  opens a question the document then has to close.

## Close the gaps

- Cite a source for every claim, and the line when the line is load-bearing. Cite the
  file, not an internal identifier: describe what a test proves rather than quoting its
  name, because names get renamed and the document does not follow. Verify each citation
  against the source, and re-anchor it by search after any source edit, because line
  numbers move.
- State the behavior directly. "This matches the semantics of `<other system>`" sends the
  reader to a second specification to check your first claim.
- Never write "as agreed earlier". If you cannot cite where a decision was made, ask.
- One source of truth across a document set. A shared definition lives in one document.
  The rest link to it. After a move or a merge, fix every cross-document reference by
  search, because a reference that no longer resolves is a gap.
- Use one name for each concept across the document set. A reader outside the team cannot
  tell that two names mean one thing.

## Cut the noise

- Name nothing the reader cannot open. A name discloses that something exists while
  leaving the reader unable to inspect it, and excluding a component by name discloses it
  just as surely as describing it. Name the role instead: "version registry", not the
  product name of your registry.
- Say little about what you do not own, and little about what drifts: infrastructure,
  release process, monitoring, counts, durations. Those go stale, in writing, in the
  reader's copy.
- Claim only what you can demonstrate, and attach the claim to the thing you deliver, not
  to a by-product of making it. "The services run in a private network" is a fact you can
  show. "Behind a firewall" names a control you now have to evidence.
- Delete reassurance. "This contains no server source" reassures the writer. A reader
  takes a denial as a hint that somebody worried.
- Positive first, and at most one load-bearing negative per topic. The anti-pattern reads
  "The plane flies. It does not walk, and it does not swim." Keep the negative that
  answers a question the reader must ask. Drop the denials around it.
- Delete a disclaimer, do not hedge it. The fact either belongs in the document or goes.

Worked example. A submission carried an accurate section on transport-security posture.
No requirement asked for it. It opened questions the document could not close, so it was
deleted. Being accurate does not earn a place.

## Where the rules stop

Text that must match an external reality stays byte-exact: verbatim quotes, literal
commands and their output, file paths, dependency specifiers, and the real name of an
external interface.
