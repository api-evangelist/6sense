---
name: 6sense — identify an anonymous website visitor
description: Resolve a visitor IP address to a company, its firmographics, its 6sense buying stage and its segment membership, using the 6sense Company Identification API.
api: openapi/6sense-company-api-openapi.yml
operations:
  - getCompanyDetails
generated: '2026-08-13'
method: generated
source: openapi/6sense-company-api-openapi.yml, https://api.6sense.com/docs/, conventions/6sense-conventions.yml
---

# Identify an anonymous website visitor

Turn an IP address into a named company plus its buying signal. This is the de-anonymization flow behind web personalisation and real-time routing.

## Before you start

- **Host is not `api.6sense.com`.** This operation lives on `https://epsilon.6sense.com`. Getting the host wrong is the most common failure.
- **Token group matters.** You need a *Company Identification API* token. A 6sense Credits or Lead Scoring token will 401 here — tokens are scoped to an API group, not to the whole account.
- **Scores and segments are off by default.** If you need `scores[]` or `segments`, an admin must enable them for that specific token in Settings → API Token management → API Settings. If they come back empty, that is a settings problem, not a data problem.
- **This is the one API 6sense designs for client-side use.** It is invoked by the WebTag in the browser. If you deploy it outside the WebTag, mint a dedicated token and pin it to an allowed-domain list.

## Steps

1. **Call `getCompanyDetails`.**

   `GET https://epsilon.6sense.com/v3/company/details?ip=<visitor ip>`

   Headers:
   - `Authorization: Token <api_token>`
   - `EpsilonCookie: <6sense visitor cookie>` — optional, improves resolution for returning visitors
   - `X-6s-CustomID: <your identifier>` — optional, echoed for your own tracking

   `ip` accepts IPv4 or IPv6 and is required.

2. **Read the match quality before you read anything else.**

   `company.company_match` is one of `Match`, `Non-actionable Match`, `No Match`.

   Only `Match` should drive personalisation. `Non-actionable Match` means 6sense resolved something it will not stand behind (commonly an ISP or a shared network) — check `company.additional_comment` for why. Also check the top-level `confidence` field (`Very High` / `High` / `Moderate` / `Low`).

3. **Do not skip `is_blacklisted`.** A `true` here means the account is on the customer's exclusion list. Suppress it rather than personalising to it.

4. **Read the buying signal from `scores[]`.**

   `scores` is an **array with one entry per product**, not a single score. There is no "the buying stage" for an account — pick the entry whose `product` matches the product you are personalising for.

   Per entry: `buying_stage` (`Purchase` | `Decision` | `Consideration` | `Awareness` | `Target`), `intent_score` (0–100), `profile_fit` (`Strong` | `Moderate` | `Weak`), `profile_score`, and `is_6qa`.

5. **Use `segments.list[]` for routing.** It carries `{id, name}` pairs; match on `id`, not on `name`, which is user-editable in the platform.

## Error handling

Read `errors/6sense-problem-types.yml` for the full catalog. The rules that matter here:

- **`404` is not a failure.** It is the documented *no match* result. Fall back to default content; do not retry, do not alert.
- **`402 Quota Exhausted` is not retryable.** Company Identification burns one API Credit per matched company, and credits are a contract-year pool. A 402 can persist for months. Escalate to a human — retrying or backing off will never clear it.
- **`429` is retryable.** The published limit is 100 requests/minute per token. No `RateLimit-*` or `Retry-After` headers are returned, so back off on your own schedule.
- **`401`** usually means the token is from the wrong API group, not that it is invalid.

Errors come back as `{"status": "error", "message": "..."}` — there is no stable error code, so branch on the HTTP status, never on the message text.

## Cost model

One **matched** company = one API Credit. Repeat lookups of the same IP still consume credits within the contract year, so cache resolutions per IP for the life of the session at minimum.

## Not available

There is no idempotency key, no request-id header, and no way to fetch a company by `companyId` afterwards — this operation is IP-in, company-out only.
