# Context Budget — production discipline

Your agent gets dumber as context fills with stale instructions, unused config,
and tool output. This is **Context Rot**, and it's a discipline problem, not a
model problem. Treat your context window like a budget.

## Measure first

In Claude Code, run `/context` *before typing anything*. You'll see how much of
the window is already consumed by CLAUDE.md, AGENTS.md, loaded skills, and MCP
tool definitions. If you've spent 20-30%+ before your first prompt, you have a
budget problem.

## The rules

1. **Always-on vs on-demand.**
   - Always-on (CLAUDE.md / AGENTS.md): only what *every* task needs.
   - On-demand (skills): everything triggered. They cost 0 tokens until invoked.

2. **Kill dead weight.**
   - A skill or section that loads but never fires is pure waste.
   - Audit periodically: which skills actually triggered in your last N sessions?
     Delete the rest.

3. **One source of truth.**
   - Contradictions across CLAUDE.md / SOUL.md / scattered rules cause drift.
   - Centralize in AGENTS.md.

4. **English for always-loaded files.**
   - Always-on config is ~2-3x cheaper in English tokens. Save where it repeats.

5. **Watch the rot threshold.**
   - Quality degradation becomes measurable around 20-30 turns, accelerates past 40.
   - Long task? Compact (`/compact`) or split into subagents before you cross it.

## A 10-minute audit

- [ ] `/context` at session start — note the baseline %.
- [ ] List every skill; mark which actually fired this week. Delete unfired ones.
- [ ] Move any workflow out of CLAUDE.md into a skill.
- [ ] Translate always-loaded config to English.
- [ ] Re-run `/context` — confirm the baseline dropped.
