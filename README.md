# 6sense (6sense)

**APIs.json:** [https://raw.githubusercontent.com/api-evangelist/6sense/refs/heads/main/apis.yml](https://raw.githubusercontent.com/api-evangelist/6sense/refs/heads/main/apis.yml)

## Scope

- **Access:** 3rd-Party

## Tags

- ABM
- Account-Based Marketing
- Intent Data
- B2B
- Predictive Analytics
- Revenue
- Sales Intelligence
- AI
- Marketing Technology

## APIs

### 6sense Company Identification API

Identify a company from a visitor IP address and return firmographics, product-level intent scoring, buying stage, profile fit, 6QA flag, and segment membership. Powers 6sense's web deanonymization use case.

- **Human URL:** [https://api.6sense.com/docs/](https://api.6sense.com/docs/)

#### Tags

- ABM
- Intent
- Web Deanonymization
- B2B

#### Properties

- [Documentation](https://api.6sense.com/docs/)
- [Documentation](https://support.6sense.com/docs/6sense-api-overview)
- [OpenAPI](openapi/6sense-company-identification-api-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/6sense-company-identification-api.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/6sense-company-identification-api.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)
- [JSON Schema](json-schema/6sense-company-schema.json) — [JSON Schema](https://json-schema.org/specification)
- [JSON Schema](json-schema/6sense-score-schema.json) — [JSON Schema](https://json-schema.org/specification)
- [JSON-LD](json-ld/6sense-context.jsonld) — [JSON-LD](https://www.w3.org/TR/json-ld11/)

### 6sense Company Firmographics API

Enrich a company by email or domain. Returns industry, employee and revenue ranges, SIC/NAICS classification, address, and segment membership.

- **Human URL:** [https://api.6sense.com/docs/](https://api.6sense.com/docs/)

#### Tags

- ABM
- Firmographics
- Enrichment

#### Properties

- [Documentation](https://api.6sense.com/docs/)
- [OpenAPI](openapi/6sense-company-firmographics-api-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/6sense-company-firmographics-api.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/6sense-company-firmographics-api.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)
- [JSON Schema](json-schema/6sense-company-schema.json) — [JSON Schema](https://json-schema.org/specification)

### 6sense Lead Scoring API

Returns predictive product-level scoring for a contact — company intent score and buying stage, profile fit, contact-level intent score, and contact grade — driven by 6sense's predictive analytics models.

- **Human URL:** [https://api.6sense.com/docs/](https://api.6sense.com/docs/)

#### Tags

- ABM
- Scoring
- Intent
- Predictive Analytics

#### Properties

- [Documentation](https://api.6sense.com/docs/)
- [OpenAPI](openapi/6sense-lead-scoring-api-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/6sense-lead-scoring-api.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/6sense-lead-scoring-api.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)
- [JSON Schema](json-schema/6sense-score-schema.json) — [JSON Schema](https://json-schema.org/specification)

### 6sense Lead Scoring And Firmographics API

Combined endpoint that returns firmographic enrichment, predictive scoring, and segment membership for a contact in a single response.

- **Human URL:** [https://api.6sense.com/docs/](https://api.6sense.com/docs/)

#### Tags

- ABM
- Scoring
- Firmographics
- Intent

#### Properties

- [Documentation](https://api.6sense.com/docs/)
- [OpenAPI](openapi/6sense-lead-scoring-firmographics-api-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/6sense-lead-scoring-firmographics-api.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/6sense-lead-scoring-firmographics-api.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### 6sense People Enrichment API

Batch enrich up to 25 contact records per request keyed by email, LinkedIn URL, or 6sense peopleId. Returns rich profile data (job, location, skills, education) and embedded company firmographics. Up to 20 QPS per customer.

- **Human URL:** [https://api.6sense.com/docs/](https://api.6sense.com/docs/)

#### Tags

- Enrichment
- People
- Contacts
- B2B

#### Properties

- [Documentation](https://api.6sense.com/docs/)
- [OpenAPI](openapi/6sense-people-enrichment-api-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/6sense-people-enrichment-api.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/6sense-people-enrichment-api.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)
- [JSON Schema](json-schema/6sense-contact-schema.json) — [JSON Schema](https://json-schema.org/specification)

### 6sense People Search API

Search contacts at a target company by domain with optional job-title, function, level, location, and industry filters. Includes a dictionary endpoint exposing valid filter values.

- **Human URL:** [https://api.6sense.com/docs/](https://api.6sense.com/docs/)

#### Tags

- Search
- People
- Contacts

#### Properties

- [Documentation](https://api.6sense.com/docs/)
- [OpenAPI](openapi/6sense-people-search-api-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/6sense-people-search-api.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/6sense-people-search-api.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

## Common Properties

- [Website](https://6sense.com)
- [Documentation](https://6sense.com/platform)
- [Portal](https://api.6sense.com/docs/)
- [Documentation](https://support.6sense.com/docs/6sense-api-overview)
- [Support](https://support.6sense.com)
- [Case Studies](https://6sense.com/customers)
- [Blog](https://6sense.com/blog)
- [LinkedIn](https://www.linkedin.com/company/6sense)
- [Github](https://github.com/6si)
- [Pricing](https://6sense.com/pricing)
- [Plans](plans/6sense-plans-pricing.yml)
- [Rate Limits](rate-limits/6sense-rate-limits.yml)
- [Fin Ops](finops/6sense-finops.yml)
- [Vocabulary](vocabulary/6sense-vocabulary.yml)
- [JSON-LD](json-ld/6sense-context.jsonld) — [JSON-LD](https://www.w3.org/TR/json-ld11/)

## Maintainers

**FN:** Kin Lane
**Email:** info@apievangelist.com
