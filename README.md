# TraceNote — Evidence-first research workflow

**TraceNote** is an interview-ready prototype for student teams and community research groups. It turns research notes into a structured review brief while prioritising evidence traceability and human review over a polished but potentially unsupported summary.

## Live demo
After the GitHub Pages workflow finishes successfully, the demo should be available at:
https://kkiaraleee.github.io/project1/

## Try the demo
1. Open the sample notes: the draft says **72%** preferred reminder emails while the raw survey note says **43%**.
2. Click **Check evidence**. The prototype flags the mismatch instead of choosing a figure.
3. Inspect the source IDs in the evidence ledger.
4. Export a Markdown review handoff for a teammate.
5. Run the built-in sanity checks.

## User and workflow
- **User:** a student project team, club committee, or small community research group.
- **Inputs:** approved research notes and a draft paragraph.
- **Steps:** segment notes into source IDs → inspect numeric claims → flag unmatched figures → prepare digest and action items → human review → export handoff.
- **Human handoff:** contradictory figures, weak evidence, ambiguous claims, or sensitive information require review before external sharing.
- **Privacy boundary:** this static demo processes inputs in the browser; it does not call a model API or save notes persistently. Do not paste confidential or identifying information into a public demo.

## Evaluation examples
- Draft says 72%, raw note says 43% → must flag the mismatch and preserve both figures.
- No source notes → ask for input rather than inventing a result.
- Email address in text → mask the common email pattern in exported draft.
- Action phrase in a draft → show a potential next step for human confirmation.

These checks test simple prototype rules, **not** the accuracy of a production AI model. The current version uses deterministic JavaScript rules, not a live LLM, semantic verification, or external fact-checking.

## Files
- `index.html` — interactive browser prototype
- `TraceNote_Workflow.svg` — editable workflow diagram
- `MODEL_CONTRACT.md` — proposed model output contract and validators
- `EVALUATION_CASES.json` — sample evaluation cases
- `INTERVIEW_GUIDE.md` — project rationale, evaluation plan and interview pitch

## Deployment
GitHub Pages is configured through the workflow in `.github/workflows/pages.yml`, which publishes the repository root when changes are pushed to `main`.
