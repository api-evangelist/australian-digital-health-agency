# Australian Digital Health Agency (australian-digital-health-agency)

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
> **Not from the company, and here with a question?** You are welcome here — we would rather be the
> front line and point you the right way than have a good report go nowhere. What this repository
> can answer is narrow, though, so it is worth knowing who you are actually looking for:
>
> - **A question about how the API works, an account, billing, or a bug in the service** — that is
>   the company's own support, not us. We profile this API; we do not operate it and cannot see
>   your account.
> - **A bug in an open-source project we only catalog** — file it on that project's own repository.
>   This has happened with a real and correct bug report that reached us instead of the people who
>   could fix it, which helped nobody.
> - **Anything about this listing itself** — the description, the tags, the rating, a missing or
>   wrong artifact — is ours. Open an issue here.
> - **Not sure, or something general about API Evangelist or APIs.io** — open an issue on the
>   [APIs.io Inbox](https://github.com/api-search/inbox) and we will route it.
>
> **This repository contains no software, and we will never ask you to download anything.** There is
> no build, release, installer, or binary here — only text and machine-readable API descriptions, so
> there is nothing here that can be "corrupt" or need "repairing". Any issue, comment, or email
> claiming otherwise and offering a download link is not from us and is hostile. Do not follow the
> link; it is a lure. Report it to GitHub and, if you like, tell us at
> [info@apievangelist.com](mailto:info@apievangelist.com) so we can take it down.
>
> **On a security or compliance team?** Email
> [info@apievangelist.com](mailto:info@apievangelist.com) with *security* in the subject line and
> you will get a person, not a form. We will tell you exactly which public URLs this profile was
> built from so your team can see the same surface we did, and we will take the listing down on
> request while you work through it.
>
> Full detail: **[Where this data comes from](https://apievangelist.com/about/where-our-data-comes-from)**
<!-- API-EVANGELIST-PROVENANCE:END -->

The Australian Digital Health Agency (ADHA) is the Australian Government statutory agency responsible for national digital health infrastructure and standards. It operates and stewards My Health Record, the Healthcare Identifiers (HI) Service, the National Authentication Service for Health (NASH) PKI, electronic prescribing, and the National Clinical Terminology Service (NCTS). ADHA publishes machine-readable APIs — centred on HL7 FHIR (R4) alongside legacy HL7 CDA — for connecting conformant clinical software to these national systems. Home market: Australia.

**APIs.json:** [https://raw.githubusercontent.com/api-evangelist/australian-digital-health-agency/refs/heads/main/apis.yml](https://raw.githubusercontent.com/api-evangelist/australian-digital-health-agency/refs/heads/main/apis.yml)

## Tags

- Healthcare
- Australia
- National Health System
- FHIR
- HL7
- Interoperability
- SMART on FHIR
- Electronic Health Record
- e-Prescribing
- Terminology
- Government

## Timestamps

- **Created:** 2026-07-24
- **Modified:** 2026-07-24

## APIs

### My Health Record FHIR Gateway (B2B)

Business-to-business FHIR Gateway for connecting conformant clinical software to the My Health Record national shared health record. Authenticated with NASH SHA-2 PKI certificates over mutual TLS; registration and conformance testing required.

- **Human URL:** [implementer.digitalhealth.gov.au — My Health Record FHIR Gateway](https://implementer.digitalhealth.gov.au/resources/services/my-health-record/my-health-record-fhir-gateway)
- **API Specification:** [FHIR Gateway API Specification v3.0.0](https://implementer.digitalhealth.gov.au/resources/my-health-record-fhir-gateway-api-specification-v3-0-0)

### My Health Record FHIR Mobile Gateway

FHIR interface for mobile and consumer applications to retrieve documents and health information from My Health Record on behalf of individuals.

- **Human URL:** [developer.digitalhealth.gov.au — Mobile Gateway Developer Guide](https://developer.digitalhealth.gov.au/developer-guide/introduction-my-health-record-fhir-gateway-developer-guide-1)

### NCTS FHIR Terminology Server

The National Clinical Terminology Service FHIR R4 (4.0.1) terminology server, operated by ADHA on CSIRO Ontoserver. Supports CodeSystem, ValueSet, ConceptMap, OperationDefinition and StructureDefinition with `$expand`, `$lookup`, `$validate-code`, `$translate` and `$closure` over SNOMED CT-AU, AMT and LOINC. Authenticated with SMART-on-FHIR OAuth2. A live FHIR CapabilityStatement was harvested from `/metadata`.

- **Human URL:** [NCTS APIs](https://www.healthterminologies.gov.au/implementing-in-software/terminology-as-a-service/ncts-apis/)
- **Base URL:** `https://api.healthterminologies.gov.au/integration/R4/fhir`
- **CapabilityStatement:** [fhir/ncts-terminology-server-capabilitystatement.json](fhir/ncts-terminology-server-capabilitystatement.json)
- **SMART configuration:** [fhir/ncts-terminology-server-smart-configuration.json](fhir/ncts-terminology-server-smart-configuration.json)

### NCTS National Syndication Server

Atom Publishing Protocol feed for downloading FHIR terminology resource bundles. Generated by the Australian Digital Health Agency.

- **Human URL:** [NCTS APIs](https://www.healthterminologies.gov.au/implementing-in-software/terminology-as-a-service/ncts-apis/)
- **Base URL:** `https://api.healthterminologies.gov.au/syndication/v1`

### Electronic Prescribing

ADHA's electronic prescribing service and conformance profiles for electronic prescriptions, dispensing and the Active Script List.

- **Human URL:** [implementer.digitalhealth.gov.au — Electronic Prescribing](https://implementer.digitalhealth.gov.au/resources/services/electronic-prescribing)

### Healthcare Identifiers (HI) Service

National service providing unique identifiers for individuals (IHI), providers (HPI-I) and organisations (HPI-O) that underpin My Health Record, e-prescribing and secure messaging.

- **Human URL:** [implementer.digitalhealth.gov.au — HI Service](https://implementer.digitalhealth.gov.au/resources/services/healthcare-identifiers-service-hi)

## Auth Model

- **National record systems** (My Health Record, HI Service, Electronic Prescribing, Secure Messaging): NASH SHA-2 PKI certificates over mutual TLS. A new NASH PKI Chain of Trust begins issuing certificates from August 2026.
- **NCTS terminology server:** SMART-on-FHIR OAuth2 (`authorize` / `token` at `api.healthterminologies.gov.au/oauth2/*`).

Production onboarding is **gated** — registration, developer welcome pack, conformance testing (test environment operated by Deloitte as Gateway Operator), and NASH PKI issuance are required.

## Standards

- HL7 FHIR R4 (4.0.1)
- AU Base / AU Core FHIR Implementation Guides (HL7 Australia / Sparked national FHIR accelerator)
- HL7 CDA (legacy clinical document exchange)

## Common Properties

- [Website](https://www.digitalhealth.gov.au/)
- [Developer Portal](https://developer.digitalhealth.gov.au/)
- [Implementer Hub](https://implementer.digitalhealth.gov.au/)
- [NASH Authentication](https://implementer.digitalhealth.gov.au/resources/services/national-authentication-service-for-health-nash)
- Support: help@digitalhealth.gov.au

## Maintainers

**FN:** Kin Lane
**Email:** kin@apievangelist.com
