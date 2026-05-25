# 6sense (6sense)

6sense is an AI-powered account-based marketing (ABM) and B2B intent data platform. Its Revenue AI platform combines firmographic, technographic, and intent signals — the Signalverse — with 6AI to identify in-market accounts, score and prioritize them, deanonymize web traffic, enrich contacts, and orchestrate Revenue Marketing and Sales Intelligence workflows. Public APIs surface company identification, firmographics, predictive scoring, people enrichment, and people search.

**URL:** [Visit APIs.json](https://raw.githubusercontent.com/api-evangelist/6sense/refs/heads/main/apis.yml)

**Run:** [Capabilities Using Naftiko](https://github.com/naftiko/fleet?utm_source=api-evangelist&utm_medium=readme&utm_campaign=company-api-evangelist&utm_content=repo)

## Tags

 - ABM, Account-Based Marketing, Intent Data, B2B, Predictive Analytics, Revenue, Sales Intelligence, AI, Marketing Technology

## Timestamps

- **Created:** 2026-05-25
- **Modified:** 2026-05-25

## APIs

### 6sense Company Identification API
Identify a company from a visitor IP address. Returns firmographics, product-level intent scoring, buying stage, profile fit, the 6QA flag, and segment membership. Powers web deanonymization.

**Host:** `https://epsilon.6sense.com`

- [OpenAPI](openapi/6sense-company-identification-api-openapi.yml)
- [JSON Schema — Company](json-schema/6sense-company-schema.json)
- [JSON Schema — Score](json-schema/6sense-score-schema.json)
- [Naftiko Capability — Company Identification](capabilities/company-identification.yaml)

### 6sense Company Firmographics API
Enrich a company by email or domain. Returns industry, employee/revenue ranges, SIC/NAICS classification, address, and segment membership.

**Host:** `https://api.6sense.com`

- [OpenAPI](openapi/6sense-company-firmographics-api-openapi.yml)
- [Naftiko Capability — Company Firmographics](capabilities/company-firmographics.yaml)

### 6sense Lead Scoring API
Returns predictive product-level scoring for a contact — company intent score, buying stage, profile fit, contact-level intent score, and contact grade — driven by 6sense's predictive analytics models.

**Host:** `https://scribe.6sense.com`

- [OpenAPI](openapi/6sense-lead-scoring-api-openapi.yml)
- [Naftiko Capability — Lead Scoring](capabilities/lead-scoring.yaml)

### 6sense Lead Scoring And Firmographics API
Combined endpoint returning firmographic enrichment, predictive scoring, and segment membership for a contact in one response.

**Host:** `https://scribe.6sense.com`

- [OpenAPI](openapi/6sense-lead-scoring-firmographics-api-openapi.yml)
- [Naftiko Capability — Lead Scoring + Firmographics](capabilities/lead-scoring-firmographics.yaml)

### 6sense People Enrichment API
Batch enrich up to 25 contacts per request keyed by email, LinkedIn URL, or 6sense peopleId. Returns profile data (job, location, skills, education) and embedded company firmographics. Up to 20 QPS per customer.

**Host:** `https://api.6sense.com`

- [OpenAPI](openapi/6sense-people-enrichment-api-openapi.yml)
- [JSON Schema — Contact](json-schema/6sense-contact-schema.json)
- [Naftiko Capability — People Enrichment](capabilities/people-enrichment.yaml)

### 6sense People Search API
Search contacts at a target company by domain with optional filters (job title, function, level, location, industry). Includes a dictionary endpoint for valid filter values.

**Host:** `https://api.6sense.com`

- [OpenAPI](openapi/6sense-people-search-api-openapi.yml)
- [Naftiko Capability — People Search](capabilities/people-search.yaml)

## Authentication

All endpoints use token-based authentication via the `Authorization` header:

```
Authorization: Token <api_token>
```

## Solutions

- **AI-Powered Account-Based Marketing** — Identify in-market accounts and orchestrate ABM at scale using 6AI and the Signalverse.
- **Web Deanonymization** — Resolve anonymous website traffic to companies.
- **Predictive Lead and Account Scoring** — Real-time per-product scoring tied to buying stage.
- **B2B Data Enrichment** — Company and contact enrichment via on-demand and bulk APIs.
- **Revenue Marketing Automation** — AI Email Agents, Audience Builder, Digital Advertising, Intelligent Workflows.
- **Sales Intelligence** — Sales Copilot, Account Prioritization, List Builder, Alerts, Chrome Extension.

## Operational Surface

- [Plans / Pricing](plans/6sense-plans-pricing.yml) — API Commons Plans 0.1 (contract pricing; tiers reconciled from public marketing pages).
- [Rate Limits](rate-limits/6sense-rate-limits.yml) — API Commons Rate Limits 0.1 (100 RPM defaults; People Enrichment 20 QPS).
- [FinOps](finops/6sense-finops.yml) — FOCUS 1.3-aligned FinOps definition for the Revenue AI subscription model.
- [Vocabulary](vocabulary/6sense-vocabulary.yml) — Domain terms (6QA, Signalverse, Buying Stage, Profile Fit, etc.).
- [JSON-LD Context](json-ld/6sense-context.jsonld) — Linked-data semantics for Company, Contact, Score, and Segment.

## Common Properties

- [Website](https://6sense.com)
- [Revenue AI Platform](https://6sense.com/platform)
- [API Portal](https://api.6sense.com/docs/)
- [API Overview](https://support.6sense.com/docs/6sense-api-overview)
- [Knowledge Base](https://support.6sense.com)
- [Blog](https://6sense.com/blog)
- [Customers](https://6sense.com/customers)
- [LinkedIn](https://www.linkedin.com/company/6sense)
- [6si GitHub Org](https://github.com/6si)
- [Pricing](https://6sense.com/pricing)

## Integrations

Salesforce, HubSpot, Marketo, Eloqua, Pardot, Microsoft Dynamics, LinkedIn, Slack, Outreach, Salesloft, Snowflake (Data Pack ingest), and the 6sense web pixel.

## Maintainers

- Kin Lane — [info@apievangelist.com](mailto:info@apievangelist.com)
