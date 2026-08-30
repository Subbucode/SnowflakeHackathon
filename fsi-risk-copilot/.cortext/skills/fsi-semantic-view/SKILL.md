---
name: fsi-semantic-view
description: >
  Builds and validates a Cortex Analyst semantic view for transaction,
  customer, account, alert, and investigation data.
---

# FSI Semantic View

## Purpose

Create a governed business semantic layer for natural-language analysis
of transaction risk and AML alerts.

## Business Entities

Include:

- Customer
- Account
- Transaction
- Beneficiary
- Alert
- Indicator
- Investigation case

## Dimensions

Include relevant dimensions for:

- Transaction date and time
- Transaction type
- Currency
- Origin country
- Destination country
- Channel
- Customer risk category
- Indicator type
- Alert severity
- Alert status
- Case status

## Measures and Metrics

Include:

- Transaction count
- Total transaction amount
- Average transaction amount
- Alert count
- Triggered indicator count
- Average risk score
- High-severity alert count
- Open-case count
- Unique affected account count

Use correct aggregation and distinct-count behavior.

Do not aggregate amounts across different currencies unless a normalized
amount and conversion basis are available.

## Synonyms

Add business synonyms including:

- Suspicious transaction
- Flagged payment
- Unusual activity
- AML alert
- Fraud signal
- Transaction-monitoring alert
- High-risk activity
- Risk indicator
- Investigation case

## Verified Queries

Create verified queries for:

1. High-severity alerts during a date range
2. Alerts grouped by indicator type
3. Related transactions for an alert
4. Accounts with multiple triggered indicators
5. Alert evidence for a transaction
6. Alert trends by day
7. Open investigations by severity

## Validation Requirements

Before deployment:

- Validate relationship cardinality.
- Prevent transaction duplication caused by joins.
- Validate every metric against direct SQL.
- Verify date filtering.
- Verify currency handling.
- Verify customer-to-account and account-to-transaction relationships.
- Test business synonyms.

## Output

Generate:

- sql/05_semantic_view.sql
- tests/validate_semantic_metrics.sql
- docs/semantic_model.md
