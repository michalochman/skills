---
name: speculating
description: Marks the user's prompt as speculation — a hypothesis that may be completely wrong, never to be treated as established truth. Use whenever the user invokes /speculating, and also when they frame a claim as a hunch ("I suspect", "my theory is", "I might be wrong but", "is it possible that", "sanity-check this").
---

# Speculating

The text passed to this skill is a **hypothesis, not a fact**. The user has pre-declared low confidence, which removes any social cost to disagreeing — confirming a wrong hypothesis is a worse failure than bluntly refuting a right-sounding one.

## What to do

1. **Extract the claim(s).** Speculation often bundles several assertions. Identify each one that can be independently true or false.
2. **Verify before responding.** Check each claim against real evidence: read the relevant code, run commands, consult docs. Do not evaluate from plausibility alone — a claim that "sounds right" is exactly the kind this skill exists to catch. Don't ask the user to confirm their own hypothesis.
3. **Judge each claim honestly**, including the uncomfortable outcomes:
   - The claim is wrong → say so directly and explain what's actually true.
   - The claim is right → confirm it, with evidence. Do not manufacture disagreement to seem rigorous; contrarianism is the same failure as sycophancy, mirrored.
   - The claim can't be verified with available evidence → say "unverified" and what would settle it. Never round "couldn't check" up to "probably right."
4. **Answer the underlying need.** After the verdict, address what the user was actually trying to figure out. A refuted hypothesis usually implies a real question that still deserves an answer.

## Response format

Open with the verdict, bolded, before anything else. The verdict line must restate the claim it judges in one clause — a bare adjective is ambiguous, especially when the speculation itself was hedged ("I might be wrong but..." — does "correct" mean the theory is correct, or that they were right to doubt it?):

```
**Verdict: wrong — the read worker does backfill KV on a D1 miss.**
**Verdict: correct — the cookie spans subdomains because of the parent-domain Domain attribute.**
**Verdict: partially right — the batching claim holds, the slimming claim doesn't.**
**Verdict: unverified — nothing in the repo settles this.**
```

Then:

- **Evidence** — for each sub-claim: what you checked and what you found. Cite specifics: code locations, command output, doc section. An unsupported verdict is just a second opinion. Cite code as `path/from/repo/root.ext:12-40`, never bare line numbers.
- **What actually happens** — when the verdict isn't "correct": the real behavior, stated as directly as the user stated their guess.

Keep the verdict honest at the sub-claim level. "Partially right" must name which part is right and which is wrong — never use it as a diplomatic blur over "mostly wrong."
