# Integrating Jev with Claude Code and Codex

Goal of this file: a map of *how* people actually wire Jev into the two harnesses, not a single blessed recipe. Repos we restore will be linked here as they land.

There are four distinct jobs people give Jev in a coding agent. Mixing them in your head is the main source of confusion.

## Four jobs

1. **Teach the agent to write Jev calls**
   Official skill: `typesafe-ai/skills`
   Claude Code:
   ```
   claude plugin marketplace add typesafe-ai/skills
   claude plugin install typesafe@typesafe-ai
   ```
   Codex / others:
   ```
   npx skills add typesafe-ai/skills --skill typesafe-ai
   ```
   This does *not* put Jev on every tool call. It teaches the LLM how to design Choice / Score / Noul questions and call the API from generated code.

   Closest “batteries included” pack for both hosts: `kerpopule/hermes-jev-skills` — nine `SKILL.md` files (model routing, memory, compaction, skill select, computer use, browser use). `install.py` detects Hermes, Claude Code, and Codex. Author later measured some claims worse than advertised (v0.18.0).

2. **Gate every tool call (hooks)**
   PreToolUse / PreCompact style.
   Jev scores destructiveness, relevance, or “should this run?” and returns allow / ask / deny.
   Examples in the wild:
   - `Gilbert09/jev-cli` — same binary for Claude Code plugin *and* Codex `hooks.json` (Codex’s hook engine is Claude-compatible, module name `ClaudeHooksEngine`). Verdict spelling differs: Codex has no `ask`, so `ask` becomes `deny`; bare `allow` is rejected unless paired with `updatedInput`.
   - `tamaratran/fast-jev-compaction` — Claude Code compaction: score each tool call, drop stale ones, keep survivors verbatim. Launch-week ~5.8k★.
   - `fatelei/jev-compact` — Codex analogue of the same idea (PreCompact + re-inject verbatim outputs Jev marked as still required).
   - `konstantinosbotonakis/codex-context-diet` — Codex plugin that trims bulky tool results.
   - `kunchenguid/compact-adviser` — tells Claude/Pi *when* a session is safe to compact.

3. **Route the next step / model / tool (MCP or proxy)**
   Jev does not write arguments. The host prepares candidates; Jev picks.
   Examples:
   - `burnigtm/jev-mcp` — local stdio MCP: `jev_step`, `jev_coding_loop`, `jev_tool_route`, `jev_review`, `jev_verify`, `jev_gate`, …
   - AutoJev hosted MCP at `https://autojev.ai/mcp`
   - `gargpratyush/jev-router` — `jev-claude` / `jev-codex` launchers that pick Fast / Balanced / Strong / Long tiers per user turn
   - `ansidium/jev-codex-bridge` — Codex Desktop/CLI model + effort picker
   - `vinilana/jev-gateway` — local gateway: when the agent is about to choose a tool, Jev chooses; generation still goes to the usual model
   - `shitianfang/jev-use` — hand steps that need no text to Jev; escalate typed low-confidence cases back to the LLM

4. **Review / label / audit**
   Diff audits, completion checks, batch labelling.
   Examples: `Kushwho/jev-codes`, `integrate-your-mind/jev-codex-plugin`, `teempai/jev-in-codex`.

## Claude Code vs Codex differences that matter

| Concern | Claude Code | Codex |
| ------- | ----------- | ----- |
| Skill install | plugin marketplace + `/plugin install` | `npx skills add` or Codex plugin marketplace |
| Hooks | first-class PreToolUse / PreCompact plugins | compatible hook JSON; must `/hooks` and **trust** or they are silently skipped |
| Ask the user | `ask` is valid | no prompt path; `ask` typically mapped to `deny` |
| Allow | `allow` | often must be silence / `updatedInput`, not a bare allow |
| Model routing | `/model` → a “Jev Router” synthetic model | commentary line or a registered provider / bridge |
| Compaction | plugin can replace the summary | hook around built-in compact, then re-inject |

## Env keys you will see

- `TYPESAFE_API_KEY` — direct TypeSafe
- `AI_GATEWAY_API_KEY` — Vercel
- `OPENROUTER_API_KEY` — many community plugins
- `JEV_BACKEND=mock` — dry run in `jev-use` and similar

Never commit keys. Per-repo notes should say which env that repo expects.

## Catalog pointer

`repos/awesome-jev/` and `notes/awesome-jev.md` are the field guide. Live cards: `notes/madewithjev.md` (https://madewithjev.com/github-repos). Claude/Codex-relevant entries cluster in:

- `categories/infra-sdks-integrations.md`
- `categories/verification-guardrails.md`
- `categories/agent-decisions.md`
- `categories/classification-routing.md`

## What we will extract from each restored repo

For every clone:

- which of the four jobs it implements
- Claude, Codex, both, or neither
- hook vs MCP vs proxy vs skill
- question pack (Choice / Score / Noul names)
- where the TypeSafe call is made (file + function)
- what happens on low confidence
