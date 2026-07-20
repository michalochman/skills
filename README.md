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

- **speculating** — Marks your prompt as a hypothesis, not a fact. The agent extracts each claim, verifies it against real evidence (reads code, runs commands, checks docs), and opens with an explicit verdict — pushing back plainly when the claim is wrong. Cancels the default bias toward agreeing with your framing. Invoke with `/speculating`, or it triggers automatically on hunches ("I suspect", "my theory is", "I might be wrong but").

## License

MIT
