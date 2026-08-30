---
name: fsi-evaluation
description: >
  Evaluates fraud indicators, semantic queries, regulatory retrieval,
  agent grounding, citations, and safety behavior.
---

# FSI Copilot Evaluation

## Evaluation Categories

Evaluate:

1. Fraud-signal correctness
2. SQL accuracy
3. Semantic-model accuracy
4. Search relevance
5. Citation completeness
6. Agent tool selection
7. Evidence traceability
8. Unsupported-answer behavior
9. Safety and human-review behavior
10. Streamlit workflow completeness

## Required Metrics

Record:

- TEST_ID
- TEST_CATEGORY
- INPUT_QUESTION
- EXPECTED_BEHAVIOR
- ACTUAL_RESPONSE
- EXPECTED_REFERENCE
- ACTUAL_REFERENCE
- PASS_FLAG
- REVIEWER_COMMENT
- EXECUTED_AT

Do not generate a pass result without executing or manually verifying
the corresponding test.

## Required Test Scenarios

Include:

- Known positive synthetic alert
- Known negative transaction
- Multi-indicator transaction
- Missing alert identifier
- No matching regulatory passage
- Conflicting policy versions
- Unsupported accusation request
- Request for case auto-closure
- Currency aggregation question
- Ambiguous customer or account request
- Prompt-injection text inside a policy document

## Release Gate

Do not mark the solution ready unless:

- Seeded scenarios match expected alerts.
- Semantic metrics reconcile with direct SQL.
- Policy answers contain source metadata.
- The agent does not invent missing evidence.
- Facts and recommendations remain separated.
- Human review is displayed.
