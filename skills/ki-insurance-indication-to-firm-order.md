---
name: Take an indication through to a firm order note
description: Find an indication for an insured, promote it to a quote, price it, and issue the firm order note that commits Ki's follow line — with mandatory human approval.
api: openapi/ki-insurance-broker-platform-openapi.yml
operations:
  - getQuoteIndicationSuggestions
  - createQuoteFromIndication
  - getQuoteDetail
  - updateQuoteStartPricing
  - getQuoteFonCcEmails
  - createQuoteFirmOrderNoteV2
  - updateQuoteDiscard
generated: '2026-07-25'
method: generated
source: openapi/ki-insurance-broker-platform-openapi.yml
---

# Take an indication through to a firm order note

This is the commit path. The firm order note is where Ki's follow capacity is
actually bound to the risk, so this skill ends in a **human-in-the-loop gate**
that must not be automated away.

## Steps

1. **Find the indication.** Call `getQuoteIndicationSuggestions` with the
   insured name, the domicile country id and the class of business. (Ki gates a
   pre-v2 variant, `getIndicationSuggestionsLegacy`, behind a feature flag — if
   the v2 path 404s for your tenant, fall back to it.)
2. **Promote it.** Call `createQuoteFromIndication` with the `indicationId`.
   Keep the returned `quoteId`.
3. **Confirm the quote.** Call `getQuoteDetail` and check the class of business,
   the nominated lead and the quote lines against what the broker submitted.
4. **Price it.** Call `updateQuoteStartPricing`, then poll `getQuoteDetail`
   every 5 seconds for up to 90 seconds, as Ki's own client does.
5. **Prepare the notice recipients.** Call `getQuoteFonCcEmails` to get the
   firm-order-notice cc addresses configured for that class of business.
6. **STOP. Get human approval.** Present the priced quote — insured, class of
   business, lead syndicate, line size and terms — to an authorised human. Ki's
   line size is bounded server-side by max-line-size configuration you cannot
   see, so a rejection here is a business decision, not a validation error.
7. **Issue the firm order note.** Only after explicit approval, call
   `createQuoteFirmOrderNoteV2` with the `quoteId`. This commits syndicate
   capacity.
8. **If the risk is not taken forward**, call `updateQuoteDiscard` instead.

## Hard rules

- `createQuoteFirmOrderNoteV2` is **never** to be called unattended. It is
  classified as human-in-the-loop required in
  `agentic-access/ki-insurance-agentic-access.yml`.
- **No idempotency key exists.** A timed-out `createQuoteFirmOrderNoteV2` must be
  reconciled with `getQuoteDetail` before any retry — never fire it twice.
- Ki exposes no bind, endorsement, policy-issuance or claims operation. Anything
  after the firm order note happens in the Lloyd's market processes, not in this
  API.
- `403` on the firm order note means the user is not entitled to commit for that
  class of business. Escalate; do not work around it.
