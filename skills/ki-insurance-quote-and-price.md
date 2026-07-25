---
name: Quote a risk and run Ki's follow algorithm
description: Create a quote on Ki's broker platform, attach the schedule of values, run the algorithmic pricing and retrieve the priced quote document.
api: openapi/ki-insurance-broker-platform-openapi.yml
operations:
  - getUserCurrent
  - getClassOfBusiness
  - getSyndicateNominatedSyndicateByClassOfBusiness
  - getRiskCodes
  - createQuote
  - updateQuoteById
  - createQuoteSov
  - createQuoteProcessSov
  - updateQuoteStartPricing
  - getQuoteDetail
  - getQuotePdf
generated: '2026-07-25'
method: generated
source: openapi/ki-insurance-broker-platform-openapi.yml
---

# Quote a risk and run Ki's follow algorithm

Ki is a **follow-only** Lloyd's syndicate (Syndicate 1618). You are never pricing
the risk from scratch — a lead underwriter has already priced it, and Ki's
algorithm decides whether and at what line size to follow. Everything below runs
against the partner-gated broker platform.

## Before you start

- **Access is partner-gated.** There is no self-serve signup. You need an Auth0
  authorization-code login against issuer `https://login.ki-insurance.com/` for
  audience `https://api.ki.com`, granted to your broking house by Ki.
- Send `Authorization: Bearer <access token>`, `Accept: application/json` and
  `Content-Type: application/json` on every call. Base URL is
  `https://app.ki-insurance.com`.
- **There is no idempotency contract.** No `Idempotency-Key` header exists. Do
  not blindly retry a `POST` — re-check state with `getQuoteById` first.
- **There are no webhooks.** Every asynchronous step is polled.
- Ki publishes no request or response schemas. Treat the payload shapes you
  observe as unstable and never hard-code them.

## Steps

1. **Confirm who you are and what you may write.** Call `getUserCurrent`. The
   returned user carries the broking house and the classes of business the
   account is entitled to; a class you are not entitled to comes back as `403`.
2. **Resolve the class of business.** Call `getClassOfBusiness` and pick the
   `classOfBusinessId` for the risk.
3. **Check the lead.** Call `getSyndicateNominatedSyndicateByClassOfBusiness`
   with the class of business (pass `newBusiness=true` for new business) to
   confirm Ki follows the nominated lead on this risk. If the lead is not in the
   list, Ki will not follow.
4. **Get the risk codes.** Call `getRiskCodes` with the class of business,
   `inceptionDate`, and `nominatedLeadsOnly` / `nonExcess` as appropriate.
5. **Create the quote.** Call `createQuote`. Keep the returned `quoteId` — every
   subsequent step is scoped to it.
6. **Fill in risk details.** Call `updateQuoteById` with the risk detail payload.
   Master-data enumerations for the form come from the `/api/masterdata/*`
   lookups (perils, occupancies, locations, territories, HQ country/state lists,
   cyber and contingency bases, and so on) — read them, do not invent values.
7. **Attach the schedule of values** (property and other SOV-bearing lines).
   Call `createQuoteSov` with the spreadsheet as a multipart body; use
   `updateQuoteSov` to replace an existing one. For the hosted import surface,
   `createOttoSovStart` returns the upload session.
8. **Geocode the exposure.** Call `createQuoteProcessSov` with the `quoteId` and
   `quoteLineId`. This starts a job — poll `getQuoteDetail` until the geocoding
   result appears.
9. **Run the algorithm.** Call `updateQuoteStartPricing` with the `quoteId`.
   Pricing is asynchronous.
10. **Poll for the price.** Poll `getQuoteDetail` every **5 seconds** for up to
    **90 seconds** — those are Ki's own client settings
    (`GET_PRICING_INTERVAL` / `GET_PRICING_TIMEOUT`). Give up and surface an
    error rather than hammering the endpoint.
11. **Retrieve the document.** Call `getQuotePdf`. It returns a binary body, not
    JSON — branch on the response `Content-Type` exactly as Ki's client does.

## Error handling

- `401` — the token is expired or rejected. Re-run the login and retry once.
- `403` — the user is not entitled to this class of business or resource. Do not
  retry; escalate to the broking-house administrator.
- `503` — Ki has put the platform into maintenance mode. Back off; there is no
  public status page to watch.
- There is **no** RFC 9457 problem+json and no error-code registry. Branch on
  status only.

## Do not

- Do not commit capacity from this skill. Issuing the firm order note is a
  separate, human-approved step — see `ki-insurance-indication-to-firm-order.md`.
- Do not call the administration operations (`updateAdminSettings`,
  `updateAdminMaintenance`, `createAdminUploadMaxLineSize`); max line size bounds
  how much capacity Ki writes.
