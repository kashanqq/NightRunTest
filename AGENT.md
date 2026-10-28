# AGENT.md

Instructions for AI coding agents (Claude Code, Antigravity, ...) working in this repository.
Read this file first. Before editing files in a folder, also read that folder's AGENT.md
and the AGENT.md of its parent folders (if they exist).

## Project
`gamecore`: a pure-Python (stdlib only) 2D game core with ECS, tilemap, dungeon generator, pathfinding, collisions, save/load and a console simulator; used as the test project for the nightrun orchestrator. Details live in docs/CONTEXT.md.

## How to work here
- Work on ONE task at a time from PLAN.md. Keep commits small and focused.
- Build / run / test commands live in docs/CONTEXT.md. Keep them up to date.
- Keep docs/ current: after each task add an entry to docs/PROGRESS.md, and update
  docs/CONTEXT.md / docs/DECISIONS.md when structure, commands or decisions change.
- Stay inside the task scope. Do not reformat or refactor unrelated code.
- Never commit secrets (.env files, keys, tokens).

## Related files
- docs/CONTEXT.md, docs/PROGRESS.md, docs/DECISIONS.md
- docs/agents/*.md (issue tracker, triage labels, domain docs) - only if present
- CLAUDE.md / AGENTS.md - only if present (may hold an "Agent skills" section)

## Project-specific rules
<!-- Durable rules: code style, forbidden patterns, tooling quirks. Agents may append short rules here. -->
