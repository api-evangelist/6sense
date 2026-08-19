---
name: 6sense — enrich and score an inbound lead
description: Take a form-fill email address and return company firmographics plus product-level predictive scores, choosing the right one of three overlapping 6sense operations.
api: openapi/6sense-people-api-openapi.yml
operations:
  - getFullLeadData
  - scoreLead
  - enrichCompany
generated: '2026-08-13'
method: generated
source: openapi/6sense-people-api-openapi.yml, openapi/6sense-enrichment-api-openapi.yml, https://api.6sense.com/docs/
---

# Enrich and score an inbound lead

The classic MAP/CRM flow: a lead fills in a form, you need to know who they work for and whether that account is in-market, before routing.

## Pick the right operation first

Three operations overlap here and they cost different amounts. Choose deliberately:

| You need | Operation | Host | Credits |
|---|---|---|---|
| Firmographics **and** scores in one call | `getFullLeadData` | `scribe.6sense.com` | 6sense Credits |
| Scores only | `scoreLead` | `scribe.6sense.com` | none |
| Firmographics only | `enrichCompany` | `api.6sense.com` | 6sense Credits |

If you only need to route on buying stage, use `scoreLead` — it is free. Reaching for `getFullLeadData` when you never read the `company` block is the single most common way to burn credits on this API.

Note the hosts differ per operation. There is no single 6sense base URL.

## Steps

1. **Both scoring operations require `email` *and* `country`.** `country` is not optional and the request will 400 without it. If your form does not collect country, derive it before calling, or use `enrichCompany` instead (which accepts `email` **or** `domain`).

2. **Send `application/x-www-form-urlencoded`, not JSON.**

   `scoreLead`, `getFullLeadData` and `enrichCompany` are form-encoded. Only the newer operations (`enrichPeople`, `searchPeople`) take JSON. Sending JSON to a form-encoded operation is a silent-shaped failure.

   ```
   POST https://scribe.6sense.com/v2/people/full
   Authorization: Token <api_token>
   Content-Type: application/x-www-form-urlencoded

   email=jane@acme.com&country=United States&company=Acme&title=VP Marketing&leadsource=webinar
   ```

   Optional fields that improve matching: `website`, `company`, `title`, `firstname`, `lastname`, `role`, `industry`, `leadsource`.

3. **Read `scores[]` per product.** As with every 6sense scoring surface, `scores` is an array with one entry per configured product. `getFullLeadData` returns both company-level and contact-level measures on each entry:

   - Company: `company_intent_score`, `company_buying_stage`, `company_profile_score`, `company_profile_fit`
   - Contact: `contact_intent_score`, `contact_grade` (`A`–`D`), `contact_profile_score`, `contact_profile_fit`

   Route on the pair, not on one number: a `Decision`-stage company with a `D`-grade contact is a different play from an `A`-grade contact at an `Awareness`-stage company.

4. **Expect camelCase here.** `getFullLeadData` returns `employeeRange`, `countryISOCode`, `sicdescription`. The Company Identification API returns the *same* fields as `employee_range`, `country_iso_code`, `sic_description`. Do not share a Company parser across the two.

5. **`segments` may be empty by design.** Segment and Score visibility is a per-token setting, secure by default. Have an admin enable it in API Settings if you need it.

## Error handling

- `402` — 6sense Credits pool exhausted. Not retryable; a human must top up or enable overage billing.
- `404` — no match on the email/domain. A normal outcome; fall back to unenriched routing.
- `429` — 100 requests/minute per token. Retry with your own backoff; no `Retry-After` is sent.
- `400` — almost always a missing `country` or `email`.

Full catalog: `errors/6sense-problem-types.yml`.

## Credits

A 6sense Credit is consumed only for a **successfully enriched** record. Unmatched records are free. Submit 100, match 80, pay 80.

## Do not

- Do not retry a write blindly — 6sense accepts no idempotency key. These operations are read-shaped so a retry is safe in practice, but nothing in the contract guarantees it.
- Do not put the token in a query string or in browser-side code. These are server-to-server operations and 6sense says so explicitly.
