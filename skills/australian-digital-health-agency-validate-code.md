---
name: Validate a code against a value set (NCTS)
description: Check that a SNOMED CT-AU / AMT / LOINC code is a valid member of a value set or code system using the FHIR $validate-code operation on the NCTS FHIR Terminology Server.
api: fhir/ncts-terminology-server-capabilitystatement.json
operations:
  - ValueSet/$validate-code
  - CodeSystem/$validate-code
---

# Validate a code (NCTS FHIR Terminology Server)

Use this to confirm that a coded value captured in clinical software is a legal member of the intended value set or code system before it is stored or transmitted.

## Base
`https://api.healthterminologies.gov.au/integration/R4/fhir`

## Authentication
SMART-on-FHIR OAuth2 Bearer token (authorize `https://api.healthterminologies.gov.au/oauth2/login`, token `https://api.healthterminologies.gov.au/oauth2/token`, scopes `openid profile`).

## Steps
1. Acquire an OAuth2 Bearer access token.
2. Call `$validate-code`:
   ```
   GET /integration/R4/fhir/ValueSet/$validate-code?url={valueSetUrl}&system={codeSystemUrl}&code={code}
   Authorization: Bearer {token}
   Accept: application/fhir+json
   ```
   Or validate directly against a code system with `CodeSystem/$validate-code`.
3. Read the returned `Parameters`: the boolean `result` says whether the code is valid; `display` returns the preferred display; `message` explains a failure.
4. If `result` is `false`, surface `message` and do not persist the code.

## Conventions & errors
- Errors return a FHIR `OperationOutcome`; see `errors/australian-digital-health-agency-problem-types.yml`.
- Idempotent read operation — safe to retry; see `conventions/australian-digital-health-agency-conventions.yml`.
