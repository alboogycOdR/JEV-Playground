# Breakout usage repos

Star counts below are **as of 21 Sep 2026** from the attached report. They move fast. These are the repos people were actually wiring into a loop, not just listing.

## The inner-loop flagships

| # | Repo | Stars then | Forks then | Pattern |
| --- | --- | ---: | ---: | --- |
| 1 | [browser-use/jev-ultrafast](https://github.com/browser-use/jev-ultrafast) | ~14.7k | 901 | Jev as per-step policy; LLM only for `TYPE_TEXT`. Zürich→London Google Flights ~7.1s / ~$0.0039. Created 16 Sep; week’s #1 new repo. Dynamic indexed action space: Jev picks operation **and** DOM target in one request. |
| 2 | [tamaratran/fast-jev-compaction](https://github.com/tamaratran/fast-jev-compaction) | ~5.8k | 316 | Claude Code plugin. Keep/drop/truncate instead of summarising. Tool calls stay verbatim. Context-window janitor. |
| 3 | [jarrodwatts/jev-trader](https://github.com/jarrodwatts/jev-trader) | ~1.7–1.8k | 331 | One buy/sell per Monad block on Kuru MON-USDC. Author latency ~81 ms/block. High fork-to-star — people copy the loop. Template almost everyone else forked. |
| 4 | [awlevin/typesafe-computer-use](https://github.com/awlevin/typesafe-computer-use) | ~720 | | macOS: OCR + AX tree → Jev next action → click. Screenshots never go to a frontier model. ~$0.0002/step. Same architecture as Ultrafast, desktop. |
| 5 | [droidrun/mobile-jev](https://github.com/droidrun/mobile-jev) | ~310 | | Same idea on a real Android phone via Mobilerun. Uber SFO → Golden Gate ~21s / 9 actions. Live React studio + traces. |

## Coding-agent and review

| Repo | Stars then | Why it matters |
| --- | ---: | --- |
| [devagrawal09/jev-review](https://github.com/devagrawal09/jev-review) | ~457 | Staged code-review + local dashboard. Jev scores findings; it does not write a review essay. |
| [thruwire/foreman](https://github.com/thruwire/foreman) | ~454 | “Software factory foreman.” Jev dispatches what the next worker (often Codex) should do / whether work is done. |
| [kerpopule/hermes-jev-skills](https://github.com/kerpopule/hermes-jev-skills) | ~360–380 | Drop-in skills for **Hermes / Claude Code / Codex**: model routing, memory, compaction, skill selection, computer + browser use. Nine `SKILL.md` files. Installer detects all three hosts. Author later published that some headline claims measured *worse* than advertised (v0.18.0). |
| [aaazzam/jev](https://github.com/aaazzam/jev) | small (~9 live when rechecked) | `@jev.fn` turns a typed Python function (Pydantic return model) into a Jev call. “Jev as a function, not an API.” Architecturally clean, not a star leader. Needs Python 3.14. |

## Search / other usage sketches

- [superagents-lab/jev-search](https://github.com/superagents-lab/jev-search) (~359★) — Jev does source selection, query understanding, relevance ranking over Search1API
- [GiesN/typesafe-jev-workflow](https://github.com/GiesN/typesafe-jev-workflow) — LangGraph email routing (`invoice` vs `general`)
- [gtaras7/typesafe-jev](https://github.com/gtaras7/typesafe-jev) — CV screening; policy is editable and re-scores for free
- [realZachi/pg-jev](https://github.com/realZachi/pg-jev) — NL `WHERE` over Postgres rows
- [rmalde/minecraft-agent](https://github.com/rmalde/minecraft-agent) — agent inner loop in Minecraft

## How to read the stars

- Ultrafast and compaction look organic: forks + issues track stars
- A lot of 200–400★ repos are still prototypes
- Launch-week spikes are not a quality ranking
- `aaazzam/jev` is in the starter stack for *shape*, not popularity

## Starter stack the report recommended

1. **Ultrafast** — see the inner loop
2. **fast-jev-compaction** — see the coding-agent use
3. **aaazzam/jev** — see the typed-function wrapper
4. Then **NanoJev / kev / SemIf** if you want the *shape* without the TypeSafe bill (see `open-replicas.md`)
