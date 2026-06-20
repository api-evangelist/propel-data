# Propel GraphQL API

GraphQL interface for the [Propel](https://www.propeldata.com/) customer-facing
analytics platform. A single GraphQL endpoint serves both the **Query APIs**
(Counter, Time Series, and Leaderboard analytics over Data Pools) and the
**Admin APIs** (managing Data Sources, Data Pools, Metrics, Applications, and
Policies).

- API docs: <https://www.propeldata.com/docs/api>
- Metrics query docs: <https://www.propeldata.com/docs/query-apis/metrics>
- Admin objects reference: <https://www.propeldata.com/docs/api/admin/objects>
- GitHub: <https://github.com/propeldata>

---

## Endpoint

```
POST https://api.us-east-2.propeldata.com/graphql
Content-Type: application/json
Authorization: Bearer <ACCESS_TOKEN>
```

Propel exposes a single GraphQL endpoint. All queries and mutations are sent as
HTTP `POST` requests with a JSON body of the shape
`{ "query": "...", "variables": { ... } }`.

---

## Authentication (OAuth2 client credentials)

Propel uses the OAuth2 **client credentials** grant. An Application (created in the
Propel Console) carries a `client_id` and `client_secret`. You exchange them at the
token endpoint for a short-lived **Bearer** access token, then send that token on the
`Authorization` header of every GraphQL request.

```
POST https://auth.us-east-2.propeldata.com/oauth2/token
Content-Type: application/x-www-form-urlencoded

grant_type=client_credentials&client_id=<CLIENT_ID>&client_secret=<CLIENT_SECRET>&scope=metric:query
```

Response:

```json
{
  "access_token": "eyJhbGciOi...",
  "token_type": "Bearer",
  "expires_in": 3600
}
```

The `metric:query` scope authorizes querying Metrics. Admin operations use the
Application's broader scopes. OAuth2 client credentials are found in the Propel
Console under your Application's "OAuth2 client credentials" section
(<https://console.propeldata.com/applications/>).

> Note: `us-east-2` is the documented region host. Use the host that matches the
> region your Propel environment is provisioned in.

---

## Core concepts

| Concept | Description |
|---------|-------------|
| **Data Source** | A connection to a warehouse or store Propel reads from — Snowflake, BigQuery, Amazon S3, Redshift, ClickHouse, Postgres, Kafka, or webhooks. |
| **Data Pool** | High-speed storage Propel syncs Data Source data into for sub-second queries. Has a primary timestamp column used to order and partition data and as the time dimension for Metrics. |
| **Metric** | A reusable definition of what to measure (type such as COUNT / SUM / COUNT_DISTINCT / CUSTOM, the measured column, and the dimensions available as filters/group-bys) over a Data Pool. |
| **Application** | The OAuth2 client-credential entity that issues access tokens and carries scopes. |
| **Policy** | A multi-tenant access rule that governs which Metric data an Application or end-customer may query. |

---

## Metric query types

Metrics are queried either by name (a pre-defined Metric, via `metricByName` /
`uniqueName`) or **inline** by pointing at a `dataPool` and supplying the measure
and dimensions in the request. Each Metric supports three query shapes:

- **Counter** — a single aggregated value over a time range. Returns `value`.
- **Time Series** — values bucketed over a time range at a `granularity`
  (`MINUTE`, `HOUR`, `DAY`, `WEEK`, `MONTH`, `YEAR`). Returns parallel
  `labels` and `values` arrays.
- **Leaderboard** — a top-N table: group by one or more `dimensions`, `sort` by
  the measure, and cap with `rowLimit`. Returns `headers` and `rows`.

Time-range inputs accept relative ranges (e.g. `LAST_N_DAYS`, `PREVIOUS_MONTH`,
`TODAY`) or explicit `start`/`stop` timestamps; if omitted, the Metric's Data Pool
min/max timestamps are used.

See [`propel-data-schema.graphql`](./propel-data-schema.graphql) for a representative
SDL subset.

---

## Query examples

### Counter — total of a Metric over the last 30 days

```graphql
query Counter {
  counter(
    input: {
      metricName: "total_sales"
      timeRange: { relative: LAST_N_DAYS, n: 30 }
      filters: [{ column: "region", operator: EQUALS, value: "us-east" }]
    }
  ) {
    value
  }
}
```

### Time Series — daily values for the last 90 days

```graphql
query TimeSeries {
  timeSeries(
    input: {
      metricName: "total_sales"
      timeRange: { relative: LAST_N_DAYS, n: 90 }
      granularity: DAY
    }
  ) {
    labels
    values
  }
}
```

### Leaderboard — top 10 salespeople

```graphql
query Leaderboard {
  leaderboard(
    input: {
      metricName: "total_sales"
      timeRange: { relative: LAST_N_DAYS, n: 30 }
      dimensions: [{ columnName: "salesperson" }]
      sort: DESC
      rowLimit: 10
    }
  ) {
    headers
    rows
  }
}
```

### Inline Metric over a Data Pool (no pre-defined Metric)

```graphql
query InlineCounter {
  counter(
    input: {
      metric: {
        dataPool: { name: "sales_pool" }
        measure: { sum: { column: "amount" } }
      }
      timeRange: { relative: PREVIOUS_MONTH }
    }
  ) {
    value
  }
}
```

---

## Mutation examples (Admin API)

### Create a Data Source (Snowflake)

```graphql
mutation CreateDataSource {
  createSnowflakeDataSource(
    input: {
      uniqueName: "snowflake-prod"
      connectionSettings: {
        account: "xy12345"
        database: "ANALYTICS"
        warehouse: "PROPEL_WH"
        schema: "PUBLIC"
        role: "PROPEL_ROLE"
        username: "propel"
        password: "<secret>"
      }
    }
  ) {
    dataSource { id uniqueName status }
  }
}
```

### Create a Data Pool

```graphql
mutation CreateDataPool {
  createDataPoolV2(
    input: {
      dataSource: { id: "DSO00000000000000000" }
      table: "SALES"
      timestamp: { columnName: "ordered_at" }
      uniqueName: "sales_pool"
    }
  ) {
    dataPool { id uniqueName status }
  }
}
```

### Create a Metric

```graphql
mutation CreateMetric {
  createSumMetric(
    input: {
      uniqueName: "total_sales"
      dataPool: { id: "DPO00000000000000000" }
      measure: { columnName: "amount" }
      dimensions: [{ columnName: "region" }, { columnName: "salesperson" }]
    }
  ) {
    metric { id uniqueName type }
  }
}
```

### Create an Application

```graphql
mutation CreateApplication {
  createApplication(
    input: {
      uniqueName: "dashboard-app"
      scopes: [METRIC_QUERY, ADMIN]
      propeller: P1_X_SMALL
    }
  ) {
    application { id uniqueName clientId scopes }
  }
}
```

### Create a Policy (multi-tenant access)

```graphql
mutation CreatePolicy {
  createPolicy(
    input: {
      metric: { id: "MET00000000000000000" }
      application: { id: "APP00000000000000000" }
      type: TENANT_ACCESS
    }
  ) {
    policy { id type }
  }
}
```

---

## Notes

- This document and the accompanying SDL are a **representative** model of Propel's
  public GraphQL surface assembled from the published documentation; consult the live
  schema introspection and the [Admin objects reference](https://www.propeldata.com/docs/api/admin/objects)
  for the authoritative, complete types, exact field names, and enum values.
- The transport is GraphQL-over-HTTP (`POST /graphql`). Propel does not document a
  GraphQL `subscription`/streaming surface; analytics are served via request/response
  Query APIs.
