# Trulioo (trulioo)

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

Trulioo is a Vancouver-based global identity verification platform that operates GlobalGateway, a single-API gateway into 450+ data sources across 195+ countries for person verification (KYC), business verification (KYB), watchlist and PEP screening, identity document verification (DocV), biometric face match, and fraud-intelligence risk scoring. The Trulioo Platform layers Workflow Studio (hosted and low-code), reusable end-client profiles, event-driven webhooks, native mobile and web capture SDKs, and an MCP server on top of the underlying Verifications and Business APIs.

**APIs.json:** [https://raw.githubusercontent.com/api-evangelist/trulioo/refs/heads/main/apis.yml](https://raw.githubusercontent.com/api-evangelist/trulioo/refs/heads/main/apis.yml)

## Scope

- **Position:** Consuming
- **Access:** 3rd-Party

## Tags

- Identity Verification
- KYC
- KYB
- AML
- Watchlist Screening
- Biometrics
- Document Verification
- Fraud Prevention
- Compliance
- Global Identity

## Timestamps

- **Created:** 2026-05-25
- **Modified:** 2026-05-25

## APIs

### Trulioo Verifications API

Normalized KYC / electronic identity verification API. Submit a Verify request with normalized PersonInfo, Communication, Location, NationalIds, and Documents fields and Trulioo's GlobalGateway routes the request across local data sources in 195+ countries. Companion endpoints retrieve transaction records, statuses, partial results, and downloadable document images.

- **Human URL:** [https://developer.trulioo.com/reference/identity-verifications](https://developer.trulioo.com/reference/identity-verifications)
- **Base URL:** `https://api.trulioo.com`

#### Tags

- KYC
- Identity Verification
- Verifications
- Transactions
- Documents

#### Properties

- [Documentation](https://developer.trulioo.com/reference/identity-verifications)
- [API Reference](https://developer.trulioo.com/reference/api-reference-overview)
- [OpenAPI](openapi/trulioo-verifications-api-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/trulioo-verifications-api.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/trulioo-verifications-api.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)
- [JSON Schema](json-schema/trulioo-verify-request-schema.json) — [JSON Schema](https://json-schema.org/specification)
- [JSON Schema](json-schema/trulioo-verify-result-schema.json) — [JSON Schema](https://json-schema.org/specification)
- [JSON-LD](json-ld/trulioo-context.jsonld) — [JSON-LD](https://www.w3.org/TR/json-ld11/)

### Trulioo Configuration API

Discovery endpoints for the GlobalGateway. Learn which countries, datasources, fields, document types, consents, and test entities are available for a configured product / package before submitting a Verify request.

- **Human URL:** [https://developer.trulioo.com/reference/configuration-1](https://developer.trulioo.com/reference/configuration-1)
- **Base URL:** `https://api.trulioo.com`

#### Tags

- Configuration
- Countries
- Datasources
- Fields
- Consents

#### Properties

- [Documentation](https://developer.trulioo.com/reference/configuration-1)
- [OpenAPI](openapi/trulioo-configuration-api-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/trulioo-configuration-api.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/trulioo-configuration-api.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Trulioo Connection API

Health-check and authentication-test endpoints. `sayhello` is an unauthenticated ping; `testauthentication` verifies your credentials before exercising paid endpoints.

- **Human URL:** [https://developer.trulioo.com/reference/connection](https://developer.trulioo.com/reference/connection)
- **Base URL:** `https://api.trulioo.com`

#### Tags

- Connection
- Health Check

#### Properties

- [Documentation](https://developer.trulioo.com/reference/connection)
- [OpenAPI](openapi/trulioo-connection-api-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/trulioo-connection-api.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/trulioo-connection-api.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Trulioo Business Verification API

Know Your Business (KYB) API for verifying legal entities, retrieving business registration data from official registries, listing officers and persons of significant control, and downloading business reports. Supports search-then-verify flows by name, registration number, and jurisdiction of incorporation.

- **Human URL:** [https://developer.trulioo.com/reference/kyb-business-verification](https://developer.trulioo.com/reference/kyb-business-verification)
- **Base URL:** `https://api.trulioo.com`

#### Tags

- KYB
- Business Verification
- Business Search
- Business Reports
- Jurisdiction Of Incorporation

#### Properties

- [Documentation](https://developer.trulioo.com/reference/kyb-business-verification)
- [Guides](https://developer.trulioo.com/reference/guide-business-verification)
- [OpenAPI](openapi/trulioo-business-verification-api-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/trulioo-business-verification-api.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/trulioo-business-verification-api.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)
- [JSON Schema](json-schema/trulioo-business-record-schema.json) — [JSON Schema](https://json-schema.org/specification)

### Trulioo Person Fraud API

Fraud Intelligence — Person Fraud risk scoring. Submit an identity payload and receive a risk verdict that aggregates third-party fraud signals, velocity checks, device intelligence, and identity-graph data.

- **Human URL:** [https://developer.trulioo.com/reference/fraud-intelligence-person-fraud](https://developer.trulioo.com/reference/fraud-intelligence-person-fraud)
- **Base URL:** `https://api.trulioo.com`

#### Tags

- Fraud Intelligence
- Person Fraud
- Risk Scoring

#### Properties

- [Documentation](https://developer.trulioo.com/reference/fraud-intelligence-person-fraud)
- [OpenAPI](openapi/trulioo-person-fraud-api-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/trulioo-person-fraud-api.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/trulioo-person-fraud-api.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Trulioo Identity Document Verification API

Capture, classify, and verify government-issued identity documents (driver's license, passport, national ID) paired with optional liveness selfie checks. Used to authenticate documents, extract MRZ / barcode data, match the document photo to a captured selfie, and manage Known Faces biometric watchlists.

- **Human URL:** [https://developer.trulioo.com/reference/identity-document-verification](https://developer.trulioo.com/reference/identity-document-verification)
- **Base URL:** `https://api.trulioo.com`

#### Tags

- Document Verification
- DocV
- Biometrics
- Liveness
- Known Faces

#### Properties

- [Documentation](https://developer.trulioo.com/reference/identity-document-verification)
- [Documentation](https://developer.trulioo.com/reference/known-faces)
- [OpenAPI](openapi/trulioo-document-verification-api-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/trulioo-document-verification-api.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/trulioo-document-verification-api.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Trulioo Platform API

Workflow Studio API. Drive hosted and embedded workflows: initialize a flow, submit data and files for each step, handle handoffs between user-facing capture and backend processing, and retrieve end-client profiles, files, workflow definitions, and transaction state. Backs both the Low-Code Workflow Studio and the API-first Workflow Studio integrations.

- **Human URL:** [https://developer.trulioo.com/reference/workflow-studio-api](https://developer.trulioo.com/reference/workflow-studio-api)
- **Base URL:** `https://api.trulioo.com`

#### Tags

- Workflow Studio
- Platform
- Flows
- End Clients
- Workflows
- Sessions
- Events

#### Properties

- [Documentation](https://developer.trulioo.com/reference/workflow-studio-api)
- [Documentation](https://developer.trulioo.com/reference/workflow-studio-low-code)
- [Webhooks](https://developer.trulioo.com/reference/event-dispatcher)
- [OpenAPI](openapi/trulioo-platform-api-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/trulioo-platform-api.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/trulioo-platform-api.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

## Common Properties

- [Arazzo Workflows](arazzo/) — [Arazzo Specification](https://spec.openapis.org/arazzo/latest.html)
- [Portal](https://www.trulioo.com)
- [Documentation](https://developer.trulioo.com)
- [Getting Started](https://developer.trulioo.com/reference/getting-started-1)
- [API Reference](https://developer.trulioo.com/reference/api-reference-overview)
- [Authentication](https://developer.trulioo.com/reference/authentication)
- [Authentication](https://developer.trulioo.com/reference/hmac)
- [Authentication](https://developer.trulioo.com/reference/connecting-to-trulioos-api-using-mutual-tls)
- [Webhooks](https://developer.trulioo.com/reference/event-dispatcher)
- [Changelog](https://developer.trulioo.com/docs/release-notes)
- [Release Notes](https://developer.trulioo.com/docs/platform-update-67)
- [Sandbox](https://developer.trulioo.com/docs/trulidemo)
- [Support](https://support@trulioo.com)
- [Support Portal](https://knowledgehub.trulioo.com)
- [Status](https://status.trulioo.com)
- [Trust Center](https://www.trulioo.com/trust)
- [Security](https://www.trulioo.com/trust/security)
- [Compliance](https://www.trulioo.com/trust/compliance)
- [Privacy Policy](https://www.trulioo.com/legal/privacy-policy)
- [Terms of Service](https://www.trulioo.com/legal/terms-of-service)
- [Blog](https://www.trulioo.com/blog)
- [Customers](https://www.trulioo.com/customers)
- [Case Studies](https://www.trulioo.com/resource-library?type=case-studies)
- [Resource Library](https://www.trulioo.com/resource-library)
- [Pricing](https://www.trulioo.com/contact)
- [Login](https://portal.trulioo.com)
- [Sign Up](https://www.trulioo.com/contact-sales)
- [Contact Sales](https://www.trulioo.com/contact-sales)
- [Careers](https://www.trulioo.com/about-us/careers)
- [About Us](https://www.trulioo.com/about-us)
- [Leadership](https://www.trulioo.com/about-us/leadership)
- [News](https://www.trulioo.com/news-and-events)
- [GitHub Organization](https://github.com/trulioo)
- [SDK](https://github.com/trulioo/sdk-csharp-v3)
- [SDK](https://github.com/trulioo/sdk-java-v3)
- [SDK](https://github.com/trulioo/sdk-csharp-v1)
- [SDK](https://github.com/trulioo/sdk-java-v1)
- [Mobile S D K](https://github.com/trulioo/trulioo-ios)
- [Mobile S D K](https://github.com/trulioo/kyc-documents-capture)
- [Mobile S D K](https://github.com/trulioo/docv)
- [Mobile S D K](https://developer.trulioo.com/reference/android)
- [Mobile S D K](https://developer.trulioo.com/reference/react-native)
- [Web S D K](https://developer.trulioo.com/reference/web)
- [M C P Server](https://github.com/trulioo/mcp-server)
- [LinkedIn](https://www.linkedin.com/company/trulioo)
- [Twitter](https://twitter.com/trulioo)
- [Instagram](https://www.instagram.com/trulioo_global)
- [Regions](https://developer.trulioo.com/reference/multi-region-hosting)
- [Errors](https://developer.trulioo.com/reference/errors)
- [Versioning](https://developer.trulioo.com/reference/api-reference-overview)
- [llmstxt](https://developer.trulioo.com/llms.txt)
- [Plans](plans/trulioo-plans-pricing.yml)
- [Rate Limits](rate-limits/trulioo-rate-limits.yml)
- [Fin Ops](finops/trulioo-finops.yml)
- [Features](undefined)

## Maintainers

**FN:** Kin Lane
**Email:** info@apievangelist.com
**URL:** https://apievangelist.com
