---
name: fsi-copilot-orchestrator
description: >
  Coordinates the end-to-end construction of an FSI Risk, Fraud,
  AML, and Regulatory Intelligence Copilot in Snowflake.
---

# FSI Copilot Orchestrator

## Purpose

Use this skill when the user asks to build, review, test, or deploy the
FSI Risk, Fraud, AML, and Regulatory Intelligence Copilot.

This skill coordinates the following project skills:

1. synthetic-banking-data
2. fraud-aml-signals
3. fsi-semantic-view
4. regulatory-search
5. investigation-agent
6. compliance-streamlit
7. fsi-evaluation

## Target Architecture

The solution must use:

- Synthetic banking data
- Snowflake tables and views
- Explainable SQL-based fraud and AML indicators
- Cortex Analyst through a semantic view
- Cortex Search for regulatory and policy documents
- Cortex Agent for tool orchestration
- Streamlit in Snowflake for the user interface
- Audit and feedback tables
- Human review before consequential actions

## Required Build Sequence

Always implement the solution in this order:

1. Inspect available role, warehouse, database, schema, and Cortex features.
2. Create the database and schemas.
3. Generate synthetic customers, accounts, and transactions.
4. Create explainable transaction features.
5. Create fraud and AML alert rules.
6. Create and validate the semantic view.
7. Load and chunk policy documents.
8. Create and validate the Cortex Search service.
9. Test Analyst and Search independently.
10. Create the Cortex Agent.
11. Build the Streamlit application.
12. Run the evaluation test set.
13. Produce a deployment and demonstration checklist.

Do not skip validation between stages.

## Snowflake Object Standards

Use the following database unless the user supplies another database:

FSI_COPILOT

Use these schemas:

- RAW
- CURATED
- AI
- APP
- AUDIT

Use uppercase Snowflake object names.

Generate idempotent scripts when practical.

Store generated SQL under the sql directory.

Store Streamlit code under the app directory.

Store evaluation assets under the tests directory.

## Safety and Compliance Requirements

The solution must:

- Use only synthetic data during development.
- Never describe an alert as proof of criminal activity.
- Describe alerts as indicators requiring investigation.
- Distinguish observed facts from generated interpretations.
- Preserve policy document title, section, version, and effective date.
- Cite retrieved policy material.
- Never invent unavailable evidence.
- Require human review before case closure or regulatory submission.
- Record agent questions, tools used, references, responses, and feedback.
- Avoid exposing unnecessary customer information.

## Change-Control Rules

Before executing SQL:

1. Explain what objects will be created or modified.
2. Generate the SQL.
3. Validate references and dependencies.
4. Highlight destructive statements.
5. Request approval when DROP, REPLACE, or destructive DML is involved.

Do not drop databases, schemas, stages, integrations, services, or agents
unless the user explicitly requests it.

## Completion Criteria

The solution is complete only when:

- Seeded suspicious scenarios generate expected alerts.
- Normal scenarios do not generate unexplained high-risk alerts.
- Natural-language questions produce valid SQL.
- Regulatory answers include source metadata.
- The agent separates facts from recommendations.
- Streamlit displays alert evidence and policy references.
- Evaluation results are recorded and reviewable.
