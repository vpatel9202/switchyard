# Switchyard

> Sorts every AI conversation onto the right track.

A rail switchyard takes cars arriving from everywhere and routes each one onto the right track. Switchyard does the same for AI conversations. You chat wherever you like — Claude, ChatGPT, Grok, Claude Code, Codex, on any machine — and Switchyard figures out which project each conversation belongs to, flags when a conversation drifts into a different one, and keeps a single human-readable home for every project up to date.

**Status:** early design. Nothing here is usable yet.

## The problem

AI work is scattered across chat apps, CLI agents, machines, and whatever directory a session happened to start in. Each surface keeps its own history and knows nothing about the others. You end up hunting for where something was discussed, re-explaining context, and carrying the organization in your head.

Shared agent memory helps with *knowledge* (what's true, what was decided). It doesn't solve *work state* (where each project stands) or *location* (which conversation holds the thread on X). Switchyard targets those.

## Goals

- **File automatically.** Conversations are routed to the right project based on what was actually discussed, not where they started.
- **Flag drift in the moment.** When a conversation wanders into a different project or a separate idea, say so and offer a clean handoff to a new session.
- **One home per project.** Each project has a canonical, human-readable, human-editable page (plain Markdown, Obsidian-compatible) that agents keep current: state, decisions and why, next steps, and links back to the conversations behind them.
- **Answer "where are we on X?"** from one place, for any agent or person.

## Design principles

- **No discipline tax.** If it depends on the user remembering to file, distill, or start in the right folder, it has failed. The user's job is yes/no confirmations and occasional edits.
- **Fewer systems, not more.** Anything added should replace something.
- **Work with the apps people already use.** Bridge into vendor chat apps (MCP connectors, standing instructions, exports) rather than replacing them.
- **Plain files as the source of truth.** Indexes and caches are derived and rebuildable.
- **Private by default.** Sensitive content never leaves the boundary it already lives in. No secrets in any index or memory.
- **No forks.** Integrate through hooks, plugins, skills, and config — never by patching upstream tools.

## Likely building blocks

Under evaluation, not commitments:

- **Agent hooks** (Claude Code, Codex) at session start, prompt submit, and session end.
- **Typed classification** via [TypeSafe](https://typesafe.ai) Jev for fast, cheap judgments: which project, did this drift, is this worth filing.
- **Markdown knowledge base with semantic search**, e.g. [Basic Memory](https://github.com/basicmachines-co/basic-memory) or [qmd](https://github.com/tobi/qmd).
- **Cross-agent session indexing**, e.g. [CASS](https://github.com/Dicklesworthstone/coding_agent_session_search).

## License

[MIT](LICENSE)
