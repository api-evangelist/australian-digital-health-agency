---
name: maintain-closure-table
description: Use the FHIR $closure operation on the NCTS FHIR Terminology Server to maintain a client-side transitive-closure table for subsumption testing.
api: NCTS FHIR Terminology Server
generated: '2026-10-21'
source: fhir/ncts-terminology-server-capabilitystatement.json
operations:
  - $closure
---

# Maintain a closure table (NCTS FHIR Terminology Server)

Base: `https://api.healthterminologies.gov.au/integration/R4/fhir`
Definition: `OperationDefinition/-s-closure` (as advertised in the CapabilityStatement).

## Steps
1. Obtain a SMART-on-FHIR Bearer token (see `fhir/ncts-terminology-server-smart-configuration.json`).
2. Initialise a named closure table by invoking `$closure` with a `name` parameter and no concepts.
3. Invoke `$closure` with the same `name` and the new `concept` codings your system has seen; the response
   `ConceptMap` holds the subsumption relationships to add to your local table.
4. Store the returned version so later calls return only the changes since that version.
5. Failures are returned as FHIR `OperationOutcome` resources.

`$closure` changes server-side table state for the named closure, so do not blindly replay it after an ambiguous failure; resynchronise using the stored version.
