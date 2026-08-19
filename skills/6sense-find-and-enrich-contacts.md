---
name: 6sense — find contacts at an account and enrich them
description: Search for the right people at a target company, then exchange their people IDs for real contact details in a batch, without wasting enrichment credits.
api: openapi/6sense-people-api-openapi.yml
operations:
  - getSearchDictionary
  - searchPeople
  - enrichPeople
generated: '2026-08-13'
method: generated
source: openapi/6sense-people-api-openapi.yml, openapi/6sense-enrichment-api-openapi.yml, https://api.6sense.com/docs/
---

# Find contacts at an account, then enrich them

This is the only genuine two-step id flow in the 6sense estate, and it is designed so that searching is free and only the details cost money. Run it in order or you will overpay.

## Steps

1. **Load the filter dictionary once, and cache it.**

   `GET https://api.6sense.com/v2/people/search/dictionary` → `getSearchDictionary`

   Returns the valid values for job title, job function, job level, industry and the other facets, as a map of facet name to string array. Filter values are **not** free text — sending a job level 6sense does not recognise silently narrows your result set to nothing rather than erroring. Fetch this at startup, not per search.

2. **Search by domain.**

   `POST https://api.6sense.com/v2/people/search` → `searchPeople`, `Content-Type: application/json`

   ```json
   { "domain": "acme.com", "jobFunction": "Marketing", "jobLevel": "VP", "location": "United States", "limit": 25 }
   ```

   `domain` is the only required field. Everything else narrows.

3. **Read `people[]` as summaries, not contacts.**

   Each `PersonSummary` gives you `id`, name, `jobTitle`, `jobFunction`, `jobLevel`, `location`, `linkedinUrl` — and crucially `hasEmail`, `hasPhone`, `hasMobilePhone` as **booleans**. The actual email and phone are deliberately withheld.

   `totalResults` tells you how many matched overall.

   **This step consumes no credits.** Filter hard here.

4. **Only enrich the people you actually want.**

   Discard anyone whose `hasEmail` is `false` if you need an email — enriching them will not conjure one, and you may still pay for the record.

   `POST https://api.6sense.com/v2/enrichment/people` → `enrichPeople`, `Content-Type: application/json`

   The body is a **bare JSON array**, maximum **25 items**:

   ```json
   [
     { "peopleId": "<PersonSummary.id>", "referenceKeys": { "crmId": "003xx0000001" } },
     { "email": "jane@acme.com", "referenceKeys": { "crmId": "003xx0000002" } }
   ]
   ```

   Each item needs at least one of `peopleId`, `email` or `linkedInUrl`.

5. **Correlate on `referenceKeys`, never on array position.**

   The response is `{ "contacts": [...] }` and each `EnrichedContact` echoes back the `referenceKeys` you sent. No ordering guarantee is documented, and unmatched records may not come back at all. Always send a `referenceKeys` map carrying your own primary key.

6. **Grade the email before you use it.** `emailConfidence` is `A+`, `A`, `B` or `C`. Route `A+`/`A` to outbound; treat `C` as a guess.

## Rate limits — this one is different

`enrichPeople` is limited to **20 requests per second**, not the 100/minute that governs the rest of the estate. With 25 records per request that is 500 records/second, but it also means a naive per-record loop will hit the limit far sooner than you expect. Batch to 25.

`searchPeople` follows the standard 100 requests/minute.

## Credits

- `searchPeople` and `getSearchDictionary`: **no credits**.
- `enrichPeople`: **1 6sense Credit per successfully enriched record.** Unmatched records are free.

Submitting 100 and matching 80 costs 80 credits. This is why step 3 filtering matters.

## Error handling

- `422` — validation error on the batch. Check that every item carries one of the three accepted identifiers and that the array is ≤ 25.
- `402` — 6sense Credits exhausted. Not retryable; escalate.
- `429` — you exceeded 20 QPS. Back off; no `Retry-After` is sent.

Full catalog: `errors/6sense-problem-types.yml`.

## Privacy

`EnrichedContact` is personal data. 6sense gates access contractually and propagates opt-out and deletion requests downstream to customers, who are required to delete on receipt. Do not persist these records outside the systems named in your contract, and honour the opt-out list. See `conformance/6sense-conformance.yml`.
