---
generated: '2026-10-08'
method: generated
name: trulioo-person-fraud-check-rest
title: Run a Person Fraud risk check
description: Read the fraud configuration for a country, then score a person for fraud risk with the Person
  Fraud API.
api: openapi/trulioo-person-fraud-api-openapi.yml
operations:
- getPersonFraudCountryCodes
- getPersonFraudFields
- personFraudCheck
source: Grounded in the matching arazzo/ workflow and the provider docs; operationIds verified in openapi/trulioo-person-fraud-api-openapi.yml;
  conventions from conventions/trulioo-conventions.yml, errors from errors/trulioo-error-codes.yml, sandbox
  from sandbox/trulioo-sandbox.yml.
---

# Run a Person Fraud risk check

Mirrors arazzo/trulioo-person-fraud-risk-check-workflow.yml and arazzo/trulioo-identity-and-fraud-risk-decision-workflow.yml.

## Steps

1. `getPersonFraudCountryCodes` (GET /risk/v1/configuration/countrycodes/{configurationName}) - confirm the Person Fraud configuration covers the country (Fraud & Risk is hosted in the US (Oregon) region only, lifecycle/trulioo-lifecycle.yml).
2. `getPersonFraudFields` (GET /risk/v1/configuration/fields/{configurationName}/{countryCode}) - read the identity, device and contact fields the risk model accepts.
3. `personFraudCheck` (POST /risk/v1/check) with the collected fields; combine the returned risk score with a KYC `verifyPerson` outcome before deciding (see the identity-and-fraud-risk-decision workflow).

## Rules that apply to every step

- Authenticate first: POST https://auth-api.trulioo.com/connect/token with `grant_type=client_credentials` and `scope=napi.api`, then send `Authorization: Bearer <token>`; Client Id/Secret come from your Trulioo Customer Success Manager (authentication/trulioo-authentication.yml).
- Use your **Sandbox** credentials while building: sandbox transactions run against static Test Entities and are not chargeable (sandbox/trulioo-sandbox.yml).
- There is no Idempotency-Key: a repeated verify call is a second chargeable transaction. Keep the returned `TransactionID` / `TransactionRecordID` and re-read instead of re-submitting (conventions/trulioo-conventions.yml, `idempotency.coverage: none`).
- A verification cannot be reversed once submitted (`reversibility`), so confirm inputs before calling the verify operation.
- Treat service-, record- and validation-level codes inside a 200 record as the real outcome (errors/trulioo-error-codes.yml): 1001 Missing Required Field and 1005 Missing Consent mean re-run the configuration steps, not retry.
- No numeric rate limit is published; back off on 5xx and contact support if you need more capacity (rate-limits/trulioo-rate-limits.yml).
