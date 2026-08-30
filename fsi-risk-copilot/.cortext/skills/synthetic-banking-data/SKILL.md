---
name: synthetic-banking-data
description: >
  Creates safe synthetic customer, account, beneficiary, transaction,
  and risk-profile data for the FSI Copilot.
---

# Synthetic Banking Data

## When to Use

Use this skill when creating or refreshing synthetic FSI development data.

## Required Tables

Create the following tables in FSI_COPILOT.RAW:

- CUSTOMERS
- ACCOUNTS
- BENEFICIARIES
- TRANSACTIONS
- CUSTOMER_RISK_PROFILE
- HIGH_RISK_JURISDICTIONS
- EXPECTED_SCENARIOS

## Data Requirements

Generate synthetic records only.

Include normal behavior and seeded test scenarios for:

1. High transaction amount
2. Rapid transaction velocity
3. Structuring below a configured threshold
4. Unusual destination geography
5. Dormant-account activity
6. New beneficiary followed by a large payment
7. Amount outside the customer's historical pattern
8. Device or channel change
9. Multiple sender accounts to one beneficiary
10. Circular movement between accounts

## Ground Truth

Every deliberately seeded scenario must have:

- SCENARIO_ID
- SCENARIO_TYPE
- CUSTOMER_ID
- ACCOUNT_ID
- EXPECTED_INDICATOR
- EXPECTED_SEVERITY
- EXPECTED_ALERT_FLAG
- TEST_DESCRIPTION

Store this information in RAW.EXPECTED_SCENARIOS.

Ground-truth fields must not be included as fraud-model input features.

## Generation Rules

- Use deterministic generation with a documented seed.
- Do not use names, email addresses, account numbers, or identifiers
  belonging to real individuals.
- Use ISO-style timestamps and currency codes.
- Ensure account and transaction relationships are valid.
- Include sufficient normal transactions for comparison.
- Make generated scenarios reproducible.
- Add comments explaining every seeded scenario.

## Required Output

Generate:

- sql/01_tables.sql
- sql/02_synthetic_data.sql
- tests/expected_alerts.csv
- Documentation of record relationships
- Validation queries for referential integrity

Do not execute generated SQL until it has been reviewed.
