# 6sense

<!-- API-EVANGELIST-PROVENANCE:BEGIN -->
> ### About this repository
>
> **This is not our API.** This repository is an independent, third-party profile of a company's
> **publicly available** API surface, maintained by [API Evangelist](https://apievangelist.com).
> API Evangelist does not operate, host, resell, or support this company's APIs, and is not
> affiliated with or endorsed by the company unless stated on the profile.
>
> **Where the information came from.** Everything here is assembled from material a member of the
> public can reach with a browser and no credentials — the company's own website, developer portal
> and documentation, the specifications it publishes for public use (OpenAPI, AsyncAPI, JSON Schema,
> `apis.json`, `llms.txt` and similar), its public repositories, and its public status, pricing and
> changelog pages. **Nothing here is obtained by breaching a system, defeating an access control, or
> using credentials of any kind.**
>
> **The rating is an independent assessment.** The Kin Score and Agent Readiness rating are
> independently calculated scores of a company's *public* API artifacts, produced by API Evangelist
> against a published rubric. They are not certifications, endorsements, security assessments, or
> audits, and they score published artifacts — not the quality, safety, or security of the software.
>
> **Corrections, re-scores, and removal are free.** No partnership, contract, or purchase is
> required, and you do not need to justify the request.
>
> - **Something wrong?** Open an issue on this repository, or email
>   [info@apievangelist.com](mailto:info@apievangelist.com).
> - **Published something new?** Ask for a re-score and we will re-run the rating.
> - **Want the listing taken down?** Say so and we will honor it. The profile is reduced to your
>   company name, a factual description, and a link to your own site, and the company is recorded as
>   **unrated** — never scored zero for having asked.
>
> **Response times.** Acknowledgement within **one business day**; removal or restriction within
> **two business days**; corrections and re-scores within **five business days**.
>
> **Not from the company, and here with a question?** You are welcome here — we would rather be the
> front line and point you the right way than have a good report go nowhere. What this repository
> can answer is narrow, though, so it is worth knowing who you are actually looking for:
>
> - **A question about how the API works, an account, billing, or a bug in the service** — that is
>   the company's own support, not us. We profile this API; we do not operate it and cannot see
>   your account.
> - **A bug in an open-source project we only catalog** — file it on that project's own repository.
>   This has happened with a real and correct bug report that reached us instead of the people who
>   could fix it, which helped nobody.
> - **Anything about this listing itself** — the description, the tags, the rating, a missing or
>   wrong artifact — is ours. Open an issue here.
> - **Not sure, or something general about API Evangelist or APIs.io** — open an issue on the
>   [APIs.io Inbox](https://github.com/api-search/inbox) and we will route it.
>
> **This repository contains no software, and we will never ask you to download anything.** There is
> no build, release, installer, or binary here — only text and machine-readable API descriptions, so
> there is nothing here that can be "corrupt" or need "repairing". Any issue, comment, or email
> claiming otherwise and offering a download link is not from us and is hostile. Do not follow the
> link; it is a lure. Report it to GitHub and, if you like, tell us at
> [info@apievangelist.com](mailto:info@apievangelist.com) so we can take it down.
>
> **On a security or compliance team?** Email
> [info@apievangelist.com](mailto:info@apievangelist.com) with *security* in the subject line and
> you will get a person, not a form. We will tell you exactly which public URLs this profile was
> built from so your team can see the same surface we did, and we will take the listing down on
> request while you work through it.
>
> Full detail: **[Where this data comes from](https://apievangelist.com/about/where-our-data-comes-from)**
<!-- API-EVANGELIST-PROVENANCE:END -->

6sense Insights is a B2B revenue AI platform that identifies in-market accounts from anonymous buying signals and orchestrates marketing and sales against them. Its Signalverse intent graph, Master Company Database of roughly 76 million company accounts and predictive models power account-based marketing, advertising, AI email agents and sales intelligence. For developers, 6sense exposes six HTTP data APIs across three hosts — Company Identification, Company Firmographics, Lead Scoring, Lead Scoring and Firmographics, People Enrichment and People Search — plus the acquired AI Email (Saleswhale) API with a signed webhook surface, and a hosted remote MCP server at api.6sense.com/mcp for agent access. Access is token-based and metered against contract-year credit pools rather than list-priced plans.

**Areas:** Account Based Marketing · Intent Data · B2B · Predictive Analytics · Revenue · Sales Intelligence · Artificial Intelligence · Marketing Technology

## 6sense on APIs.io

Everything profiled for 6sense is published on APIs.io rather than in this repository. Start at the provider page — **[apis.io/providers/6sense/](https://apis.io/providers/6sense/)** — or go straight to one of the APIs or properties below.

### APIs (5)

- [6sense Company API](https://apis.io/apis/6sense/6sense-company-api/) — The Company API from 6sense — 1 operation(s) for company.
- [6sense Enrichment API](https://apis.io/apis/6sense/6sense-enrichment-api/) — The Enrichment API from 6sense — 2 operation(s) for enrichment.
- [6sense People API](https://apis.io/apis/6sense/6sense-people-api/) — The People API from 6sense — 4 operation(s) for people.
- [6sense MCP Server](https://apis.io/apis/6sense/6sense-mcp/) — Hosted remote Model Context Protocol server at https://api.6sense.com/mcp (beta). Read-only retrieval of Revvy AI-powered 6sense insights — account…
- [6sense Scoring API](https://apis.io/apis/6sense/6sense-scoring-api/) — The Scoring API from 6sense — 1 operation(s) for scoring.

### Published properties

Each property below is a page on APIs.io carrying the machine-readable artifact and what it says.

#### AsyncAPI (2)

Event-driven and webhook contracts.

- [6sense AI Email Webhooks](https://apis.io/asyncapis/6sense/6sense-ai-email-asyncapi/)
- [6Sense Ai Email Webhooks](https://apis.io/asyncapis/6sense/6sense-ai-email-webhooks/)

#### Event channels (1)

Individual events and webhooks the provider emits.

- [/](https://apis.io/channels/6sense/webhook/)

#### GraphQL (1)

GraphQL schemas.

- [Moved to /providers/6sense/](https://apis.io/graphqls/6sense/6sense-graphql/)

#### MCP servers (1)

Model Context Protocol servers that expose the API to agents.

- [6sense MCP](https://apis.io/servers/6sense/6sense-mcp/)

#### Agentic access (1)

Which operations an agent can call, which act, and which need a human in the loop.

- [6Sense Agentic Access](https://apis.io/agentic-access/6sense/6sense-agentic-access/)

#### JSON Schema (3)

The data models the API reads and writes.

- [6sense Company](https://apis.io/schemas/6sense/6sense-company/)
- [6sense Enriched Contact](https://apis.io/schemas/6sense/6sense-contact/)
- [6sense Product Score](https://apis.io/schemas/6sense/6sense-score/)

#### JSON-LD (1)

Linked-data contexts for the provider's vocabulary.

- [6Sense Context](https://apis.io/jsonld/6sense/6sense-context/)

#### Vocabulary (1)

The provider's domain terms, defined.

- [6Sense Vocabulary](https://apis.io/vocabularies/6sense/6sense-vocabulary/)

#### Collections (9)

Postman and Open Collection request collections.

- [6sense Firmographics Company API](https://apis.io/collections/6sense/open-6sense-company-api/)
- [6sense Company Firmographics API](https://apis.io/collections/6sense/open-6sense-company-firmographics-api/)
- [6sense Company Identification API](https://apis.io/collections/6sense/open-6sense-company-identification-api/)
- [6sense Firmographics Company Enrichment API](https://apis.io/collections/6sense/open-6sense-enrichment-api/)
- [6sense Lead Scoring API](https://apis.io/collections/6sense/open-6sense-lead-scoring-api/)
- [6sense Lead Scoring And Firmographics API](https://apis.io/collections/6sense/open-6sense-lead-scoring-firmographics-api/)
- [6sense Firmographics Company People API](https://apis.io/collections/6sense/open-6sense-people-api/)
- [6sense People Enrichment API](https://apis.io/collections/6sense/open-6sense-people-enrichment-api/)
- [6sense People Search API](https://apis.io/collections/6sense/open-6sense-people-search-api/)

#### Overlays (8)

OpenAPI overlays, including conversational phrasing for each operation.

- [6Sense Company Api Phrasing Overlay](https://apis.io/overlays/6sense/6sense-company-api-phrasing-overlay/)
- [6Sense Company Overlay](https://apis.io/overlays/6sense/6sense-company-overlay/)
- [6Sense Enrichment Api Phrasing Overlay](https://apis.io/overlays/6sense/6sense-enrichment-api-phrasing-overlay/)
- [6Sense Enrichment Overlay](https://apis.io/overlays/6sense/6sense-enrichment-overlay/)
- [6Sense People Api Phrasing Overlay](https://apis.io/overlays/6sense/6sense-people-api-phrasing-overlay/)
- [6Sense People Overlay](https://apis.io/overlays/6sense/6sense-people-overlay/)
- [6Sense Scoring Api Phrasing Overlay](https://apis.io/overlays/6sense/6sense-scoring-api-phrasing-overlay/)
- [6Sense Scribe Overlay](https://apis.io/overlays/6sense/6sense-scribe-overlay/)

#### Governance rules (1)

Spectral rulesets for the provider's contracts.

- [6sense — jsonschema rules](https://apis.io/rules/6sense/6sense-jsonschema-spectral-rules/)

#### Security (3)

Authentication, trust centre, and vulnerability disclosure.

- [6Sense Authentication](https://apis.io/security/6sense/6sense-authentication/)
- [6Sense Domain Security](https://apis.io/security/6sense/6sense-domain-security/)
- [6Sense Trust Center](https://apis.io/security/6sense/6sense-trust-center/)

#### OAuth scopes (1)

The permissions the API asks for.

- [6Sense Scopes](https://apis.io/scopes/6sense/6sense-scopes/)

#### Plans and pricing (1)

Published plans, tiers and prices.

- [6Sense Plans Pricing](https://apis.io/plans/6sense/6sense-plans-pricing/)

#### Rate limits (1)

Published request limits.

- [6Sense Rate Limits](https://apis.io/rate-limits/6sense/6sense-rate-limits/)

#### FinOps (1)

What the API costs to run, by operation.

- [6Sense Finops](https://apis.io/finops/6sense/6sense-finops/)

## Where to find this API

Links to the company's own pages. This repository publishes no copy of their specifications — the canonical document is theirs and lives at the URLs below.

- [Website](https://6sense.com)
- [Documentation](https://6sense.com/platform)
- [Getting started](https://support.6sense.com/docs/api-credits-api-tokens)
- [API reference](https://api.6sense.com/docs/)
- [Pricing](https://6sense.com/pricing)
- [Support](https://support.6sense.com)
- [Changelog](https://support.6sense.com/docs/product-release-notes)
- [Blog](https://6sense.com/blog)
- [Compliance](https://trust.6sense.com/)
- [Terms of service](https://6sense.com/terms-of-use/)
- [Privacy policy](https://6sense.com/privacy-policy/)
- [GitHub](https://github.com/6si)
- [Status](https://status.6sense.com/)

## API Evangelist rating

**Kin Score 71.8** — exemplar · rubric 0.25.0 · scored 2026-10-23

| Facet | Score |
|---|---|
| Discoverability | 80.0 |
| Contract quality | 60.8 |
| Contract governance | 41.7 |
| Operational transparency | 81.6 |
| Developer ergonomics | 58.9 |
| Access clarity | 93.4 |

**Agent readiness 54.6** — agent-ready (gated down from agent-native)

| Agent-readiness dimension | Result |
|---|---|
| Spec Presence | yes |
| Agentic Access | derived (partial credit) |
| Reversibility Documented | — |
| MCP Server | verified |
| Auth Clarity | served (partial credit) |
| Idempotency | — |
| Error Semantics | verified |
| OpenAPI Examples | — |
| Rate Limit Signal | documented (partial credit) |
| Event Surface Described | yes |
| Agent Skills | derived (partial credit) |
| Well Known Catalog | — |
| Consent Identity | — |
| Agent Card | — |
| Dry Run Mode | — |
| Delegated Identity | served (partial credit) |
| Protected Resource Metadata | verified |
| Dynamic Client Registration | yes |
| Agentic Commerce | — |
| Pagination Ratio | — |
| Operation Distinctiveness | distinct |

**Regulatory alignment 36.4** — Horizontal (data, software, accessibility, platform)

The rubric is published at [github.com/api-evangelist/kin-score](https://github.com/api-evangelist/kin-score). The per-check breakdown behind these numbers — which checks were earned, partial or missed — along with score history and how this provider compares to its peers, is available at [apis.io/providers/6sense/](https://apis.io/providers/6sense/).

## How this profile is made

API Evangelist profiles a company's public API surface the way a developer would find it: the website, developer portal and documentation, the specifications it publishes, its public repositories, and its pricing, status and changelog pages. From that it derives the properties above — contracts split per API, workflows, schemas, collections, governance rules, plans and rate limits — and scores them against the published [Kin Score rubric](https://github.com/api-evangelist/kin-score).

The artifacts are published on [APIs.io](https://apis.io), not in this repository. This repository is the public record for 6sense: the place to say something is wrong, missing or out of date, and to ask for a re-score or a removal.

## Open an issue

- **Something about this listing** — a wrong description, a missing API, a stale artifact or a question about the rating: [open an issue on this repository](https://github.com/api-evangelist/6sense/issues/new).
- **A new API, or one that is not in the catalog yet** — [submit it on APIs.io](https://apis.io/add/).
- **Anything else** — [the APIs.io inbox](https://github.com/api-search/inbox/issues/new) or [info@apievangelist.com](mailto:info@apievangelist.com).
