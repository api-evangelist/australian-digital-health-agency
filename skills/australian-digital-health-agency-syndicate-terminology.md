---
name: Download terminology releases from the NCTS syndication feed
description: Discover and download versioned FHIR terminology bundles (SNOMED CT-AU, AMT, LOINC, RCPA SPIA) from the NCTS National Syndication Server Atom feed.
api: NCTS National Syndication Server
operations:
  - GET /syndication/v1/syndication.xml
---

# Download terminology releases (NCTS National Syndication Server)

Use this to keep a local terminology cache current: read the Atom syndication feed, find the entry for the content you need at the version you need, then download the referenced bundle.

## Base
`https://api.healthterminologies.gov.au/syndication/v1`

## Authentication
SMART-on-FHIR OAuth2 Bearer token (same client credentials as the terminology server). A registered NCTS client account is required.

## Steps
1. Acquire an OAuth2 Bearer access token.
2. Fetch the syndication feed:
   ```
   GET /syndication/v1/syndication.xml
   Authorization: Bearer {token}
   Accept: application/atom+xml
   ```
3. Parse the Atom `entry[]` elements. Filter by the `category[term=...]` content type (e.g. `SCT_RF2_FULL`, `FHIR`, `LOINC`) and read `ncts:contentItemVersion` to select the release version you want.
4. Follow the entry's `link[rel=enclosure]` `href` to download the terminology bundle (FHIR NPM package or RF2 archive).
5. Verify the downloaded artifact against the entry's hash/length metadata, then load it into your terminology store (e.g. import to a local Ontoserver).

## Notes
- The feed is versioned; poll on a cadence and download only entries newer than your last import. See `lifecycle/australian-digital-health-agency-lifecycle.yml`.
- The official .NET syndication client (`ncts-syndication-client-dotnet`) automates this flow; see `packages/australian-digital-health-agency-packages.yml`.
