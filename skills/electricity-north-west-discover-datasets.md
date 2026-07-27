---
generated: '2026-07-27'
method: generated
name: Discover SP Electricity North West open datasets
description: Search the 146-dataset catalogue, filter it by licence or theme, and read a dataset's field schema before querying it.
api: openapi/electricity-north-west-explore-api-v2-1-openapi.json
operations: [getDatasets, getDatasetsFacets, getDataset, getDatasetAttachments]
source: >-
  Every operationId verified verbatim in
  openapi/electricity-north-west-explore-api-v2-1-openapi.json. Behaviour grounded
  in conventions/electricity-north-west-conventions.yml,
  errors/electricity-north-west-problem-types.yml and live probes on 2026-07-27.
---

# Discover SP Electricity North West open datasets

Find the right dataset in the SP Electricity North West open data catalogue and
learn its schema. This is the prerequisite skill — do not attempt a records query
until you have run step 3.

## Base URL

`https://electricitynorthwest.opendatasoft.com/api/explore/v2.1`

## Auth

None needed for anything in this skill. Catalogue and dataset metadata are
readable anonymously. See `authentication/electricity-north-west-authentication.yml`.

## Steps

1. **Search the catalogue** — `getDatasets` (`GET /catalog/datasets`). Use ODSQL:
   `where` for full-text and boolean filtering, `select` to trim the response,
   `order_by` to sort, `limit`/`offset` to page. `limit` maxes out at 100 without a
   `group_by`, and `offset + limit` must stay under 10000. The response is
   `{total_count, results[], links[]}`; `total_count` was 146 on 2026-07-27.

2. **Narrow with facets** — `getDatasetsFacets` (`GET /catalog/facets`). Pass
   `facet=license` to see the licence split (CC BY 4.0 = 96, SP ENW Shared Licence
   = 41, Open Government Licence v3.0 = 8), or `facet=theme` / `facet=keyword` to
   slice by subject. Feed a chosen value back into `getDatasets` as `refine=license:CC BY 4.0`.

3. **Read the dataset's schema** — `getDataset`
   (`GET /catalog/datasets/{dataset_id}`). **This step is mandatory before any
   ODSQL against records.** The response `fields[]` array is the only source of
   valid field names for that dataset — each entry gives `name` (what ODSQL uses),
   `label`, and `type` (`text`, `int`, `double`, `date`, `datetime`,
   `geo_point_2d`, `geo_shape`, `file`). Also read `metas.default.license` before
   you reuse the data, and `has_records` / `data_visible` to know whether records
   are available to you.

4. **Check for attachments** — `getDatasetAttachments`
   (`GET /catalog/datasets/{dataset_id}/attachments`). Some datasets ship source
   spreadsheets or methodology PDFs that are not in the records.

## Conventions

- Every response carries a `links[]` array of `{rel, href}`. `rel: self` is the
  canonical URL, `rel: source` walks back up the hierarchy.
- Responses are `Cache-Control: no-store`. There is no ETag; do not rely on
  conditional requests.
- CORS is fully open (`Access-Control-Allow-Origin: *`), so this works from a
  browser with no proxy.

## Errors

- **400 `ODSQLError`** — you named a field that does not exist, or used a field in
  a clause that does not accept it (`data_visible` is selectable but not
  filterable). The `message` names the offending clause. Re-read step 3.
- **429** — a domain-wide daily quota, 5000 calls/day observed anonymously. Read
  `X-RateLimit-Remaining` proactively; the reset is midnight UTC. See
  `rate-limits/electricity-north-west-rate-limits.yml`.

## Notes

- Dataset ids are slugs. Most carry an `sp-enw-` prefix after the 2025 Iberdrola
  rebrand (`sp-enw-gis-conductors-trafford`); older ids are unprefixed
  (`enwl_control_boundary`, `lv_load_duration`). Search on both.
- 41 of the 146 datasets sit under a bespoke "SP ENW Shared Licence" that is not an
  open licence. Always check `metas.default.license` before redistributing.
