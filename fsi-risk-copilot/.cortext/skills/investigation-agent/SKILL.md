---
name: investigation-agent
description: >
  Builds the Cortex Agent that combines structured transaction analysis,
  regulatory search, and investigation report generation.
---

# FSI Investigation Agent

## Purpose

Create a Cortex Agent that supports alert investigation without making
autonomous compliance decisions.

## Required Agent Tools

Configure applicable tools for:

1. Cortex Analyst semantic view
2. Regulatory Cortex Search service
3. Alert evidence retrieval
4. Related transaction retrieval
5. Draft investigation report generation
6. Audit-event recording

## Agent Workflow

For an alert investigation:

1. Resolve the requested alert.
2. Retrieve alert and transaction facts.
3. Retrieve triggered rule contributions.
4. Retrieve related transactions.
5. Retrieve relevant policy passages.
6. Separate facts, interpretations, and recommendations.
7. Identify missing evidence.
8. Generate a draft investigation report.
9. Mark the report as requiring human review.
10. Record tool and evidence references.

## Mandatory Agent Instructions

The agent must:

- Never state that an alert proves fraud or criminal activity.
- Never invent a transaction, customer attribute, policy, or citation.
- Label unsupported information as unavailable.
- Cite relevant policy sources.
- State the rules that contributed to an alert.
- State the observed value and configured threshold.
- Distinguish facts from AI-generated interpretation.
- Require investigator approval.
- Avoid automatically closing cases or submitting reports.
- Avoid exposing sensitive data not necessary for the request.

## Expected Response Structure

Return:

1. Investigation summary
2. Observed facts
3. Triggered indicators
4. Related activity
5. Policy references
6. Information gaps
7. Recommended review actions
8. Human-review notice

## Validation

Test:

- Correct tool routing
- Citation presence
- Unsupported-answer behavior
- Alert-to-evidence traceability
- Separation of facts and recommendations
- Human-review messaging
- Refusal to make unsupported accusations

## Output

Generate:

- sql/08_agent.sql
- sql/09_agent_tools.sql
- tests/agent_evaluation.yaml
- docs/agent_instructions.md
