---
generated: '2026-07-27'
method: generated
name: Bulk-export datasets and the catalogue
description: Pull a whole dataset or the entire 146-dataset catalogue out in CSV, Parquet, GPX, GeoJSON or DCAT-AP RDF, bypassing the record paging ceiling.
api: openapi/electricity-north-west-explore-api-v2-1-openapi.json
operations: [listExportFormats, exportDatasets, exportCatalogCSV, exportCatalogDCAT, listDatasetExportFormats, exportRecords, exportRecordsCSV, exportRecordsParquet, exportRecordsGPX]
source: >-
  Every operationId verified verbatim in
  openapi/electricity-north-west-explore-api-v2-1-openapi.json. Format lists and
  the DCAT-AP response confirmed by live calls on 2026-07-27.
---

# Bulk-export datasets and the catalogue

The records endpoints cap out at `offset + limit` < 10000. The export endpoints
have **no record-count limitation** — this is the correct path for any real data
pull, and it is far cheaper against the shared daily quota than paging.

## Base URL

`https://electricitynorthwest.opendatasoft.com/api/explore/v2.1`

## Auth

- Catalogue-level exports are **anonymous**.
- Dataset record exports are **gated** — same API key as the records skill. See
  `authentication/electricity-north-west-authentication.yml`.

## Steps — exporting one dataset

1. **Discover the formats that dataset supports** — `listDatasetExportFormats`
   (`GET /catalog/datasets/{dataset_id}/exports`). Returns a `links[]` of
   `{rel, href}`, one per available serialisation. Do not assume a format; geo
   formats only appear on geo datasets.

2. **Export** — pick the operation that matches:
   - `exportRecords` (`GET /catalog/datasets/{dataset_id}/exports/{format}`) —
     the general form, for any advertised format including `json`, `xlsx` and
     `geojson`.
   - `exportRecordsCSV` (`.../exports/csv`) — CSV. Note it emits a UTF-8 BOM by
     default in v2.1.
   - `exportRecordsParquet` (`.../exports/parquet`) — Apache Parquet, the right
     choice for anything analytical.
   - `exportRecordsGPX` (`.../exports/gpx`) — geo datasets only. v2.1 exports
     attributes in `<extension>` rather than `<desc>`.

3. **Filter before you export.** The export endpoints accept the same ODSQL
   clauses as the records endpoint, and v2.1 added `group_by` support to exports.
   `select` and `where` on the export call is much better than exporting
   everything and filtering locally.

## Steps — exporting the catalogue

1. **List catalogue formats** — `listExportFormats` (`GET /catalog/exports`).
   Observed live: `csv`, `json`, `data.json`, `rdf`, `ttl`, `dublin_core`, `dcat`,
   `rss`, `sitemap`, `xlsx`.

2. **Export it** — `exportDatasets` (`GET /catalog/exports/{format}`) for the
   general case, `exportCatalogCSV` (`GET /catalog/exports/csv`) for CSV.

3. **Take the standards-based catalogue** — `exportCatalogDCAT`
   (`GET /catalog/exports/dcat{dcat_ap_format}`) returns DCAT-AP as
   `application/rdf+xml`. Verified live on 2026-07-27: HTTP 200, 4,920,757 bytes,
   all 146 datasets. This is the single best artifact for loading the whole
   catalogue into a data-catalogue tool or triple store, and it needs no
   credential.

## Idempotency and retries

All nine operations are `GET`s — safe, idempotent, and freely retryable. A failed
or truncated export can simply be re-requested. See
`conventions/electricity-north-west-conventions.yml`.

## Errors

- **`ForbiddenAccess`** — dataset record exports need an API key. Catalogue
  exports do not.
- **400 `ODSQLError`** — a bad `select`/`where` on the export call. Read the
  dataset's `fields[]` from `getDataset` first.
- **429** — daily domain quota. A large export is one call, so exports are the
  quota-efficient choice; retries of a big export are not.

## Notes

- `robots.txt` disallows `/api/explore/v2*/exports/` to Googlebot. That is a
  crawler instruction, not an access control — it does not affect API clients, but
  it does tell you the provider does not want export URLs indexed.
- Responses are `Cache-Control: no-store`. Persist what you pull; re-pulling costs
  quota.
- Check `metas.default.license` on the dataset before redistributing anything —
  41 of the 146 datasets are under the bespoke "SP ENW Shared Licence", not an
  open licence.
