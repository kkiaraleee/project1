# TraceNote model contract (proposed)

This is a design artifact for a future LLM-backed version. The current demo does not call a model.

## Suggested structured response
```json
{
  "summary": [{"text": "Short, source-grounded observation", "evidence_ids": ["S02"]}],
  "claims": [{"claim": "Draft claim", "evidence_ids": ["S01"], "status": "supported|conflicting|insufficient"}],
  "caveats": [{"text": "Limitation", "evidence_ids": ["S03"]}],
  "actions": [{"text": "Next step", "owner": null, "evidence_ids": ["S04"]}],
  "review_required": true,
  "review_reasons": ["Conflicting numerical claim"]
}
```

## Validation layer
1. Reject malformed output or unexpected fields.
2. Confirm every evidence ID exists in the supplied source ledger.
3. Where an exact quote is returned, verify that the quote is a substring of its cited source.
4. Flag numerical conflicts for the same topic; do not average or silently pick one.
5. If evidence is absent or ambiguous, use `insufficient` and ask for review.
6. Do not allow the model to publish, email, or modify source documents autonomously.
7. Apply approved redaction before external model calls and before export.
8. Keep a human approval gate for sensitive, ambiguous, conflicting, or externally shared content.

## Failure behaviour
- Model/API timeout: preserve input and offer retry or manual review.
- Schema failure: do not show the result as approved.
- Invalid evidence ID: reject the claim or mark it unsupported.
- Low evidence coverage: ask a clarifying question rather than fill gaps.
- Sensitive input: warn and stop any unapproved external transfer.

## Evaluation
Measure evidence coverage, conflict recall, unsupported-claim rate, privacy leakage in exports, reviewer usefulness, and unsafe release rate on a labelled test set. Any numeric goals in the workflow are proposed targets, not observed results.
