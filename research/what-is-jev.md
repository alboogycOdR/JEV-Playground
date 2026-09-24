# What Jev is (research snapshot)

Source pack: attached Grok reports dated 21 Sep 2026, plus earlier session notes.
Stars in sibling files are snapshots, not live.

Jev is TypeSafe AI’s hosted **System One** model.

You send unstructured **state** plus typed **questions**. You get schema-locked answers with probabilities in roughly **70–500 ms**. No prose. No JSON-parsing lottery.

Launched ~15 Sep 2026. GitHub reaction in the first week was unusually fast; most hot repos were less than a week old at the time of the reports.

## Primitives

| Name | Question | Return |
| --- | --- | --- |
| Choice | pick one of the options you listed | winner + distribution + confidence |
| Score | grade on an ordered rubric | weighted score + level probabilities + confidence |
| Noul (aka Boolean in some lists) | is this claim true? | probability in `[0, 1]` |

## Pricing shape (vendor + ecosystem consensus)

- Input about **$0.042 / million tokens**
- Output free (the answer is a handful of numbers)
- Multiples like “200× faster / 400× cheaper” are measured on **System One-shaped workflows** (classify / route / score), not on writing or multi-step reasoning

## Hard limits

- Jev does not write text, code, or explanations
- Jev is **not open source**. Public repos consume the API or imitate the `/v1/systemone` interface
- Typed output ≠ correct output. Calibration is uneven across datasets. Treat confidence as a threshold you measure, not a guarantee
- Option space is bounded (Choice often capped at 255)

See also: `00-overview/JEV.md` (session primer) and `notes/madewithjev.md` (Jev Engineering wording).
