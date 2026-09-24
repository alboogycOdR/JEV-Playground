# Recurring architecture

Almost every hot repo in the first week follows the same split. This is also what madewithjev.com named **Jev Engineering**.

1. **Deterministic perception** builds a candidate set  
   DOM nodes, accessibility tree, tool-call traces, table rows, CV fields, legal placements, model tiers.
2. **Jev chooses / scores / gates** over that set in one parallel call.
3. **Your code executes** the chosen action. An LLM is only invoked when free text is genuinely required.

That is why the latency and cost claims survive contact with demos: the expensive model is no longer in the inner loop.

## Product shapes this week

| Shape | What Jev does | Examples |
| --- | --- | --- |
| Agent inner loop | next click / key / desktop / mobile action | Ultrafast, typesafe-computer-use, mobile-jev, minecraft-agent, jev-desktop |
| Context engineering | keep / drop / truncate / when-to-compact / which skill | fast-jev-compaction, hermes-jev-skills, yoshi, compact-adviser, codex-context-diet |
| Routing / firewalls | ticket lane, tool-call pre-check, model router | jev-router, jev-axi, jev-guard, Foreman |
| Batch scoring | CVs, search rerank, news cold-start, issue triage | jev-search, typesafe-jev CV screener, DocJev |
| Markets | per-block or per-tick binary decision | jev-trader and forks — see `finance-cluster.md` |

## Design habits that keep showing up

- Rebuild the option set every step (Ultrafast’s “new action space every step”)
- Batch many questions on one state (ten questions ≈ cost of one)
- Threshold on confidence; escalate to human or LLM when low
- Deterministic rules first, Jev only on the gray zone
- Verify the side effect in code before the next call
- Keep survivors **verbatim** when compacting (controversial — Theo’s pushback: compaction is reconstruction, not filtering)

## Claude Code vs Codex mapping onto these shapes

| Shape | Claude-first examples | Codex-first examples | Both |
| --- | --- | --- | --- |
| Context janitor | fast-jev-compaction, jev-pruner, compact-adviser | codex-context-diet, fast-dev-compaction | yoshi |
| Model / skill route | gargpratyush/jev-router, jcm-router | Jev-Auto-Router | hermes-jev-skills |
| Tool gate | jev-axi, jev-belay | same hooks.json family | jev-guard, jev-use |
| Browser / computer use | public-browser | jev-browser-use, jev-desktop | hermes-jev-skills |
| Factory / review | | Foreman above Codex workers | jev-review |

## Caveats (from the report, keep them)

- Jev is not open source
- Most star counts are launch-week spikes
- Typed output is not correct output
- Vendor speed/cost multiples do not apply to writing or long reasoning
