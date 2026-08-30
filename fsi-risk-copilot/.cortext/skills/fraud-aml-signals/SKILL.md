---
name: fraud-aml-signals
description: >
  Creates transparent SQL-based fraud and AML indicators, scores,
  alerts, and evidence records.
---

# Fraud and AML Signals

## Objective

Create explainable transaction-monitoring indicators using Snowflake SQL.

The language model must not determine whether a transaction is fraudulent.
The language model may explain deterministic indicators and retrieve
supporting policy.

## Required Indicators

Implement configurable indicators for:

- HIGH_VALUE
- HIGH_VELOCITY
- STRUCTURING_PATTERN
- HIGH_RISK_GEOGRAPHY
- DORMANT_ACCOUNT_ACTIVITY
- NEW_BENEFICIARY
- AMOUNT_DEVIATION
- DEVICE_CHANGE
- MANY_TO_ONE_TRANSFER
- CIRCULAR_TRANSFER_PATTERN

## Required Objects

Create:

- CURATED.TRANSACTION_FEATURES
- CURATED.TRANSACTION_INDICATORS
- CURATED.FRAUD_ALERTS
- CURATED.ALERT_EVIDENCE
- CURATED.ALERT_RELATED_TRANSACTIONS
- CURATED.RULE_CONFIGURATION

## Explainability Requirements

For each evaluated transaction preserve:

- RULE_ID
- RULE_NAME
- RULE_VERSION
- RULE_DESCRIPTION
- THRESHOLD_USED
- OBSERVED_VALUE
- CONTRIBUTION_SCORE
- TRIGGERED_FLAG
- EVIDENCE_REFERENCE

The final risk score must equal the sum of its documented contributions.

## Separation of Responsibilities

Observed fact examples:

- Transaction amount was 9,800.
- Five payments occurred within one hour.
- Destination country matched a configured risk list.

Interpretation examples:

- Activity requires review for a possible structuring pattern.
- Transaction differs materially from recent account behavior.

Never represent an interpretation as an observed fact.

## Required Validation

Generate SQL tests that verify:

1. All seeded positive scenarios trigger their expected indicator.
2. Negative scenarios remain below the configured threshold.
3. Risk score equals the sum of rule contributions.
4. Evidence references resolve to valid transaction records.
5. Rule versions and thresholds are populated.
6. No ground-truth label is used as an input feature.

## Output Files

Generate:

- sql/03_features.sql
- sql/04_alerts.sql
- tests/validate_fraud_signals.sql
- docs/fraud_rule_catalog.md
