# Skills

Agent skills for coding agents (Claude Code, Cursor, Codex, and others), sourced from real development workflows.

## Setup

Install with the [skills.sh](https://skills.sh) installer:

```
npx skills@latest add michalochman/skills
```

Pick the skills and agents you want when prompted. The installer copies skills into your project so you can customize them.

### As a Claude Code plugin

Inside Claude Code:

```
/plugin marketplace add michalochman/skills
/plugin install skills@michalochman-skills
```

From the shell:

```
claude plugin marketplace add michalochman/skills
claude plugin install skills@michalochman-skills
```

The plugin is read-only and auto-updates on each push.

## Skills

- **[handoff](skills/handoff/SKILL.md)** — Distills the current session's state (goal, progress, next steps, key files, gotchas) into a compact block for whoever continues the work: a clean-context subagent when results should come back, or a paste-ready block for a fresh session. Invoke with `/handoff`, or it triggers on any request to hand off, delegate, or offload work ("give the next agent everything it needs").

- **[speculating](skills/speculating/SKILL.md)** — Marks your prompt as a hypothesis, not a fact. The agent extracts each claim, verifies it against real evidence (reads code, runs commands, checks docs), and opens with an explicit verdict — pushing back plainly when the claim is wrong. Cancels the default bias toward agreeing with your framing. Invoke with `/speculating`, or it triggers automatically on hunches ("I suspect", "my theory is", "I might be wrong but").

## License

MIT
