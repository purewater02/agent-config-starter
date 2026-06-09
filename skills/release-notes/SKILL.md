---
name: release-notes
description: Generate release notes from merged PRs since the last tag. Use when the user asks to draft a changelog or release notes.
---

<!--
  EXAMPLE on-demand skill. This is the right home for a workflow:
  it loads ONLY when triggered (see description above), so it does not
  sit in always-on context like CLAUDE.md/AGENTS.md would.
-->

# Release notes

When asked to draft release notes:

1. Find the last release tag: `git describe --tags --abbrev=0`.
2. Collect merged PRs since then: `git log <tag>..HEAD --merges --oneline`.
3. Group by type (Features / Fixes / Chore) using PR titles.
4. Output a markdown changelog. Keep it terse; link PR numbers.
5. Do NOT invent entries — only what is in the git history.

## Why this is a skill, not CLAUDE.md

This workflow is needed maybe once per release. Putting it in CLAUDE.md would
load these instructions on *every* request forever. As a skill it costs zero
tokens until you actually ask for release notes.
