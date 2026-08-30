---
name: regulatory-search
description: >
  Creates the policy-ingestion, chunking, metadata, and Cortex Search
  components for regulatory and AML content.
---

# Regulatory Search

## Purpose

Build a cited retrieval layer for internal AML policies and permitted
regulatory documents.

## Required Metadata

Every document and chunk must preserve:

- DOCUMENT_ID
- DOCUMENT_TITLE
- DOCUMENT_TYPE
- REGULATION_NAME
- JURISDICTION
- VERSION
- EFFECTIVE_DATE
- SECTION_ID
- SECTION_NAME
- SOURCE_REFERENCE
- INGESTED_AT
- CONTENT

## Required Objects

Create:

- AI.REGULATORY_DOCUMENTS
- AI.REGULATORY_CHUNKS
- AI.REGULATORY_SEARCH_SERVICE
- AI.SEARCH_EVALUATION_SET

Use the actual supported Cortex Search syntax available in the connected
Snowflake account.

## Chunking Requirements

- Preserve section boundaries where practical.
- Include document and section metadata in every chunk.
- Avoid mixing multiple policy sections into an ambiguous chunk.
- Do not remove qualification, exceptions, or effective-date wording.
- Retain source references required for citations.

## Answer Requirements

Retrieved policy answers must include:

- Document title
- Section name
- Version
- Effective date
- Source reference
- Supporting passage or reference

If no supporting passage is retrieved, return:

"No supporting policy passage was found in the configured knowledge base."

Do not generate an unsupported regulatory answer.

## Validation Questions

Test retrieval for:

1. High-value transaction evidence requirements
2. Transaction-velocity investigation steps
3. Structuring-related escalation
4. Unusual geography review
5. Case documentation requirements
6. Human review and approval
7. Policy version and effective date

## Output

Generate:

- sql/06_regulatory_tables.sql
- sql/07_regulatory_search.sql
- tests/regulatory_search_questions.yaml
- docs/regulatory_ingestion.md
