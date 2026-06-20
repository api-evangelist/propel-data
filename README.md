# Propel (propel-data)

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
