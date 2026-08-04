# Electricity North West (electricity-north-west)

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
> **On a security or compliance team?** Email
> [info@apievangelist.com](mailto:info@apievangelist.com) with *security* in the subject line and
> you will get a person, not a form. We will tell you exactly which public URLs this profile was
> built from so your team can see the same surface we did, and we will take the listing down on
> request while you work through it.
>
> Full detail: **[Where this data comes from](https://apievangelist.com/about/where-our-data-comes-from)**
<!-- API-EVANGELIST-PROVENANCE:END -->

Electricity North West — rebranded SP Electricity North West in August 2025 after Iberdrola acquired it and folded it in alongside SP Energy Networks — is the regulated electricity distribution network operator for the North West of England, running roughly 13,000 km of overhead line and more than 44,000 km of underground cable from Cumbria to Manchester. It is a poles-and-wires business in the regulated middle of the United Kingdom value chain: it owns the meter point and the network, it earns a regulated revenue under Ofgem's RIIO-ED2 price control, and it never bills the household — the supplier does.

Its API posture is a clean split. On the **market-data** side it is genuinely API-native for a network operator: an Opendatasoft-hosted open data portal carrying 146 datasets, served through the documented Explore REST API v2.1 (and legacy v2.0) with a real OpenAPI 3.0.3 contract, a DCAT-AP catalogue export, and an in-portal API console. On the **consumer-data** side there is nothing — and no UK mandate requires there to be. The United Kingdom has no consumer energy data-portability right equivalent to Australia's Consumer Data Right; Great Britain's smart-meter mandate produced infrastructure (the licensed Smart DCC) rather than a data right; Green Button has no UK footprint.

**APIs.json:** [https://raw.githubusercontent.com/api-evangelist/electricity-north-west/refs/heads/main/apis.yml](https://raw.githubusercontent.com/api-evangelist/electricity-north-west/refs/heads/main/apis.yml)

## Tags

- Energy
- United Kingdom
- Utilities
- Electricity
- Grid
- Distribution Network
- Open Data
- DER
- Renewables
- Energy Markets
- Smart Metering

## Timestamps

- **Created:** 2026-07-27
- **Modified:** 2026-07-27

## APIs

### SP Electricity North West Open Data Explore API v2.1

The current Opendatasoft Explore REST API v2.1 scoped to the SP Electricity North West open data domain. Read-only (GET only, JSON), 16 documented paths covering catalogue search over the 146 published datasets, per-dataset metadata and field schemas, record query, facets, attachments, and bulk exports in CSV, JSON, Parquet, GPX and DCAT-AP. All endpoints accept the Opendatasoft Query Language (ODSQL). The OpenAPI 3.0.3 document was harvested verbatim from the live host on 2026-07-27 and declares a single `apikey` security scheme; an API key is issued from a free self-serve portal account.

- **Human URL:** [https://electricitynorthwest.opendatasoft.com/api](https://electricitynorthwest.opendatasoft.com/api)
- **Base URL:** `https://electricitynorthwest.opendatasoft.com/api/explore/v2.1`

#### Tags

- Open Data
- Catalog
- Records
- Exports
- DCAT
- Energy

#### Properties

- [OpenAPI](openapi/electricity-north-west-explore-api-v2-1-openapi.json) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [API Reference](https://electricitynorthwest.opendatasoft.com/api-console/explore/v2.1/)
- [Documentation](https://help.huwise.com/apis/ods-explore-v2/)
- [Portal](https://electricitynorthwest.opendatasoft.com/api)
- [Data](https://electricitynorthwest.opendatasoft.com/explore)

### SP Electricity North West Open Data Explore API v2.0

The previous-generation Opendatasoft Explore REST API v2.0, still served on the SP Electricity North West domain alongside v2.1. Same 16-path read-only shape — catalogue, dataset metadata, records, facets, attachments and CSV/JSON/Parquet/GPX exports — against the same 146 datasets. Retained here because it is a distinct live base URL with its own OpenAPI 3.0.3 contract, harvested verbatim on 2026-07-27.

- **Human URL:** [https://electricitynorthwest.opendatasoft.com/api](https://electricitynorthwest.opendatasoft.com/api)
- **Base URL:** `https://electricitynorthwest.opendatasoft.com/api/explore/v2.0`

#### Tags

- Open Data
- Catalog
- Records
- Exports
- Energy

#### Properties

- [OpenAPI](openapi/electricity-north-west-explore-api-v2-0-openapi.json) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Documentation](https://help.huwise.com/apis/ods-explore-v2/)
- [Portal](https://electricitynorthwest.opendatasoft.com/api)

## Common Properties

- [Website](https://www.enwl.co.uk/)
- [Blog](https://news.enwl.co.uk/)
- [LinkedIn](https://www.linkedin.com/company/electricity-north-west)
- [Portal](https://electricitynorthwest.opendatasoft.com/)
- [Documentation](https://electricitynorthwest.opendatasoft.com/api)
- [Data](https://electricitynorthwest.opendatasoft.com/explore)
- [Data — DCAT-AP catalogue](https://electricitynorthwest.opendatasoft.com/api/explore/v2.1/catalog/exports/dcat)
- [Registration](https://electricitynorthwest.opendatasoft.com/pages/registration_log_in/)
- [Regulator — Ofgem Data Best Practice Guidance](https://www.ofgem.gov.uk/sites/default/files/2024-10/Track_Changes_Data_Best_Practice_Guidance_v301728394292260.pdf)

## Mandate Posture

| Question | Answer |
| --- | --- |
| Mandate regime | `other` — Ofgem Data Best Practice Guidance under the RIIO-ED2 digitalisation licence condition ("presumed open") |
| Mandate status | `live-implemented` — verified by a live OpenAPI 3.0.3 contract, a 146-dataset catalogue and a 4.9 MB DCAT-AP export, all served anonymously on 2026-07-27 |
| Data standard | Opendatasoft Explore API v2.1 (OpenAPI 3.0.3) + DCAT-AP; no Green Button / ESPI / CDR / OCPP / OpenADR / IEEE 2030.5 / IEC CIM reference found |
| Consumer data API | No — the UK has no consumer energy data right, and the distributor does not hold the retail relationship |
| Market data open | Yes — 146 datasets, 96 CC BY 4.0 and 8 Open Government Licence v3.0 (41 under a bespoke "SP ENW Shared Licence") |
| Access gate | `self-serve` — free portal account, then an API key; catalogue and DCAT are anonymous, record/export data is not |
| Auth model | API key (single `apikey` security scheme in both OpenAPI documents); no OAuth2, no OIDC, no mTLS |
| Home market | United Kingdom |

See [`review.yml`](review.yml) for every URL probed, its HTTP status, and the evidence behind each answer above.

## Maintainers

- Kin Lane — kin@apievangelist.com
