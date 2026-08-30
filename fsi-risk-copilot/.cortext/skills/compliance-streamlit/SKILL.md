---
name: compliance-streamlit
description: >
  Builds a Streamlit in Snowflake application for fraud-alert review,
  policy lookup, investigation, and draft reporting.
---

# Compliance Streamlit Application

## Required Pages

Create:

1. Risk Overview
2. Alert Investigation
3. Regulatory Copilot
4. Investigation Report
5. Evaluation and Feedback

## Risk Overview

Display:

- Alert counts by severity
- Alerts by indicator type
- Alert trends
- Risk-score distribution
- Open investigation cases

Do not claim that alerts represent confirmed fraud.

## Alert Investigation

Display:

- Alert identifier
- Transaction facts
- Triggered indicators
- Observed values
- Rule thresholds
- Score contributions
- Related transactions
- Policy references
- Missing evidence

## Regulatory Copilot

Provide:

- Natural-language question input
- Agent-generated answer
- Document title
- Section name
- Version
- Effective date
- Source reference
- Clear unsupported-answer messaging

## Investigation Report

Separate:

- Observed facts
- Triggered indicators
- AI-generated interpretation
- Policy references
- Information gaps
- Recommended review actions

Display:

"Draft generated with AI assistance. Human review is required."

## Security Rules

- Use the active Snowpark session.
- Do not embed usernames, passwords, private keys, or tokens.
- Do not expose internal prompts.
- Do not display unrestricted customer data.
- Log feedback without storing unnecessary sensitive information.

## Output

Generate:

- app/streamlit_app.py
- app/pages/risk_overview.py
- app/pages/alert_investigation.py
- app/pages/regulatory_copilot.py
- app/pages/investigation_report.py
- app/pages/evaluation_feedback.py
- docs/streamlit_deployment.md
