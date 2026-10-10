# TraceNote — Interview brief

## One-line pitch
TraceNote is an evidence-first research-note workflow for student project teams. It creates a useful draft, but its differentiator is that it keeps source excerpts attached to claims and stops a potentially contradictory statistic from being quietly copied into a presentation.

## User and problem
- **User:** a student project team, club committee, or small community research group.
- **Pain point:** notes arrive from surveys, interviews, shared docs and chat; summarising them is slow, and a fluent but incorrect statistic can slip into a report.
- **Outcome:** a concise brief containing key observations, caveats, proposed next steps and an evidence ledger.

## Workflow
1. Input approved notes and a draft paragraph.
2. Split source lines into stable IDs.
3. Inspect numerical claims and compare draft values with the supplied notes.
4. Preserve conflicting values and flag the draft for review rather than silently choosing.
5. Present a source ledger, possible action items and a reviewer handoff.
6. Export a Markdown review note; a human owns the final decision.

## Why it is not a generic summariser
Traceability and uncertainty handling are the core features. The product should make it easy to ask “where did this statement come from?” Contradiction is treated as a workflow state, not just another sentence in a summary.

## Evaluation plan
These are proposed targets, not measured performance:
- Evidence coverage: proportion of material claims with supporting evidence; target ≥90% on a labelled set.
- Conflict recall: proportion of seeded same-topic numerical conflicts correctly flagged; target 100% on the known test set.
- Human usefulness: reviewer score for clarity/actionability; target median ≥4/5.
- Unsafe release rate: high-risk cases incorrectly marked ready to share; target 0.
- Time saved: compare median time for a reviewed brief against the team's manual baseline during a pilot.

## Example evaluation cases
| Case | Expected behaviour | Pass condition |
|---|---|---|
| Draft says 72% want reminders; raw note says 43% | Preserve both values and flag conflict | Review state remains active |
| Notes mention convenience sampling | Keep the limitation | No population-wide conclusion |
| Input is too vague | Ask for more context | No fabricated findings |
| Input includes an email | Mask it in generated/exported draft | Unmasked address absent from export |
| Explicit next step exists | Extract a candidate action item | Human can confirm it |

## Failure handling
- Conflicting claims: never average, pick, or silently rewrite; attach both excerpts and hold for review.
- Weak evidence: state that evidence is insufficient.
- Parsing/model failure: show an error and preserve original input.
- Sensitive or high-stakes content: stop automatic sharing and route to an authorised reviewer.
- False negatives are possible; no warning is not proof of correctness.

## Privacy boundary
- **Current prototype:** runs in the browser, makes no API call and does not save input persistently. The export applies simple email/phone-like pattern masking to the draft.
- **Before production:** obtain permission for data sources; minimise collection; restrict access; define retention/deletion; approve model provider and data settings; test privacy leakage.
- **Out of scope:** identifying students, making disciplinary decisions, mental-health advice, or autonomously publishing results.

## Honest prototype boundary
The current HTML uses deterministic browser-side heuristics, not a live LLM, semantic verification, or external fact-checking. It demonstrates interaction, source IDs, numerical review states, export, and small rule checks. A production version would connect a model behind a strict schema and validate each evidence reference before display.

## 60–90 second interview pitch
“I designed TraceNote for student teams who need to turn survey and interview notes into a brief. A normal summariser can sound confident while copying a wrong number, so I made evidence traceability the core feature: claims keep source-line IDs, and draft-versus-raw statistics trigger a review hold. The prototype is deliberately browser-only and uses simple rules, so I’m not claiming it has real LLM intelligence or measured benchmark performance. My next step would be to connect a model behind a strict output schema, evaluate it on labelled conflict and privacy cases, and keep a human reviewer responsible for approval.”

## Suggested live demo
1. Show the sample where the draft says 72% but the source note says 43%.
2. Click **Check evidence** and explain why the tool does not decide which figure is correct.
3. Point to the evidence ledger and stable source IDs.
4. Run the built-in checks.
5. Export a Markdown handoff note.
