# Electricity North West

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

Electricity North West — rebranded SP Electricity North West in August 2025 after Iberdrola acquired it and folded it in alongside SP Energy Networks — is the regulated electricity distribution network operator for the North West of England, running roughly 13,000 km of overhead line and more than 44,000 km of underground cable from Cumbria to Manchester. It is a poles-and-wires business in the regulated middle of the United Kingdom value chain: it owns the meter point and the network, it earns a regulated revenue under Ofgem's RIIO-ED2 price control, and it never bills the household — the supplier does. Its API posture is a clean split and worth stating plainly. On the MARKET-DATA side it is genuinely API-native for a network operator: it runs an Opendatasoft-hosted open data portal at electricitynorthwest.opendatasoft.com carrying 146 datasets — embedded capacity register, DFES scenarios, LV headroom and peak demand, network capacity heatmaps, GSP connection queue, GIS conductor and substation layers — served through the documented Opendatasoft Explore REST API v2.1 (and legacy v2.0) with a real OpenAPI 3.0.3 contract, a DCAT-AP catalogue export, and an in-portal API console. 96 of those datasets are CC BY 4.0 and 8 are Open Government Licence v3.0, but 41 sit under a bespoke "SP ENW Shared Licence" rather than an open one. On the CONSUMER-DATA side there is nothing: the United Kingdom has no consumer energy data-portability right equivalent to Australia's Consumer Data Right, Great Britain's smart-meter mandate produced infrastructure (the licensed Smart DCC) rather than a data right, Green Button has no UK footprint, and Electricity North West publishes no customer usage or billing API of any kind. The obligation that actually binds it is Ofgem's Data Best Practice Guidance under the RIIO-ED2 digitalisation licence condition — an open-data duty, not a consumer data right — and the portal is a real, verifiable implementation of it. Note that the corporate site www.enwl.co.uk sits behind a Cloudflare managed challenge and returns HTTP 403 to every non-browser client, so no part of the main website is machine-readable.

**Areas:** Energy · United Kingdom · Utilities · Electricity · Grid · Distribution Network · Open Data · DER · Renewables · Energy Markets · Smart Metering

## Electricity North West on APIs.io

Everything profiled for Electricity North West is published on APIs.io rather than in this repository. Start at the provider page — **[apis.io/providers/electricity-north-west/](https://apis.io/providers/electricity-north-west/)** — or go straight to one of the APIs or properties below.

### APIs (2)

- [Electricity North West Catalog API](https://apis.io/apis/electricity-north-west/electricity-north-west-catalog-api/) — API to enumerate datasets
- [Electricity North West Dataset API](https://apis.io/apis/electricity-north-west/electricity-north-west-dataset-api/) — API to work on records

### Published properties

Each property below is a page on APIs.io carrying the machine-readable artifact and what it says.

#### MCP servers (1)

Model Context Protocol servers that expose the API to agents.

- [electricity-north-west](https://apis.io/servers/electricity-north-west/electricity-north-west/)

#### Examples (6)

Example requests and responses.

- [Electricity North West Catalog Facets License Example](https://apis.io/examples/electricity-north-west/electricity-north-west-catalog-facets-license-example/)
- [Electricity North West Forbidden Records Example](https://apis.io/examples/electricity-north-west/electricity-north-west-forbidden-records-example/)
- [Electricity North West Get Dataset Example](https://apis.io/examples/electricity-north-west/electricity-north-west-get-dataset-example/)
- [Electricity North West List Datasets Example](https://apis.io/examples/electricity-north-west/electricity-north-west-list-datasets-example/)
- [Electricity North West List Export Formats Example](https://apis.io/examples/electricity-north-west/electricity-north-west-list-export-formats-example/)
- [Electricity North West Odsql Error Example](https://apis.io/examples/electricity-north-west/electricity-north-west-odsql-error-example/)

#### Collections (2)

Postman and Open Collection request collections.

- [Explore API](https://apis.io/collections/electricity-north-west/open-electricity-north-west-explore-api-v2-0/)
- [Explore API](https://apis.io/collections/electricity-north-west/open-electricity-north-west-explore-api-v2-1/)

#### Overlays (2)

OpenAPI overlays, including conversational phrasing for each operation.

- [Electricity North West Explore Api V2 0 Overlay](https://apis.io/overlays/electricity-north-west/electricity-north-west-explore-api-v2-0-overlay/)
- [Electricity North West Explore Api V2 1 Overlay](https://apis.io/overlays/electricity-north-west/electricity-north-west-explore-api-v2-1-overlay/)

#### Security (3)

Authentication, trust centre, and vulnerability disclosure.

- [Electricity North West Authentication](https://apis.io/security/electricity-north-west/electricity-north-west-authentication/)
- [Electricity North West Domain Security](https://apis.io/security/electricity-north-west/electricity-north-west-domain-security/)
- [Electricity North West Vulnerability Disclosure](https://apis.io/security/electricity-north-west/electricity-north-west-vulnerability-disclosure/)

#### OAuth scopes (1)

The permissions the API asks for.

- [Electricity North West Scopes](https://apis.io/scopes/electricity-north-west/electricity-north-west-scopes/)

#### Rate limits (1)

Published request limits.

- [Electricity North West Rate Limits](https://apis.io/rate-limits/electricity-north-west/electricity-north-west-rate-limits/)

## Where to find this API

Links to the company's own pages. This repository publishes no copy of their specifications — the canonical document is theirs and lives at the URLs below.

- [Website](https://www.enwl.co.uk/)
- [Documentation](https://electricitynorthwest.opendatasoft.com/api)
- [Getting started](https://help.huwise.com/apis/ods-explore-v2/#section/Getting-Started)
- [API reference](https://help.huwise.com/apis/ods-explore-v2/)
- [Sign up](https://electricitynorthwest.opendatasoft.com/pages/registration_log_in/)
- [Blog](https://news.enwl.co.uk/)
- [Security](https://www.huwise.com/en/security/)
- [Terms of service](https://www.enwl.co.uk/about-us/terms-and-conditions/)
- [Privacy policy](https://www.enwl.co.uk/misc/privacy-policy/)
- [GitHub](https://github.com/spenw-open-data)
- [Status](https://status.huwise.com/)

## API Evangelist rating

**Kin Score 59.6** — strong · rubric 0.25.0 · scored 2026-10-23

| Facet | Score |
|---|---|
| Discoverability | 73.2 |
| Contract quality | 54.2 |
| Contract governance | 4.5 |
| Operational transparency | 84.2 |
| Developer ergonomics | 77.5 |
| Access clarity | 34.2 |

**Agent readiness 33.0** — agent-ready

| Agent-readiness dimension | Result |
|---|---|
| Spec Presence | yes |
| Agentic Access | — |
| Reversibility Documented | na |
| MCP Server | — |
| Auth Clarity | bearer (partial credit) |
| Idempotency | na |
| Error Semantics | derived (partial credit) |
| OpenAPI Examples | verified |
| Rate Limit Signal | documented (partial credit) |
| Event Surface Described | — |
| Agent Skills | derived (partial credit) |
| Well Known Catalog | — |
| Consent Identity | — |
| Agent Card | — |
| Dry Run Mode | na |
| Delegated Identity | — |
| Protected Resource Metadata | — |
| Dynamic Client Registration | — |
| Agentic Commerce | — |
| Pagination Ratio | paginated |
| Operation Distinctiveness | distinct |

**Regulatory alignment 45.9** — Energy & Utilities

The rubric is published at [github.com/api-evangelist/kin-score](https://github.com/api-evangelist/kin-score). The per-check breakdown behind these numbers — which checks were earned, partial or missed — along with score history and how this provider compares to its peers, is available at [apis.io/providers/electricity-north-west/](https://apis.io/providers/electricity-north-west/).

## How this profile is made

API Evangelist profiles a company's public API surface the way a developer would find it: the website, developer portal and documentation, the specifications it publishes, its public repositories, and its pricing, status and changelog pages. From that it derives the properties above — contracts split per API, workflows, schemas, collections, governance rules, plans and rate limits — and scores them against the published [Kin Score rubric](https://github.com/api-evangelist/kin-score).

The artifacts are published on [APIs.io](https://apis.io), not in this repository. This repository is the public record for Electricity North West: the place to say something is wrong, missing or out of date, and to ask for a re-score or a removal.

## Open an issue

- **Something about this listing** — a wrong description, a missing API, a stale artifact or a question about the rating: [open an issue on this repository](https://github.com/api-evangelist/electricity-north-west/issues/new).
- **A new API, or one that is not in the catalog yet** — [submit it on APIs.io](https://apis.io/add/).
- **Anything else** — [the APIs.io inbox](https://github.com/api-search/inbox/issues/new) or [info@apievangelist.com](mailto:info@apievangelist.com).
