# Ki Insurance (ki-insurance)

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
> **On a security or compliance team?** Email
> [info@apievangelist.com](mailto:info@apievangelist.com) with *security* in the subject line and
> you will get a person, not a form. We will tell you exactly which public URLs this profile was
> built from so your team can see the same surface we did, and we will take the listing down on
> request while you work through it.
>
> Full detail: **[Where this data comes from](https://apievangelist.com/about/where-our-data-comes-from)**
<!-- API-EVANGELIST-PROVENANCE:END -->

Ki is the first fully digital, algorithmically driven syndicate at Lloyd's of London — Syndicate 1618 — launched in 2020 out of Brit with Google Cloud and University College London, and capitalised with US$500m from Blackstone Tactical Opportunities and Fairfax Financial. Operating from the United Kingdom, Ki writes follow-only capacity across property, casualty and specialty lines, quoting risks a lead underwriter has already priced in seconds rather than days.

**APIs.json:** [https://raw.githubusercontent.com/api-evangelist/ki-insurance/refs/heads/main/apis.yml](https://raw.githubusercontent.com/api-evangelist/ki-insurance/refs/heads/main/apis.yml)

## Tags

- Insurance
- United Kingdom
- Lloyd's of London
- Specialty Insurance
- Property and Casualty
- Underwriting
- Insurtech
- Broker
- Algorithmic Underwriting
- Reinsurance

## Timestamps

- **Created:** 2026-07-25
- **Modified:** 2026-07-25

## APIs

**Ki Broker Trading Platform API** — partner-gated, base URL `https://app.ki-insurance.com`.

Ki publishes no developer portal, no API reference, no self-serve signup and no OpenAPI. Every candidate developer host was probed and none resolves: `developer.`, `developers.`, `docs.`, `api.`, `platform.`, `broker-api.` and `sandbox.ki-insurance.com` all fail DNS, and `/developers`, `/api`, `/developer`, `/partners`, `/integrations` and `/brokers` on ki-insurance.com all return HTTP 404. The only live application surface is `app.ki-insurance.com`, the authenticated broker trading platform behind an Auth0 authorization-code login. `/openapi.json`, `/swagger.json` and `/graphql` on that host return HTTP 200 but serve the single-page app's HTML — catch-all false positives, explicitly rejected. `api.ki.com`, the OAuth audience Ki publishes in its runtime config, is a parked page, not a host.

What *is* observable is the platform API itself. Ki's own broker client ships a complete endpoint registry in its public JavaScript bundle, together with the `GET`/`POST`/`PUT`/`DELETE` helpers that call it. API Evangelist derived an OpenAPI from that bundle: **102 paths, 109 operations** across quotes, quote lines, algorithmic pricing, schedules of value, slip extraction, leads, pipeline, users, broking houses, branches, nominated lead syndicates and insurers, Lloyd's risk codes, facilities, and 38 class-of-business master-data lookups. Paths, methods, query-parameter names, the `Authorization: Bearer` scheme, the JSON content negotiation and the 401/403/503 semantics are verbatim observations. Request and response schemas are **not** published by Ki and were deliberately left unspecified rather than invented — [openapi/ki-insurance-broker-platform-openapi.yml](openapi/ki-insurance-broker-platform-openapi.yml) is an API Evangelist derivation, not a Ki contract.

Notable gaps the derivation makes concrete: no idempotency contract on any write (including the firm order note that commits capacity), no pagination on any list, no RFC 9457 problem details or error registry, no rate-limit documentation, no webhooks or events, no sandbox, no status page, no deprecation policy, and no published scope model — authorisation is role and class-of-business entitlement enforced server-side and surfaced only as HTTP 403.

**ACORD posture:** no ACORD reference found. Neither ACORD, AL3, ACORD XML, NGDS nor IVANS appears anywhere on Ki's public site or its 30 press releases. As a Lloyd's follow syndicate, Ki's market plumbing runs through Lloyd's own modernisation programme — Blueprint Two, the Core Data Record, PPL/Whitespace electronic placement — rather than through published ACORD assets. The one standards signal Ki emits publicly is a GitHub fork of [OasisLMF/OpenDataTransform](https://github.com/Ki-Insurance/OpenDataTransform), the open catastrophe exposure-data (OED) transformation tool.

Ki is the archetype of the United Kingdom's London-market pattern: genuinely advanced machine-to-machine insurance placement infrastructure, built for brokers and syndicates rather than for developers, and therefore invisible from the outside.

## Links

- [Website](https://ki-insurance.com/)
- [About](https://ki-insurance.com/about/)
- [News](https://ki-insurance.com/news/)
- [Capacity Partners](https://ki-insurance.com/capacity-partners/)
- [Broker Platform (login)](https://app.ki-insurance.com/)
- [OIDC Discovery](https://login.ki-insurance.com/.well-known/openid-configuration)
- [GitHub](https://github.com/Ki-Insurance)
- [LinkedIn](https://www.linkedin.com/company/ki-insurance)

## Artifacts

- [OpenAPI (derived)](openapi/ki-insurance-broker-platform-openapi.yml) · [Overlay](overlays/ki-insurance-broker-platform-overlay.yaml)
- [Authentication](authentication/ki-insurance-authentication.yml) · [OAuth scopes](scopes/ki-insurance-scopes.yml) · [Well-known](well-known/ki-insurance-well-known.yml)
- [Conventions](conventions/ki-insurance-conventions.yml) · [Error catalog](errors/ki-insurance-problem-types.yml) · [Lifecycle](lifecycle/ki-insurance-lifecycle.yml) · [Conformance](conformance/ki-insurance-conformance.yml)
- [Data model](data-model/ki-insurance-data-model.yml) · [Domain security](security/ki-insurance-domain-security.yml) · [Agentic access](agentic-access/ki-insurance-agentic-access.yml)
- [MCP (candidate)](mcp/ki-insurance-mcp.yml) · [Tool crosswalk](mcp/ki-insurance-tool-crosswalk.yml) · [Agent skills](skills/_index.yml) · [Arazzo workflows](arazzo/_index.yml)
- [llms.txt](llms/ki-insurance-llms.txt)

## Review

See [review.yml](review.yml) for the full API Evangelist reviewer finding, including every probed URL and its HTTP status, and the 2026-07-25 enrichment round that overturned the "no spec" conclusion.
