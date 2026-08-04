# Chroma (chroma-db)

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

Chroma (Chroma DB) is an open-source, AI-native **vector database** (embedding database) for building LLM, RAG, and semantic-search applications. It provides storage, indexing, and retrieval for **vector embeddings** with metadata filtering, full-text and regex search, and multi-modal retrieval across text, images, and audio. Chroma is Apache-2.0 licensed.

## Access Model

Chroma ships in two deployment models that share one HTTP/REST **v2 API**:

- **Open-source, self-hosted.** Run the Chroma server yourself (a single server, default port `8000`; `github.com/chroma-core/chroma`). Base URL is `http://your-host:8000`. Authentication is optional and set by the operator - the server can run open (no auth) or be configured with a static token (carried in `x-chroma-token`, or `Authorization: Bearer`) or HTTP basic auth.
- **Chroma Cloud.** A managed, serverless, usage-based offering. Base URL is `https://api.trychroma.com`. An **API key is required**, passed in the `x-chroma-token` header, and the tenant and database names come from your Cloud instance.

Both surfaces expose the same v2 resource hierarchy - **tenants → databases → collections → records (embeddings)** - and the same operations: create/list/get/update/delete collections, add/upsert/update/get/delete/count records, and `query` for nearest-neighbor **vector similarity search**. The Python, JavaScript/TypeScript, Rust, and other client libraries wrap this same REST API. A running server also serves its own generated OpenAPI at `/openapi.json`.

> Endpoint honesty note: the `query` endpoint (method, path, request body, and `x-chroma-token` auth) is confirmed against the official Chroma reference docs. The remaining endpoints follow Chroma's documented v2 path structure and client operations, but the request/response **JSON schemas in the OpenAPI here are modeled** by API Evangelist and should be verified against your server's `/openapi.json`. See `review.yml` for the confirmed-vs-modeled breakdown.

**APIs.json:** [https://raw.githubusercontent.com/api-evangelist/chroma-db/refs/heads/main/apis.yml](https://raw.githubusercontent.com/api-evangelist/chroma-db/refs/heads/main/apis.yml)

## Tags

- Vector Database
- Vector Index
- Vector Search
- Vector Store
- Embeddings
- Similarity Search
- RAG
- Semantic Search
- AI
- AI Inference
- Machine Learning
- Open Source

## Timestamps

- **Created:** 2026-07-12
- **Modified:** 2026-07-12

## APIs

### Chroma Collections API

Create, list, get, update, count, and delete collections - the named vector stores that hold embeddings and their metadata. Collections are scoped to a tenant and database and carry an embedding function, index configuration, and distance metric.

- **Human URL:** [https://docs.trychroma.com/reference/chroma-reference](https://docs.trychroma.com/reference/chroma-reference)
- **Base URL:** `https://api.trychroma.com`

#### Tags

- Vector Database
- Vector Store
- Collections

#### Properties

- [Documentation](https://docs.trychroma.com/docs/collections/manage-collections)
- [API Reference](https://docs.trychroma.com/reference/chroma-reference)
- [OpenAPI](openapi/chroma-db-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/chroma-db.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/chroma-db.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Chroma Records (Embeddings) API

Write and manage the records (embeddings) inside a collection - add, upsert, update, get, count, and delete vectors along with their documents, metadata, and URIs. Records can be indexed with client-provided embeddings or generated by the collection's embedding function.

- **Human URL:** [https://docs.trychroma.com/reference/chroma-api/record/add-records](https://docs.trychroma.com/reference/chroma-api/record/add-records)
- **Base URL:** `https://api.trychroma.com`

#### Tags

- Embeddings
- Vector Index
- Records

#### Properties

- [Documentation](https://docs.trychroma.com/docs/collections/add-data)
- [API Reference](https://docs.trychroma.com/reference/chroma-api/record/add-records)
- [OpenAPI](openapi/chroma-db-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/chroma-db.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/chroma-db.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Chroma Query and Similarity Search API

Run nearest-neighbor vector similarity search over a collection with query embeddings, plus metadata (`where`) and full-text (`where_document`) filters, returning the closest records with configurable included fields (distances, documents, embeddings, metadatas, uris).

- **Human URL:** [https://docs.trychroma.com/reference/chroma-api/record/query-collection](https://docs.trychroma.com/reference/chroma-api/record/query-collection)
- **Base URL:** `https://api.trychroma.com`

#### Tags

- Vector Search
- Similarity Search
- Semantic Search

#### Properties

- [Documentation](https://docs.trychroma.com/docs/querying-collections/query-and-get)
- [API Reference](https://docs.trychroma.com/reference/chroma-api/record/query-collection)
- [OpenAPI](openapi/chroma-db-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/chroma-db.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/chroma-db.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Chroma Tenants and Databases API

Administer the multi-tenancy hierarchy that scopes all collections - create and get tenants, and create, list, get, and delete databases within a tenant. Every collection and record path is nested under a tenant and database.

- **Human URL:** [https://docs.trychroma.com/reference/chroma-reference](https://docs.trychroma.com/reference/chroma-reference)
- **Base URL:** `https://api.trychroma.com`

#### Tags

- Multi-Tenancy
- Tenants
- Databases

#### Properties

- [Documentation](https://docs.trychroma.com/docs/overview/architecture)
- [API Reference](https://docs.trychroma.com/reference/chroma-reference)
- [OpenAPI](openapi/chroma-db-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/chroma-db.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/chroma-db.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Chroma System and Health API

Operational endpoints for a Chroma server - heartbeat, healthcheck, version, and pre-flight checks. On self-hosted deployments a reset endpoint can clear all data when explicitly enabled.

- **Human URL:** [https://docs.trychroma.com/reference/chroma-reference](https://docs.trychroma.com/reference/chroma-reference)
- **Base URL:** `https://api.trychroma.com`

#### Tags

- Health
- Operations
- Monitoring

#### Properties

- [API Reference](https://docs.trychroma.com/reference/chroma-reference)
- [OpenAPI](openapi/chroma-db-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/chroma-db.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/chroma-db.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

## Common Properties

- [Domain Security](security/chroma-db-domain-security.yml)
- [Authentication](authentication/chroma-db-authentication.yml)
- [GitHub Organization](https://github.com/chroma-core)
- [LinkedIn](https://www.linkedin.com/company/trychroma)
- [Website](https://www.trychroma.com)
- [Documentation](https://docs.trychroma.com)
- [Plans](plans/chroma-db-plans-pricing.yml)
- [Rate Limits](rate-limits/chroma-db-rate-limits.yml)
- [Fin Ops](finops/chroma-db-finops.yml)

## Maintainers

**FN:** Kin Lane
**Email:** kin@apievangelist.com
