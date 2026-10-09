---
generated: '2026-10-08'
method: generated
name: trulioo-document-verification-rest
title: Verify an identity document with the capture SDK handoff
description: Authorize a Platform session, create a short-lived handoff code for the capture SDK, then
  verify the document and download the evidence.
api: openapi/trulioo-document-verification-api-openapi.yml
operations:
- postAuthCustomer
- postHandoff
- getDocumentTypes
- documentVerificationVerify
- downloadDocument
source: Grounded in the matching arazzo/ workflow and the provider docs; operationIds verified in openapi/trulioo-document-verification-api-openapi.yml;
  conventions from conventions/trulioo-conventions.yml, errors from errors/trulioo-error-codes.yml, sandbox
  from sandbox/trulioo-sandbox.yml.
---

# Verify an identity document with the capture SDK handoff

Mirrors arazzo/trulioo-document-verification-with-liveness-workflow.yml and arazzo/trulioo-document-verify-and-download-evidence-workflow.yml.

## Steps

1. `postAuthCustomer` (POST /customer/v2/auth/customer) - exchange your Platform client credentials for an access token; tokens expire in one hour.
2. `postHandoff` (POST /customer/v2/handoff) - generate a single-use short code (valid for 5 minutes) that hands the active transaction to the @trulioo/kyc-documents-capture web SDK or the iOS/Android capture SDKs; image capture happens in the SDK, never in your API call.
3. `getDocumentTypes` (GET /v3/verifications/documenttypes/{countryCode}) - confirm the document type the end user holds is accepted for that country.
4. `documentVerificationVerify` (POST /v3/verifications/documentverification/verify) with the captured `DocumentFrontImage` / `DocumentBackImage` / `LivePhoto` (base64) and `DocumentType`; the sandbox article does not cover DocV, so test with real sandbox sessions.
5. `downloadDocument` (GET /v3/verifications/documentdownload/{transactionRecordId}/{fieldName}) to retrieve the stored evidence image for the record.

## Rules that apply to every step

- Authenticate first: POST https://auth-api.trulioo.com/connect/token with `grant_type=client_credentials` and `scope=napi.api`, then send `Authorization: Bearer <token>`; Client Id/Secret come from your Trulioo Customer Success Manager (authentication/trulioo-authentication.yml).
- Use your **Sandbox** credentials while building: sandbox transactions run against static Test Entities and are not chargeable (sandbox/trulioo-sandbox.yml).
- There is no Idempotency-Key: a repeated verify call is a second chargeable transaction. Keep the returned `TransactionID` / `TransactionRecordID` and re-read instead of re-submitting (conventions/trulioo-conventions.yml, `idempotency.coverage: none`).
- A verification cannot be reversed once submitted (`reversibility`), so confirm inputs before calling the verify operation.
- Treat service-, record- and validation-level codes inside a 200 record as the real outcome (errors/trulioo-error-codes.yml): 1001 Missing Required Field and 1005 Missing Consent mean re-run the configuration steps, not retry.
- No numeric rate limit is published; back off on 5xx and contact support if you need more capacity (rate-limits/trulioo-rate-limits.yml).
