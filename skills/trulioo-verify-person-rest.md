---
generated: '2026-10-08'
method: generated
name: trulioo-verify-person-rest
title: Verify a person (KYC) over REST
description: Discover the fields and consents a package requires for a country, submit a normalized Verify
  request, poll an in-progress transaction and fetch the full record.
api: openapi/trulioo-verifications-api-openapi.yml
operations:
- getCountryCodes
- getRecommendedFields
- getConsents
- verifyPerson
- getTransactionStatus
- getTransactionRecord
source: Grounded in the matching arazzo/ workflow and the provider docs; operationIds verified in openapi/trulioo-verifications-api-openapi.yml;
  conventions from conventions/trulioo-conventions.yml, errors from errors/trulioo-error-codes.yml, sandbox
  from sandbox/trulioo-sandbox.yml.
---

# Verify a person (KYC) over REST

Mirrors arazzo/trulioo-recommended-fields-verify-workflow.yml and arazzo/trulioo-async-verify-and-poll-status-workflow.yml.

## Steps

1. `getCountryCodes` (GET /v3/configuration/countrycodes/{configurationName}) - confirm the country is enabled on your package; a 400 "Account not configured for this country" means it is not.
2. `getRecommendedFields` (GET /v3/configuration/fields/{configurationName}/{countryCode}/recommended) - read the JSON Schema of PersonInfo / Location / Communication / NationalIds fields the data sources expect.
3. `getConsents` (GET /v3/configuration/consents/{configurationName}/{countryCode}) - collect every named consent the sources require and put the names in `ConsentForDataSources`; a missing consent returns code 1005 inside the record.
4. `verifyPerson` (POST /v3/verifications/verify) with `AcceptTruliooTermsAndConditions: true`, `CountryCode`, `ConfigurationName` and the `DataFields` you collected. Save `TransactionID` and `TransactionRecordID` from the response.
5. If `Record.RecordStatus` is still in progress, poll `getTransactionStatus` (GET /v3/verifications/transaction/{transactionId}/status) until `Status` is no longer `inprogress`.
6. `getTransactionRecord` (GET /v3/verifications/transactionrecord/{transactionRecordId}) - read `Record.RecordStatus` (match / nomatch) and the per-datasource `DatasourceResults`; 2004 means the ID was a TransactionID rather than a TransactionRecordID.

## Rules that apply to every step

- Authenticate first: POST https://auth-api.trulioo.com/connect/token with `grant_type=client_credentials` and `scope=napi.api`, then send `Authorization: Bearer <token>`; Client Id/Secret come from your Trulioo Customer Success Manager (authentication/trulioo-authentication.yml).
- Use your **Sandbox** credentials while building: sandbox transactions run against static Test Entities and are not chargeable (sandbox/trulioo-sandbox.yml).
- There is no Idempotency-Key: a repeated verify call is a second chargeable transaction. Keep the returned `TransactionID` / `TransactionRecordID` and re-read instead of re-submitting (conventions/trulioo-conventions.yml, `idempotency.coverage: none`).
- A verification cannot be reversed once submitted (`reversibility`), so confirm inputs before calling the verify operation.
- Treat service-, record- and validation-level codes inside a 200 record as the real outcome (errors/trulioo-error-codes.yml): 1001 Missing Required Field and 1005 Missing Consent mean re-run the configuration steps, not retry.
- No numeric rate limit is published; back off on 5xx and contact support if you need more capacity (rate-limits/trulioo-rate-limits.yml).
