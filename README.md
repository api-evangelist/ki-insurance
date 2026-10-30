# Ki Insurance

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

Ki is the first fully digital, algorithmically driven syndicate at Lloyd's of London, launched in 2020 out of Brit with Google Cloud and University College London and capitalised with US$500m from Blackstone Tactical Opportunities and Fairfax Financial. Operating from the United Kingdom as Lloyd's Syndicate 1618, Ki writes follow-only capacity across specialty lines — property, casualty and specialty — quoting risks that a lead underwriter has already priced, in seconds rather than days, through an algorithm rather than a face-to-face negotiation in the Room. Brokers reach Ki through app.ki-insurance.com, a partner-gated single-page platform behind an Auth0 authorization-code login, and Ki announced a "Broker API" in May 2021 that lets partner broking platforms request quotes directly from the algorithm. That API posture is entirely partner-gated: there is no developer portal, no public reference documentation, no self-serve signup, no provider-published OpenAPI or Postman collection, and no public webhook or event catalog. What is observable is the platform API itself — Ki's own broker client ships a complete endpoint registry in its public JavaScript bundle, exposing a same-origin REST surface of roughly a hundred JSON operations across quotes, quote lines, pricing, schedules of values, slip extraction, leads, pipeline, broking houses, nominated leads and Lloyd's risk codes, all authorised with an Auth0 bearer token. API Evangelist has derived an observed OpenAPI from that bundle. Ki remains the archetype of the United Kingdom's London-market pattern: genuinely advanced machine-to-machine insurance placement infrastructure, aimed at brokers and syndicates rather than at developers, and therefore effectively invisible from the outside.

**Areas:** Insurance · United Kingdom · Lloyd's of London · Specialty Insurance · Property and Casualty · Underwriting · Insurtech · Brokerage · Algorithmic Underwriting · Reinsurance

## Ki Insurance on APIs.io

Everything profiled for Ki Insurance is published on APIs.io rather than in this repository. Start at the provider page — **[apis.io/providers/ki-insurance/](https://apis.io/providers/ki-insurance/)** — or go straight to one of the APIs or properties below.

### APIs (18)

- [Ki Insurance Administration API](https://apis.io/apis/ki-insurance/ki-insurance-administration-api/) — The Administration API from Ki Insurance — 4 operation(s) for administration.
- [Ki Insurance Broking Houses API](https://apis.io/apis/ki-insurance/ki-insurance-broking-houses-api/) — The Broking Houses API from Ki Insurance — 5 operation(s) for broking houses.
- [Ki Insurance Classes of Business API](https://apis.io/apis/ki-insurance/ki-insurance-classes-of-business-api/) — The Classes of Business API from Ki Insurance — 1 operation(s) for classes of business.
- [Ki Insurance Configuration API](https://apis.io/apis/ki-insurance/ki-insurance-configuration-api/) — The Configuration API from Ki Insurance — 1 operation(s) for configuration.
- [Ki Insurance Dashboard API](https://apis.io/apis/ki-insurance/ki-insurance-dashboard-api/) — The Dashboard API from Ki Insurance — 2 operation(s) for dashboard.
- [Ki Insurance Facilities API](https://apis.io/apis/ki-insurance/ki-insurance-facilities-api/) — The Facilities API from Ki Insurance — 4 operation(s) for facilities.
- [Ki Insurance Indications API](https://apis.io/apis/ki-insurance/ki-insurance-indications-api/) — The Indications API from Ki Insurance — 2 operation(s) for indications.
- [Ki Insurance Leads API](https://apis.io/apis/ki-insurance/ki-insurance-leads-api/) — The Leads API from Ki Insurance — 3 operation(s) for leads.
- [Ki Insurance Market Leaders API](https://apis.io/apis/ki-insurance/ki-insurance-market-leaders-api/) — The Market Leaders API from Ki Insurance — 4 operation(s) for market leaders.
- [Ki Insurance Master Data API](https://apis.io/apis/ki-insurance/ki-insurance-master-data-api/) — The Master Data API from Ki Insurance — 39 operation(s) for master data.
- [Ki Insurance Pipeline API](https://apis.io/apis/ki-insurance/ki-insurance-pipeline-api/) — The Pipeline API from Ki Insurance — 2 operation(s) for pipeline.
- [Ki Insurance Quotes API](https://apis.io/apis/ki-insurance/ki-insurance-quotes-api/) — The Quotes API from Ki Insurance — 15 operation(s) for quotes.
- [Ki Insurance Risk Codes API](https://apis.io/apis/ki-insurance/ki-insurance-risk-codes-api/) — The Risk Codes API from Ki Insurance — 1 operation(s) for risk codes.
- [Ki Insurance Schedule of Values API](https://apis.io/apis/ki-insurance/ki-insurance-schedule-of-values-api/) — The Schedule of Values API from Ki Insurance — 2 operation(s) for schedule of values.
- [Ki Insurance Slip Extraction API](https://apis.io/apis/ki-insurance/ki-insurance-slip-extraction-api/) — The Slip Extraction API from Ki Insurance — 5 operation(s) for slip extraction.
- [Ki Insurance Support API](https://apis.io/apis/ki-insurance/ki-insurance-support-api/) — The Support API from Ki Insurance — 1 operation(s) for support.
- [Ki Insurance Telemetry API](https://apis.io/apis/ki-insurance/ki-insurance-telemetry-api/) — The Telemetry API from Ki Insurance — 1 operation(s) for telemetry.
- [Ki Insurance Users API](https://apis.io/apis/ki-insurance/ki-insurance-users-api/) — The Users API from Ki Insurance — 10 operation(s) for users.

### Published properties

Each property below is a page on APIs.io carrying the machine-readable artifact and what it says.

#### Arazzo workflows (2)

Multi-step workflows that chain operations into a business task.

- [Ki — quote a risk and run the follow algorithm](https://apis.io/arazzos/ki-insurance/ki-insurance-quote-and-price/)
- [Ki — turn a broker slip into a quote](https://apis.io/arazzos/ki-insurance/ki-insurance-slip-to-quote/)

#### MCP servers (1)

Model Context Protocol servers that expose the API to agents.

- [ki-insurance](https://apis.io/servers/ki-insurance/ki-insurance/)

#### Agentic access (1)

Which operations an agent can call, which act, and which need a human in the loop.

- [Ki Insurance Agentic Access](https://apis.io/agentic-access/ki-insurance/ki-insurance-agentic-access/)

#### Collections (1)

Postman and Open Collection request collections.

- [Ki Broker Trading Platform API (observed)](https://apis.io/collections/ki-insurance/open-ki-insurance-broker-platform/)

#### Overlays (1)

OpenAPI overlays, including conversational phrasing for each operation.

- [Ki Insurance Broker Platform Overlay](https://apis.io/overlays/ki-insurance/ki-insurance-broker-platform-overlay/)

#### Security (2)

Authentication, trust centre, and vulnerability disclosure.

- [Ki Insurance Authentication](https://apis.io/security/ki-insurance/ki-insurance-authentication/)
- [Ki Insurance Domain Security](https://apis.io/security/ki-insurance/ki-insurance-domain-security/)

#### OAuth scopes (1)

The permissions the API asks for.

- [Ki Insurance Scopes](https://apis.io/scopes/ki-insurance/ki-insurance-scopes/)

## Where to find this API

Links to the company's own pages. This repository publishes no copy of their specifications — the canonical document is theirs and lives at the URLs below.

- [Website](https://ki-insurance.com/)
- [Sign up](https://app.ki-insurance.com/)
- [Blog](https://ki-insurance.com/news/)
- [Terms of service](https://app.ki-insurance.com/policies/2025/11/16/Ki_Website_Terms.pdf)
- [Privacy policy](https://app.ki-insurance.com/policies/2025/V2/Ki_Privacy_Policy.pdf)
- [GitHub](https://github.com/Ki-Insurance)

## API Evangelist rating

**Kin Score 21.5** — emerging · rubric 0.24.0 · scored 2026-10-17

| Facet | Score |
|---|---|
| Discoverability | 73.2 |
| Contract quality | 14.3 |
| Contract governance | 4.5 |
| Operational transparency | 2.6 |
| Developer ergonomics | 16.1 |
| Access clarity | 21.1 |

**Agent readiness 31.5** — agent-ready

| Agent-readiness dimension | Result |
|---|---|
| Spec Presence | yes |
| Agentic Access | derived (partial credit) |
| Reversibility Documented | — |
| MCP Server | — |
| Auth Clarity | served (partial credit) |
| Idempotency | — |
| Error Semantics | derived (partial credit) |
| OpenAPI Examples | — |
| Rate Limit Signal | — |
| Event Surface Described | — |
| Agent Skills | derived (partial credit) |
| Well Known Catalog | — |
| Consent Identity | — |
| Agent Card | — |
| Dry Run Mode | — |
| Delegated Identity | served (partial credit) |
| Protected Resource Metadata | — |
| Dynamic Client Registration | yes |
| Agentic Commerce | — |

**Regulatory alignment 36.8** — Insurance

The rubric is published at [github.com/api-evangelist/kin-score](https://github.com/api-evangelist/kin-score). The per-check breakdown behind these numbers — which checks were earned, partial or missed — along with score history and how this provider compares to its peers, is available at [apis.io/providers/ki-insurance/](https://apis.io/providers/ki-insurance/).

## How this profile is made

API Evangelist profiles a company's public API surface the way a developer would find it: the website, developer portal and documentation, the specifications it publishes, its public repositories, and its pricing, status and changelog pages. From that it derives the properties above — contracts split per API, workflows, schemas, collections, governance rules, plans and rate limits — and scores them against the published [Kin Score rubric](https://github.com/api-evangelist/kin-score).

The artifacts are published on [APIs.io](https://apis.io), not in this repository. This repository is the public record for Ki Insurance: the place to say something is wrong, missing or out of date, and to ask for a re-score or a removal.

## Open an issue

- **Something about this listing** — a wrong description, a missing API, a stale artifact or a question about the rating: [open an issue on this repository](https://github.com/api-evangelist/ki-insurance/issues/new).
- **A new API, or one that is not in the catalog yet** — [submit it on APIs.io](https://apis.io/add/).
- **Anything else** — [the APIs.io inbox](https://github.com/api-search/inbox/issues/new) or [info@apievangelist.com](mailto:info@apievangelist.com).
