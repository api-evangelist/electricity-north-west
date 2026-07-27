---
generated: '2026-07-27'
method: generated
name: Query and aggregate network dataset records
description: Get an API key, then query, filter and aggregate records inside an SP Electricity North West dataset with ODSQL.
api: openapi/electricity-north-west-explore-api-v2-1-openapi.json
operations: [getDataset, getRecords, getRecord, getRecordsFacets]
source: >-
  Every operationId verified verbatim in
  openapi/electricity-north-west-explore-api-v2-1-openapi.json. ODSQL semantics and
  the paging ceiling from https://help.opendatasoft.com/apis/ods-explore-v2/;
  the access gate confirmed by live probes on 2026-07-27.
---

# Query and aggregate network dataset records

Read the actual rows — LV headroom, peak demand, embedded capacity, GIS conductor
layers, DFES scenarios — out of a chosen SP Electricity North West dataset.

## Base URL

`https://electricitynorthwest.opendatasoft.com/api/explore/v2.1`

## Auth — required for this skill

Record data on this domain is **gated**. Anonymous calls to the records endpoints
return `{"error_code": "ForbiddenAccess", ...}` even for CC BY 4.0 datasets.

1. Create a free account at
   `https://electricitynorthwest.opendatasoft.com/pages/registration_log_in/`.
2. Generate a key from the "My API keys" tab at
   `https://electricitynorthwest.opendatasoft.com/account/`.
3. Send it as `Authorization: Apikey <API_KEY>`. The `?apikey=<KEY>` query form
   also works but the vendor recommends the header, because query strings persist
   in logs and browser history.

A key inherits the full rights of the user that created it — do not share it. See
`authentication/electricity-north-west-authentication.yml`.

## Steps

1. **Read the field schema first** — `getDataset`
   (`GET /catalog/datasets/{dataset_id}`). Take the `fields[]` array. Every ODSQL
   clause below must use `name` values from it. Skipping this step is the single
   most common cause of a 400.

2. **Query the records** — `getRecords`
   (`GET /catalog/datasets/{dataset_id}/records`). ODSQL clauses:
   - `select` — pick or compute fields, e.g. `select=gsp, bsp, risk_level` or a
     labelled expression `select=capacity * 2 as double_capacity`.
   - `where` — filter, e.g. `where=risk_level="High"`, with `AND`/`OR`/`NOT` and
     the function library (including `within_distance()`, `intersects()`,
     `within()` for geo fields).
   - `order_by` — `order_by=start desc`.
   - `refine` / `exclude` — restrict or drop a facet value.
   - `limit` / `offset` — page size and cursor. **Ceilings:** `limit` ≤ 100
     without a `group_by`, and `offset + limit` < 10000.
   The response is `{total_count, results[], links[]}`. Each result carries the
   dataset's own columns plus the platform fields `_id`, `_timestamp`, `_size`.

3. **Aggregate instead of paging** — the same `getRecords` operation with a
   `group_by` clause plus aggregation functions in `select`
   (e.g. `select=sum(capacity) as total&group_by=gsp`). This is almost always
   cheaper than pulling rows. Note the v2.1 semantics: date functions (`year()`,
   `month()`, …) return integers, null values are grouped, and date aggregation
   keys are ISO strings.

4. **Enumerate facet values** — `getRecordsFacets`
   (`GET /catalog/datasets/{dataset_id}/facets`) to discover the distinct values
   in a column before filtering on it.

5. **Fetch one row** — `getRecord`
   (`GET /catalog/datasets/{dataset_id}/records/{record_id}`) using the `_id` from
   a previous result.

## When to stop querying and start exporting

If you need more than ~10000 rows, the records endpoint cannot serve you — the
`offset + limit` ceiling is a hard wall. Switch to the export skill
(`electricity-north-west-bulk-export.md`); the export endpoints have no
record-count limitation.

## Idempotency and retries

Every operation here is a `GET`. The vendor states "Only the HTTP GET method is
supported", so all four operations are safe and idempotent under RFC 9110 and can
be retried freely — there is no `Idempotency-Key` header because there is nothing
unsafe to deduplicate. The real constraint on retries is quota, not correctness.
See `conventions/electricity-north-west-conventions.yml`.

## Errors

- **`ForbiddenAccess`** — no key, or your account cannot see this dataset. Some
  dataset descriptions say so outright: "Actual dataset content is available to
  registered users only".
- **400 `ODSQLError`** — bad field name or a field used in a clause that rejects
  it. The `message` names the clause. Go back to step 1.
- **401** — missing or invalid credential.
- **429** — `{errorcode: 10002, reset_time, limit_time_unit, call_limit, error}`.
  The quota is per-domain and shared with every other consumer of this portal;
  5000/day was observed anonymously, and authenticated users get an unpublished
  higher ceiling. Back off until `reset_time`.

Full catalogue in `errors/electricity-north-west-problem-types.yml`.

## Notes

- There is no cross-dataset schema. Each of the 146 datasets defines its own
  columns; `gsp`, `bsp`, `mpan`, `postcode` and similar recur but are not
  guaranteed. See `data-model/electricity-north-west-data-model.yml`.
- Watch the `ODS-Explore-API-Deprecation` response header — it warns, per feature,
  that a behaviour will change in the next API version.
