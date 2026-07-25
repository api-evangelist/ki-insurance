---
name: Turn a broker slip into a Ki quote
description: Upload a broker slip, run Ki's slip extraction job, poll it to completion and create a quote from the extracted result.
api: openapi/ki-insurance-broker-platform-openapi.yml
operations:
  - createSlipExtractionUpload
  - createSlipExtractionExecuteSlipExtractionJob
  - getSlipExtractionJobStatus
  - getSlipExtractionJobResult
  - createSlipExtractionQuoteFromJobResult
  - getQuoteDetail
generated: '2026-07-25'
method: generated
source: openapi/ki-insurance-broker-platform-openapi.yml
---

# Turn a broker slip into a Ki quote

Ki's slip extraction pipeline reads a broker slip document and produces
structured quote input. It is a three-call job with a polling loop, then a
promotion step. Partner-gated: an Auth0 bearer token for audience
`https://api.ki.com` is required on every call against
`https://app.ki-insurance.com`.

## Steps

1. **Create the upload.** Call `createSlipExtractionUpload` to register the slip
   document. The body is the document; the response identifies the upload.
2. **Execute the job.** Call `createSlipExtractionExecuteSlipExtractionJob`.
   Keep the returned `jobId`.
3. **Poll to completion.** Call `getSlipExtractionJobStatus` with the `jobId` on
   a backoff. There is no webhook and no completion callback — polling is the
   only mechanism Ki exposes.
4. **Read the result.** When the status reports completion, call
   `getSlipExtractionJobResult` with the `jobId`.
5. **Review before promoting.** Extraction from a scanned or free-text slip is
   probabilistic. Surface the extracted fields to the underwriter or broker for
   confirmation — do not promote silently.
6. **Create the quote.** Call `createSlipExtractionQuoteFromJobResult` with the
   `jobId`. Then continue with `ki-insurance-quote-and-price.md` from the risk
   details step: confirm with `getQuoteDetail`, attach the schedule of values if
   the line needs one, and run `updateQuoteStartPricing`.

## Rules

- **No idempotency.** Re-executing a job for the same upload may create a second
  job. Track the `jobId` you already have before retrying.
- **Poll politely.** Ki publishes no rate limits, which is a reason to be
  conservative, not a licence to be aggressive.
- `401` re-authenticate once; `403` means the class of business is not in your
  entitlement; `503` is platform maintenance — back off.
- Ki publishes no schema for the extraction result. Do not hard-code field paths
  without a fallback.
