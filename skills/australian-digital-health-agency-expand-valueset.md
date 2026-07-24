---
name: Expand a value set on the NCTS FHIR terminology server
description: Retrieve the full member list of a SNOMED CT-AU / AMT / LOINC value set using the FHIR $expand operation on the NCTS FHIR Terminology Server.
api: fhir/ncts-terminology-server-capabilitystatement.json
operations:
  - ValueSet/$expand
---

# Expand a value set (NCTS FHIR Terminology Server)

Use this to turn a value set (identified by canonical URL) into its concrete list of member codes and displays — for populating pick-lists, validating coded fields, or building UI selectors.

## Base
`https://api.healthterminologies.gov.au/integration/R4/fhir`

## Authentication
SMART-on-FHIR OAuth2 (authorization code). Obtain a Bearer token:
- authorize: `https://api.healthterminologies.gov.au/oauth2/login`
- token: `https://api.healthterminologies.gov.au/oauth2/token`
- scopes: `openid profile`

See `authentication/australian-digital-health-agency-authentication.yml` and `scopes/australian-digital-health-agency-scopes.yml`.

## Steps
1. Acquire an OAuth2 Bearer access token (authorization-code flow).
2. Call the `$expand` operation on the `ValueSet` type:
   ```
   GET /integration/R4/fhir/ValueSet/$expand?url={valueSetCanonicalUrl}&count=100
   Authorization: Bearer {token}
   Accept: application/fhir+json
   ```
   For large or parameterised expansions, POST a `Parameters` resource with `url`, `filter`, `count`, and `offset` instead.
3. Read the returned `ValueSet.expansion.contains[]` — each entry has `system`, `code`, and `display`.
4. Page with `count` + `offset` (or the Bundle link relations) until `expansion.total` is exhausted.

## Conventions & errors
- Content negotiation: `application/fhir+json` (default) or `application/fhir+xml`; see `conventions/australian-digital-health-agency-conventions.yml`.
- Errors return a FHIR `OperationOutcome`; see `errors/australian-digital-health-agency-problem-types.yml` (e.g. 404 unknown value set, 401 missing/expired token).
