# Propel (propel-data)

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

Propel is a customer-facing analytics platform that puts a fast GraphQL analytics API in front of a data warehouse. Teams connect a Data Source (Snowflake, BigQuery, S3, Redshift, ClickHouse, Postgres, Kafka, webhooks), sync it into high-speed Data Pools, define Metrics, and serve sub-second Counter, Time Series, and Leaderboard queries to in-product dashboards, with multi-tenant Policies and OAuth2 Applications for access control.

**APIs.json:** [https://raw.githubusercontent.com/api-evangelist/propel-data/refs/heads/main/apis.yml](https://raw.githubusercontent.com/api-evangelist/propel-data/refs/heads/main/apis.yml)

## Tags

- Analytics
- GraphQL
- Data Warehouse
- Metrics
- Customer Facing Analytics

## Timestamps

- **Created:** 2026-06-20
- **Modified:** 2026-06-20

## APIs

### Propel Metrics Queries API

GraphQL query surface for analytics over Data Pools - Counter (single aggregated value), Time Series (values over a time range at a granularity), and Leaderboard (top-N grouped by dimensions) queries, run against a pre-defined Metric by uniqueName or against an inline Metric over a Data Pool.

- **Human URL:** [https://www.propeldata.com/docs/query-apis/metrics](https://www.propeldata.com/docs/query-apis/metrics)
- **Base URL:** `https://api.us-east-2.propeldata.com/graphql`

#### Tags

- Metrics
- Queries
- Analytics
- GraphQL

#### Properties

- [Documentation](https://www.propeldata.com/docs/query-apis/metrics)
- [API Reference](https://www.propeldata.com/docs/api)
- [OpenAPI](openapi/propel-data-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [GraphQL](graphql/propel-data-graphql.md) — [GraphQL Specification](https://spec.graphql.org/)
- [Postman Collection](collections/propel-data.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/propel-data.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Propel Data Pools API

Admin operations for Data Pools - the high-speed storage Propel syncs warehouse data into, with a primary timestamp column for ordering and partitioning. Create, read, list, update, and delete Data Pools and inspect their columns and sync status via GraphQL mutations and queries.

- **Human URL:** [https://www.propeldata.com/docs/api/admin/objects](https://www.propeldata.com/docs/api/admin/objects)
- **Base URL:** `https://api.us-east-2.propeldata.com/graphql`

#### Tags

- Data Pools
- Storage
- GraphQL

#### Properties

- [Documentation](https://www.propeldata.com/docs/data-pools)
- [API Reference](https://www.propeldata.com/docs/api/admin/objects)
- [OpenAPI](openapi/propel-data-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [GraphQL](graphql/propel-data-graphql.md) — [GraphQL Specification](https://spec.graphql.org/)
- [Postman Collection](collections/propel-data.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/propel-data.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Propel Data Sources API

Admin operations for Data Sources - the connections to warehouses and stores Propel reads from (Snowflake, BigQuery, Amazon S3, Redshift, ClickHouse, Postgres, Kafka, and webhooks). Create, introspect tables, test the connection, and manage the lifecycle via GraphQL.

- **Human URL:** [https://www.propeldata.com/docs/api/admin/objects](https://www.propeldata.com/docs/api/admin/objects)
- **Base URL:** `https://api.us-east-2.propeldata.com/graphql`

#### Tags

- Data Sources
- Connectors
- GraphQL

#### Properties

- [Documentation](https://www.propeldata.com/docs/data-sources)
- [API Reference](https://www.propeldata.com/docs/api/admin/objects)
- [OpenAPI](openapi/propel-data-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [GraphQL](graphql/propel-data-graphql.md) — [GraphQL Specification](https://spec.graphql.org/)
- [Postman Collection](collections/propel-data.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/propel-data.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Propel Applications and Policies API

Admin operations for Applications (the OAuth2 client-credential entities that issue access tokens and carry scopes) and Policies (the multi-tenant access rules that govern which Metric data an Application or end-customer can query), managed via GraphQL mutations and queries.

- **Human URL:** [https://www.propeldata.com/docs/applications](https://www.propeldata.com/docs/applications)
- **Base URL:** `https://api.us-east-2.propeldata.com/graphql`

#### Tags

- Applications
- Policies
- Access Control
- GraphQL

#### Properties

- [Documentation](https://www.propeldata.com/docs/applications)
- [API Reference](https://www.propeldata.com/docs/api/admin/objects)
- [OpenAPI](openapi/propel-data-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [GraphQL](graphql/propel-data-graphql.md) — [GraphQL Specification](https://spec.graphql.org/)
- [Postman Collection](collections/propel-data.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/propel-data.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Propel OAuth2 Token API

OAuth2 client-credentials token endpoint. Applications exchange a client_id and client_secret for a short-lived Bearer access token (for example with the metric:query scope) that is then sent on the Authorization header to the GraphQL API.

- **Human URL:** [https://www.propeldata.com/docs/api/authentication](https://www.propeldata.com/docs/api/authentication)
- **Base URL:** `https://auth.us-east-2.propeldata.com/oauth2/token`

#### Tags

- OAuth2
- Authentication
- Access Tokens

#### Properties

- [Documentation](https://www.propeldata.com/docs/api/authentication)
- [OpenAPI](openapi/propel-data-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [GraphQL](graphql/propel-data-graphql.md) — [GraphQL Specification](https://spec.graphql.org/)

## Common Properties

- [GitHub Organization](https://github.com/propeldata)
- [LinkedIn](https://www.linkedin.com/company/propeldata)
- [Website](https://www.propeldata.com)
- [Documentation](https://www.propeldata.com/docs)
- [Plans](plans/propel-data-plans-pricing.yml)
- [Rate Limits](rate-limits/propel-data-rate-limits.yml)
- [Fin Ops](finops/propel-data-finops.yml)

## Maintainers

**FN:** Kin Lane
**Email:** kin@apievangelist.com
