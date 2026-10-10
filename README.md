# TraceNote — Evidence-first Research Workflow

TraceNote is a lightweight browser-based workflow for student teams and community groups that need to turn research notes into a reviewable brief. It prioritises evidence traceability and uncertainty handling over producing a polished summary that may hide conflicting information.

## Live demo
https://kkiaraleee.github.io/project1/

## Try it
1. Load the sample notes. The draft says **72%** preferred reminder emails, while the raw survey note says **43%**.
2. Click **Check evidence**.
3. Inspect the source IDs and numerical-claim audit.
4. Review the flagged figure instead of letting the tool choose one automatically.
5. Export a Markdown review note and run the built-in sanity checks.

## Workflow
1. **Input:** a team member pastes approved research notes and a draft paragraph.
2. **Prepare:** the notes are assigned stable source IDs.
3. **Check:** simple rules compare draft percentages with the supplied evidence.
4. **Structure:** the interface displays a digest, evidence ledger and possible action items.
5. **Handoff:** conflicts or weak evidence are flagged for a person to verify before sharing.

## Design principle
**Do not guess when the evidence disagrees.** A conflicting number can refer to a different group, period or measurement. TraceNote preserves the source figures and makes the uncertainty visible, leaving the decision to a human reviewer.

## Evaluation examples
- Draft says 72%, source note says 43% → flag the mismatch and preserve both figures.
- No source notes → ask for input instead of inventing findings.
- Email-like contact information → mask a common email pattern in the exported draft.
- Explicit next step → show a potential action item for human confirmation.

Potential metrics for a future pilot include evidence coverage, recall on seeded numerical conflicts, unsupported-claim rate, reviewer usefulness, privacy leakage and time saved. Any target thresholds should be treated as goals until they are measured.

## Privacy and limitations
The current static demo processes input in the browser. It does not call an LLM API or persistently store notes. It uses deterministic JavaScript rules, not semantic verification or external fact-checking; therefore, a clean result is not proof that a claim is true. Do not paste confidential, sensitive or identifying data into a public demo.

A production version would require permission for data sources, access control, retention and deletion rules, a validated model-output schema, evidence checks, and a human approval gate.

## Project files
- `index.html` — interactive browser prototype
- `TraceNote_Workflow.svg` — editable workflow diagram
- `MODEL_CONTRACT.md` — proposed model output structure and validation rules
- `EVALUATION_CASES.json` — example evaluation cases
- `.github/workflows/pages.yml` — GitHub Pages deployment workflow

## Deployment
GitHub Pages is published through the GitHub Actions workflow in `.github/workflows/pages.yml` when changes reach the `main` branch.
