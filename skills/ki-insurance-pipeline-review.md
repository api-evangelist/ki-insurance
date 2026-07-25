---
name: Review the Ki broker pipeline
description: Read-only review of a broking house's Ki position — pipeline, dashboard indications and renewals, leads — and export it.
api: openapi/ki-insurance-broker-platform-openapi.yml
operations:
  - getUserCurrent
  - getPipelineList
  - getDashboardIndications
  - getDashboardRenewals
  - getLeadsList
  - getLeadsLead
  - createLeadsActivate
  - createPipelineCsv
generated: '2026-07-25'
method: generated
source: openapi/ki-insurance-broker-platform-openapi.yml
---

# Review the Ki broker pipeline

A read-mostly skill: what is in front of the broking house at Ki right now.
Everything runs against `https://app.ki-insurance.com` with an Auth0 bearer
token; nothing here commits capacity.

## Steps

1. **Establish context.** Call `getUserCurrent` for the broking house and the
   classes of business the account is entitled to.
2. **List the working pipeline.** Call `getPipelineList`. It takes the
   `useDomainModelBasedIndications` flag Ki's own client passes from LaunchDarkly
   — send `false` unless you know the tenant is on the domain model.
3. **Read the dashboard windows.** Call `getDashboardIndications` and
   `getDashboardRenewals` with `days` (the lookback window) and, optionally,
   `statuses` as a comma-joined list. These are the only time-windowed
   operations Ki exposes — there is no pagination anywhere in the API.
4. **Work the leads.** Call `getLeadsList`, then `getLeadsLead` for detail. To
   pull a lead into the working pipeline, call `createLeadsActivate` — this is
   the one write in this skill, and it is reversible only by discarding the
   resulting quote.
5. **Export.** Call `createPipelineCsv` with the quote ids in the JSON body and
   `Accept: application/csv`. The response is a CSV blob, not JSON.

## Notes

- **No pagination.** Lists return in full. Expect large responses and do not
  invent `page`/`limit` parameters — they do not exist.
- **No rate limits are published.** Poll conservatively.
- `401` re-authenticate; `403` means the class of business is outside the
  account's entitlement; `503` is maintenance mode.
- Renewal and indication statuses are not documented by Ki. Read the values back
  from the responses rather than assuming an enumeration.
