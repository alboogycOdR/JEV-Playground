# JEV Playground

Study notes on **Jev**, TypeSafe AI's System One decision model.
This repo is a map, not a runtime. It does not call the Jev API and it does not store keys.

Jev does not write prose. You send **state** plus typed **questions** (Choice / Score / Noul) and get schema-locked answers with probabilities in about 70–500 ms.

The working split across almost every public build:

> An LLM writes. Jev decides. Code acts.

## Read in this order

1. [research/what-is-jev.md](research/what-is-jev.md) — model, primitives, pricing, limits
2. [research/usage-patterns.md](research/usage-patterns.md) — the recurring architecture
3. [research/claude-and-codex.md](research/claude-and-codex.md) — how people wire Jev into Claude Code and Codex
4. [research/trending-github-repos.md](research/trending-github-repos.md) — launch-week usage repos (star snapshot 21 Sep 2026)
5. [research/open-replicas.md](research/open-replicas.md) — local `/systemone`-shaped stand-ins
6. [research/finance-cluster.md](research/finance-cluster.md) — trading loops; Jev judges, code trades
7. [research/catalogs.md](research/catalogs.md) — other indexes
8. [research/sources.md](research/sources.md) — where this snapshot came from

## Starter stack to clone next

Not in this repo. Clone these when you want code:

| Goal | Repo |
| --- | --- |
| See the inner loop | [browser-use/jev-ultrafast](https://github.com/browser-use/jev-ultrafast) |
| Claude Code compaction | [tamaratran/fast-jev-compaction](https://github.com/tamaratran/fast-jev-compaction) |
| Skills for Claude + Codex + Hermes | [kerpopule/hermes-jev-skills](https://github.com/kerpopule/hermes-jev-skills) |
| Jev as a typed Python function | [aaazzam/jev](https://github.com/aaazzam/jev) |
| Official agent skill | [typesafe-ai/skills](https://github.com/typesafe-ai/skills) |
| Finance loop | [jarrodwatts/jev-trader](https://github.com/jarrodwatts/jev-trader) |
| Shape without TypeSafe | [TianyuCodings/NanoJev](https://github.com/TianyuCodings/NanoJev), [jaredpalmer/kev](https://github.com/jaredpalmer/kev), [TheoLeeCJ/SemIf](https://github.com/TheoLeeCJ/SemIf) |

## Access (when you do call Jev)

- Direct: `POST https://api.typesafe.ai/v1/systemone`
- Model: `jev-latest` (pin `jev-1.13.0` if you tune thresholds)
- Also: Vercel AI Gateway `typesafe-ai/jev`, OpenRouter, Cloudflare `typesafe/jev`
- Env: `TYPESAFE_API_KEY` — never commit it

## Caveats

- Jev is hosted and closed-weight. Public repos consume the API or imitate the interface.
- Star counts in these notes are a 21 Sep 2026 snapshot.
- Typed output is not correct output. Fit confidence thresholds on your own labels.
- Vendor speed/cost multiples are for classify / route / score workflows, not writing.
