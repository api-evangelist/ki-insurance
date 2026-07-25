# Ki Insurance (ki-insurance)

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

None listed. Ki has a real machine-to-machine API — the "Broker API" it announced on 4 May 2021, which lets partner broking platforms request follow-capacity quotes directly from Ki's algorithm — but it is entirely partner-gated. Ki publishes no developer portal, no API reference, no base URL, no self-serve signup, and no downloadable OpenAPI, Swagger, GraphQL SDL, AsyncAPI, webhook catalog or Postman collection.

Every candidate developer host was probed on 2026-07-25 and none resolves: `developer.`, `developers.`, `docs.`, `api.`, `platform.`, `broker-api.` and `sandbox.ki-insurance.com` all fail DNS, and `/developers`, `/api`, `/developer`, `/partners`, `/integrations` and `/brokers` on ki-insurance.com all return HTTP 404. The only live application surface is `app.ki-insurance.com` (HTTP 200), the authenticated broker trading platform, which sits behind an Auth0 authorization-code login — a login wall, not a developer portal. Requests to `/openapi.json`, `/swagger.json` and `/graphql` on that host return HTTP 200 but serve the single-page app's HTML, not a specification.

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

## Review

See [review.yml](review.yml) for the full API Evangelist reviewer finding, including every probed URL and its HTTP status.
