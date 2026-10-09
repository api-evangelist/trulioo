---
generated: '2026-10-08'
method: generated
name: trulioo-business-search-and-verify-rest
title: Search for a business and verify it (KYB) over REST
description: Look up registration-number formats, search for a business by name and country, verify the
  chosen candidate and download the business report.
api: openapi/trulioo-business-verification-api-openapi.yml
operations:
- getBusinessRegistrationNumbersByCountry
- businessSearch
- getBusinessSearchResult
- businessVerify
- getBusinessReport
source: Grounded in the matching arazzo/ workflow and the provider docs; operationIds verified in openapi/trulioo-business-verification-api-openapi.yml;
  conventions from conventions/trulioo-conventions.yml, errors from errors/trulioo-error-codes.yml, sandbox
  from sandbox/trulioo-sandbox.yml.
---

# Search for a business and verify it (KYB) over REST

Mirrors arazzo/trulioo-business-search-and-verify-workflow.yml and arazzo/trulioo-business-verify-and-download-report-workflow.yml. The same flow is available over MCP as kyb_search -> kyb_verify -> kyb_get_report (mcp/trulioo-tool-crosswalk.yml).

## Steps

1. `getBusinessRegistrationNumbersByCountry` (GET /v3/business/businessregistrationnumbers/{countryCode}) - learn which registration-number types and jurisdictions the country accepts before you format the request.
2. `businessSearch` (POST /v3/business/search) with `Business.BusinessName`, `Business.CountryCode` (and `JurisdictionOfIncorporation` where known). Keep the returned `TransactionRecordID`.
3. `getBusinessSearchResult` (GET /v3/business/search/transactionrecord/{transactionRecordId}) - read the ranked candidates; when more than one business matches, have the user choose before verifying.
4. `businessVerify` (POST /v3/business/verify) with the chosen `BusinessRegistrationNumber`, `BusinessName`, `CountryCode` and `ConfigurationName` of a Business Verification package (Essentials, Insights or Complete). Save `TransactionRecordID`.
5. `getBusinessReport` (GET /v3/business/report/{transactionRecordId}) once the verification is complete to retrieve the Trulioo Business Summary Report.

## Rules that apply to every step

- Authenticate first: POST https://auth-api.trulioo.com/connect/token with `grant_type=client_credentials` and `scope=napi.api`, then send `Authorization: Bearer <token>`; Client Id/Secret come from your Trulioo Customer Success Manager (authentication/trulioo-authentication.yml).
- Use your **Sandbox** credentials while building: sandbox transactions run against static Test Entities and are not chargeable (sandbox/trulioo-sandbox.yml).
- There is no Idempotency-Key: a repeated verify call is a second chargeable transaction. Keep the returned `TransactionID` / `TransactionRecordID` and re-read instead of re-submitting (conventions/trulioo-conventions.yml, `idempotency.coverage: none`).
- A verification cannot be reversed once submitted (`reversibility`), so confirm inputs before calling the verify operation.
- Treat service-, record- and validation-level codes inside a 200 record as the real outcome (errors/trulioo-error-codes.yml): 1001 Missing Required Field and 1005 Missing Consent mean re-run the configuration steps, not retry.
- No numeric rate limit is published; back off on 5xx and contact support if you need more capacity (rate-limits/trulioo-rate-limits.yml).
