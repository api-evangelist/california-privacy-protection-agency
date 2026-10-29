# California Privacy Protection Agency

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

The California Privacy Protection Agency (CPPA, branded CalPrivacy) is the state regulator that administers and enforces the California Consumer Privacy Act and the Delete Act. Under the Delete Act it operates DROP, the Delete Request and Opt-out Platform, through which California residents file a single deletion request that every registered data broker must process at least once every 45 days beginning August 1, 2026. Data brokers integrate with DROP through the DROP Data Broker API, a three-operation REST surface on api.drop.privacy.ca.gov (download hashed consumer deletion lists as a ZIP of CSVs, upload Id,Status response files, amend prior responses) authenticated with an X-API-KEY issued in the Data Broker Portal, with a sandbox environment, HMAC-SHA256 signed webhook notifications, and an OpenAPI 3.1.0 contract published alongside the technical specifications on privacy.ca.gov. The agency also publishes the California Data Broker Registry as downloadable CSV files.

**Areas:** Government · Privacy · Data Brokers · Regulatory Compliance · Data Deletion · Consumer Rights · California · Webhook

## California Privacy Protection Agency on APIs.io

Everything profiled for California Privacy Protection Agency is published on APIs.io rather than in this repository. Start at the provider page — **[apis.io/providers/california-privacy-protection-agency/](https://apis.io/providers/california-privacy-protection-agency/)** — or go straight to one of the APIs or properties below.

### APIs (3)

- [DROP Webhook Notifications](https://apis.io/apis/california-privacy-protection-agency/drop-webhook-notifications/) — Optional outbound HTTPS webhook notifications from DROP to a data broker's endpoint, enabled in the Data Broker Portal notification settings. Five event…
- [California Privacy Protection Agency Download API](https://apis.io/apis/california-privacy-protection-agency/california-privacy-protection-agency-download-api/) — Request or download consumer deletion lists(s)
- [California Privacy Protection Agency Upload API](https://apis.io/apis/california-privacy-protection-agency/california-privacy-protection-agency-upload-api/) — Submit new or amended status response files

### Published properties

Each property below is a page on APIs.io carrying the machine-readable artifact and what it says.

#### AsyncAPI (1)

Event-driven and webhook contracts.

- [California Privacy Protection Agency Drop Webhooks](https://apis.io/asyncapis/california-privacy-protection-agency/california-privacy-protection-agency-drop-webhooks/)

#### MCP servers (1)

Model Context Protocol servers that expose the API to agents.

- [DROP Data Broker API (candidate MCP tool surface)](https://apis.io/servers/california-privacy-protection-agency/drop-data-broker-api-candidate-mcp-tool-surface/)

#### Overlays (1)

OpenAPI overlays, including conversational phrasing for each operation.

- [California Privacy Protection Agency Drop Data Broker Api Overlay](https://apis.io/overlays/california-privacy-protection-agency/california-privacy-protection-agency-drop-data-broker-api-overlay/)

#### Security (3)

Authentication, trust centre, and vulnerability disclosure.

- [California Privacy Protection Agency Authentication](https://apis.io/security/california-privacy-protection-agency/california-privacy-protection-agency-authentication/)
- [California Privacy Protection Agency Domain Security](https://apis.io/security/california-privacy-protection-agency/california-privacy-protection-agency-domain-security/)
- [California Privacy Protection Agency Vulnerability Disclosure](https://apis.io/security/california-privacy-protection-agency/california-privacy-protection-agency-vulnerability-disclosure/)

#### Plans and pricing (1)

Published plans, tiers and prices.

- [California Privacy Protection Agency Plans Pricing](https://apis.io/plans/california-privacy-protection-agency/california-privacy-protection-agency-plans-pricing/)

#### Rate limits (1)

Published request limits.

- [California Privacy Protection Agency Rate Limits](https://apis.io/rate-limits/california-privacy-protection-agency/california-privacy-protection-agency-rate-limits/)

## Where to find this API

Links to the company's own pages. This repository publishes no copy of their specifications — the canonical document is theirs and lives at the URLs below.

- [Website](https://cppa.ca.gov/)
- [Documentation](https://privacy.ca.gov/drop-for-data-brokers/technical-specifications/)
- [Getting started](https://privacy.ca.gov/drop-for-data-brokers/technical-specifications/getting-started/)
- [API reference](https://privacy.ca.gov/drop-for-data-brokers/technical-specifications/api-operations/)
- [Pricing](https://privacy.ca.gov/drop-for-data-brokers/account-creation-fees-and-annual-registration/)
- [Support](https://privacy.ca.gov/drop-for-data-brokers/help/)
- [Changelog](https://privacy.ca.gov/drop-for-data-brokers/technical-specifications/reference/#history)
- [Blog](https://privacy.ca.gov/about-us/blog/)
- [Terms of service](https://www.ca.gov/legal/conditions-of-use/)
- [Privacy policy](https://privacy.ca.gov/privacy-policy/)

## API Evangelist rating

**Kin Score 56.3** — strong · rubric 0.25.0 · scored 2026-10-23

| Facet | Score |
|---|---|
| Discoverability | 67.0 |
| Contract quality | 58.8 |
| Contract governance | 18.2 |
| Operational transparency | 34.2 |
| Developer ergonomics | 66.1 |
| Access clarity | 65.8 |

**Agent readiness 41.0** — agent-native

| Agent-readiness dimension | Result |
|---|---|
| Spec Presence | yes |
| Agentic Access | — |
| Reversibility Documented | — |
| MCP Server | — |
| Auth Clarity | bearer (partial credit) |
| Idempotency | documented (partial credit) |
| Error Semantics | verified |
| OpenAPI Examples | verified |
| Rate Limit Signal | verified |
| Event Surface Described | yes |
| Agent Skills | derived (partial credit) |
| Well Known Catalog | — |
| Consent Identity | — |
| Agent Card | — |
| Dry Run Mode | — |
| Delegated Identity | — |
| Protected Resource Metadata | — |
| Dynamic Client Registration | — |
| Agentic Commerce | — |
| Pagination Ratio | na |
| Operation Distinctiveness | distinct |

**Regulatory alignment 30.4** — Government & Public Sector

The rubric is published at [github.com/api-evangelist/kin-score](https://github.com/api-evangelist/kin-score). The per-check breakdown behind these numbers — which checks were earned, partial or missed — along with score history and how this provider compares to its peers, is available at [apis.io/providers/california-privacy-protection-agency/](https://apis.io/providers/california-privacy-protection-agency/).

## How this profile is made

API Evangelist profiles a company's public API surface the way a developer would find it: the website, developer portal and documentation, the specifications it publishes, its public repositories, and its pricing, status and changelog pages. From that it derives the properties above — contracts split per API, workflows, schemas, collections, governance rules, plans and rate limits — and scores them against the published [Kin Score rubric](https://github.com/api-evangelist/kin-score).

The artifacts are published on [APIs.io](https://apis.io), not in this repository. This repository is the public record for California Privacy Protection Agency: the place to say something is wrong, missing or out of date, and to ask for a re-score or a removal.

## Open an issue

- **Something about this listing** — a wrong description, a missing API, a stale artifact or a question about the rating: [open an issue on this repository](https://github.com/api-evangelist/california-privacy-protection-agency/issues/new).
- **A new API, or one that is not in the catalog yet** — [submit it on APIs.io](https://apis.io/add/).
- **Anything else** — [the APIs.io inbox](https://github.com/api-search/inbox/issues/new) or [info@apievangelist.com](mailto:info@apievangelist.com).
