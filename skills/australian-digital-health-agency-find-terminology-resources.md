---
name: find-terminology-resources
description: Find and read CodeSystem, ValueSet and ConceptMap resources (SNOMED CT-AU, AMT, LOINC content) on the NCTS FHIR Terminology Server.
api: NCTS FHIR Terminology Server
generated: '2026-10-21'
source: fhir/ncts-terminology-server-capabilitystatement.json
operations:
  - CodeSystem.search-type
  - CodeSystem.read
  - ValueSet.search-type
  - ValueSet.read
  - ConceptMap.search-type
  - ConceptMap.read
---

# Find terminology resources (NCTS FHIR Terminology Server)

Base: `https://api.healthterminologies.gov.au/integration/R4/fhir`

## Authentication
SMART-on-FHIR OAuth2. Discovery: `fhir/ncts-terminology-server-smart-configuration.json`; see
`authentication/australian-digital-health-agency-authentication.yml`. A registered NCTS client is required.

## Steps
1. Obtain a Bearer access token using the flow described in the SMART configuration.
2. Search by type (`search-type`), e.g. `GET /ValueSet?url={canonicalUrl}` or `GET /CodeSystem?url={system}`,
   with `Accept: application/fhir+json`. The result is a FHIR `Bundle` of type `searchset`.
3. Read a single resource by id (`read`): `GET /ValueSet/{id}`, `GET /CodeSystem/{id}`, `GET /ConceptMap/{id}`.
4. On failure the server returns a FHIR `OperationOutcome`; see `errors/australian-digital-health-agency-problem-types.yml`.

These are read-only interactions and safe to retry.
