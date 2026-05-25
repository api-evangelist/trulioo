# Trulioo (trulioo)
Trulioo is a Vancouver-based global identity verification platform that operates GlobalGateway, a single-API gateway into 450+ data sources across 195+ countries for person verification (KYC), business verification (KYB), watchlist and PEP screening, identity document verification (DocV), biometric face match, and fraud-intelligence risk scoring. The Trulioo Platform layers Workflow Studio (hosted and low-code), reusable end-client profiles, event-driven webhooks, native mobile and web capture SDKs, and an MCP server on top of the underlying Verifications and Business APIs.

**URL:** [Visit APIs.json](https://raw.githubusercontent.com/api-evangelist/trulioo/refs/heads/main/apis.yml)

**Run:** [Capabilities Using Naftiko](https://github.com/naftiko/fleet?utm_source=api-evangelist&utm_medium=readme&utm_campaign=company-api-evangelist&utm_content=repo)

## Tags

- Identity Verification, KYC, KYB, AML, Watchlist Screening, Biometrics, Document Verification, Fraud Prevention, Compliance, Global Identity

## Timestamps

- **Created:** 2026-05-25
- **Modified:** 2026-05-25

## APIs

### Trulioo Verifications API
Normalized KYC / electronic identity verification API. Submit a Verify request with normalized PersonInfo, Communication, Location, NationalIds, and Documents fields and Trulioo's GlobalGateway routes the request across local data sources in 195+ countries. Companion endpoints retrieve transaction records, statuses, partial results, and downloadable document images.

**Human URL:** [https://developer.trulioo.com/reference/identity-verifications](https://developer.trulioo.com/reference/identity-verifications)

**Base URL:** `https://api.trulioo.com`

- [Documentation](https://developer.trulioo.com/reference/identity-verifications)
- [API Reference](https://developer.trulioo.com/reference/api-reference-overview)
- [OpenAPI](openapi/trulioo-verifications-api-openapi.yml)
- [JSON Schema — Verify Request](json-schema/trulioo-verify-request-schema.json)
- [JSON Schema — Verify Result](json-schema/trulioo-verify-result-schema.json)
- [JSON-LD](json-ld/trulioo-context.jsonld)
- [Naftiko Capability — Verify](capabilities/verifications-verify.yaml)
- [Naftiko Capability — Transactions](capabilities/verifications-transactions.yaml)

### Trulioo Configuration API
Discovery endpoints for the GlobalGateway. Learn which countries, datasources, fields, document types, consents, and test entities are available for a configured product / package before submitting a Verify request.

**Human URL:** [https://developer.trulioo.com/reference/configuration-1](https://developer.trulioo.com/reference/configuration-1)

- [OpenAPI](openapi/trulioo-configuration-api-openapi.yml)
- [Naftiko Capability — Configuration](capabilities/configuration-configuration.yaml)

### Trulioo Connection API
Health-check and authentication-test endpoints. `sayhello` is an unauthenticated ping; `testauthentication` verifies your credentials before exercising paid endpoints.

**Human URL:** [https://developer.trulioo.com/reference/connection](https://developer.trulioo.com/reference/connection)

- [OpenAPI](openapi/trulioo-connection-api-openapi.yml)
- [Naftiko Capability — Connection](capabilities/connection-connection.yaml)

### Trulioo Business Verification API
Know Your Business (KYB) API for verifying legal entities, retrieving business registration data from official registries, listing officers and persons of significant control, and downloading business reports. Supports search-then-verify flows by name, registration number, and jurisdiction of incorporation.

**Human URL:** [https://developer.trulioo.com/reference/kyb-business-verification](https://developer.trulioo.com/reference/kyb-business-verification)

- [Documentation](https://developer.trulioo.com/reference/kyb-business-verification)
- [Guide — Business Verification](https://developer.trulioo.com/reference/guide-business-verification)
- [OpenAPI](openapi/trulioo-business-verification-api-openapi.yml)
- [JSON Schema — Business Record](json-schema/trulioo-business-record-schema.json)
- [Naftiko Capability — Search](capabilities/business-verification-search.yaml)
- [Naftiko Capability — Verify](capabilities/business-verification-verify.yaml)

### Trulioo Person Fraud API
Fraud Intelligence — Person Fraud risk scoring. Submit an identity payload and receive a risk verdict that aggregates third-party fraud signals, velocity checks, device intelligence, and identity-graph data.

**Human URL:** [https://developer.trulioo.com/reference/fraud-intelligence-person-fraud](https://developer.trulioo.com/reference/fraud-intelligence-person-fraud)

- [OpenAPI](openapi/trulioo-person-fraud-api-openapi.yml)
- [Naftiko Capability — Risk](capabilities/person-fraud-risk.yaml)

### Trulioo Identity Document Verification API
Capture, classify, and verify government-issued identity documents (driver's license, passport, national ID) paired with optional liveness selfie checks. Used to authenticate documents, extract MRZ / barcode data, match the document photo to a captured selfie, and manage Known Faces biometric watchlists.

**Human URL:** [https://developer.trulioo.com/reference/identity-document-verification](https://developer.trulioo.com/reference/identity-document-verification)

- [Documentation](https://developer.trulioo.com/reference/identity-document-verification)
- [Documentation — Known Faces](https://developer.trulioo.com/reference/known-faces)
- [OpenAPI](openapi/trulioo-document-verification-api-openapi.yml)
- [Naftiko Capability — Verify](capabilities/document-verification-verify.yaml)
- [Naftiko Capability — Known Faces](capabilities/document-verification-known-faces.yaml)

### Trulioo Platform API
Workflow Studio API. Drive hosted and embedded workflows: initialize a flow, submit data and files for each step, handle handoffs between user-facing capture and backend processing, and retrieve end-client profiles, files, workflow definitions, and transaction state. Backs both the Low-Code Workflow Studio and the API-first Workflow Studio integrations.

**Human URL:** [https://developer.trulioo.com/reference/workflow-studio-api](https://developer.trulioo.com/reference/workflow-studio-api)

- [Documentation — Workflow Studio (API)](https://developer.trulioo.com/reference/workflow-studio-api)
- [Documentation — Workflow Studio (Low-Code)](https://developer.trulioo.com/reference/workflow-studio-low-code)
- [Webhooks — Event Dispatcher](https://developer.trulioo.com/reference/event-dispatcher)
- [OpenAPI](openapi/trulioo-platform-api-openapi.yml)
- [Naftiko Capability — Flows](capabilities/platform-flows.yaml)
- [Naftiko Capability — End Clients](capabilities/platform-end-clients.yaml)
- [Naftiko Capability — Workflows](capabilities/platform-workflows.yaml)

## Authentication

Trulioo offers four authentication mechanisms:

- **HTTP Basic** — username/password supplied via the `Authorization: Basic` header. Used by the v3 Verifications, Configuration, Connection, Business, Document Verification, and Person Fraud APIs.
- **OAuth 2.0 Client Credentials** — two-legged flow at `https://auth-api.trulioo.com/connect/token` (and `https://api.trulioo.com/customer/v2/auth/customer` for the Platform API). Used for the Workflow Studio / Platform API.
- **HMAC** — request signing for additional integrity.
- **Mutual TLS** — certificate-based authentication for enterprise customers.

See: [Authentication](https://developer.trulioo.com/reference/authentication) · [HMAC](https://developer.trulioo.com/reference/hmac) · [Mutual TLS](https://developer.trulioo.com/reference/connecting-to-trulioos-api-using-mutual-tls)

## SDKs

| Language / Platform | Repo |
|---|---|
| C# (v3) | [trulioo/sdk-csharp-v3](https://github.com/trulioo/sdk-csharp-v3) |
| Java (v3) | [trulioo/sdk-java-v3](https://github.com/trulioo/sdk-java-v3) |
| C# (v1, legacy) | [trulioo/sdk-csharp-v1](https://github.com/trulioo/sdk-csharp-v1) |
| Java (v1, legacy) | [trulioo/sdk-java-v1](https://github.com/trulioo/sdk-java-v1) |
| iOS | [trulioo/trulioo-ios](https://github.com/trulioo/trulioo-ios) |
| iOS Document Capture | [trulioo/kyc-documents-capture](https://github.com/trulioo/kyc-documents-capture) |
| iOS DocV (legacy) | [trulioo/docv](https://github.com/trulioo/docv) |
| Android Capture | [Android docs](https://developer.trulioo.com/reference/android) |
| React Native Capture | [React Native docs](https://developer.trulioo.com/reference/react-native) |
| Web Capture | [Web docs](https://developer.trulioo.com/reference/web) |
| MCP Server (KYB) | [trulioo/mcp-server](https://github.com/trulioo/mcp-server) |

## Common Properties

- **Portal:** [https://www.trulioo.com](https://www.trulioo.com)
- **Developer:** [https://developer.trulioo.com](https://developer.trulioo.com)
- **API Reference:** [https://developer.trulioo.com/reference/api-reference-overview](https://developer.trulioo.com/reference/api-reference-overview)
- **Getting Started:** [https://developer.trulioo.com/reference/getting-started-1](https://developer.trulioo.com/reference/getting-started-1)
- **Multi-Region Hosting:** [https://developer.trulioo.com/reference/multi-region-hosting](https://developer.trulioo.com/reference/multi-region-hosting)
- **Webhooks (Event Dispatcher):** [https://developer.trulioo.com/reference/event-dispatcher](https://developer.trulioo.com/reference/event-dispatcher)
- **Changelog:** [https://developer.trulioo.com/docs/release-notes](https://developer.trulioo.com/docs/release-notes)
- **Latest release (6.7):** [Platform Update 6.7](https://developer.trulioo.com/docs/platform-update-67)
- **Knowledge Hub:** [https://knowledgehub.trulioo.com](https://knowledgehub.trulioo.com)
- **Sandbox:** [Trulidemo](https://developer.trulioo.com/docs/trulidemo)
- **Trust Center:** [https://www.trulioo.com/trust](https://www.trulioo.com/trust)
- **llms.txt:** [https://developer.trulioo.com/llms.txt](https://developer.trulioo.com/llms.txt)
- **GitHub:** [https://github.com/trulioo](https://github.com/trulioo)

## Commercial Surface

- [Plans / Pricing](plans/trulioo-plans-pricing.yml)
- [Rate Limits](rate-limits/trulioo-rate-limits.yml)
- [FinOps](finops/trulioo-finops.yml)

## Spec Artifacts

- [OpenAPI specs](openapi/) — 7 specs (Verifications, Configuration, Connection, Business Verification, Person Fraud, Document Verification, Platform)
- [Naftiko Capabilities](capabilities/) — 11 capabilities across all seven APIs
- [JSON Schema](json-schema/) — Verify Request, Verify Result, Business Record
- [JSON Structure](json-structure/) — Verification result structure
- [JSON-LD](json-ld/) — schema.org / trulioo vocab context
- [Examples](examples/) — Verify, Business Search, Document Verify
- [Spectral Rules](rules/) — `trulioo-rules.yml`
- [Vocabulary](vocabulary/) — Operational vocabulary across products
