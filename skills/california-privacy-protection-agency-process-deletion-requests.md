---
name: california-privacy-protection-agency-process-deletion-requests
description: Run one DROP download-match-upload cycle for a registered data broker — pull the hashed consumer deletion lists, match them against standardized and hashed local records, and report a status for every work item within the statutory window.
api: DROP Data Broker API
base_url: https://api.drop.privacy.ca.gov
sandbox_url: https://api.drop.privacy.ca.gov/sandbox
generated: '2026-09-17'
method: generated
source: openapi/california-privacy-protection-agency-drop-data-broker-api-openapi.yml + https://privacy.ca.gov/drop-for-data-brokers/technical-specifications/integration-workflow/
operations:
  - downloadData
  - uploadData
  - uploadAmend
---

# Process DROP deletion requests

Use this when a data broker registered with CalPrivacy needs to complete its recurring Delete Act
cycle. From August 1, 2026 every registered broker must access DROP at least once every 45 calendar
days, download its consumer deletion lists, delete or opt out matching consumers, and report a
status per work item. The whole API is three operations; the work is in the matching.

## Credential

Send `X-API-KEY: <key>` on every request. The key is issued in the Data Broker Portal
(https://databroker.drop.privacy.ca.gov/) only after the account is approved, the registration or
access fee is paid, and at least one consumer deletion list is selected. A sandbox key is issued
separately under SANDBOX ENVIRONMENT and is used against `/sandbox`. There is no OAuth and no scope
vocabulary. `401` means the key is wrong; `403` means the account is not eligible or has selected
no lists — neither is retryable until a human fixes the account.

## Steps

1. **Rehearse in the sandbox first.** Point the same three calls at
   `https://api.drop.privacy.ca.gov/sandbox` with a sandbox key, and check your hashing against the
   published vectors in `sandbox/california-privacy-protection-agency-sandbox.yml` (or the portal's
   Standardization and Hashing Tool). A wrong standardization rule silently yields "not found" for
   every consumer, which is a compliance failure, not an API error.
2. **Request the batch.** Call `downloadData` (`GET /data/download`) with
   `Accept: application/zip, application/json`. Handle three outcomes: `202` — the ZIP is being
   prepared, wait `Retry-After` seconds (example 60) and call again; `200 application/json` — nothing
   new since the last completed batch, stop; `200 application/zip` — save the archive
   (`Content-Disposition` names it `<YYYYMMDD>_<DataBrokerId>_DROP.zip`). A `409` means the previous
   batch still has outstanding responses: finish step 5 for it before requesting again.
3. **Read the files.** The ZIP holds one CSV per selected list (`NDZ`, `Email`, `Phone`, `MAID`,
   `NameVIN`, `CTVID`) with header `ID,Hash`, header-only when empty, plus an optional
   `..._Removed.csv` (`ID,Hash,ListType`) of identifiers consumers have withdrawn. Work item IDs are
   12-character case-sensitive Base62 strings and are permanent; keep them.
4. **Standardize, hash, match.** Apply the per-field rules (email: strip whitespace, lowercase;
   phone: digits only, last 10; DOB: `YYYYMMDD`; ZIP: alphanumerics, drop +4, drop leading zeros,
   first five; names: Unicode-normalized, lowercase, letters and digits only; MAID 32 hex; VIN 17
   alphanumerics; CTVID 8–32 alphanumerics), SHA-256 over UTF-8, Base64. `NDZ` and `NameVIN` are
   composite: hash each field, concatenate the Base64 hashes in order, hash again. Compare against
   the `Hash` column. Then act: delete non-exempt data for matches (and direct service providers to
   do the same), opt out when one identifier maps to several consumers, keep the identifiers of
   non-matches to screen future records.
5. **Report status.** Build `Id,Status` CSVs — status `2` exempted, `3` deleted, `4` opted out,
   `5` not found — named after the downloaded file (`20260312_4821_Email.csv`), or with an
   `_<suffix>` of up to 10 alphanumerics to split a list across uploads. Call `uploadData`
   (`POST /data/upload`) as `multipart/form-data` with one or more parts in the field `files`. A `202`
   returns `acceptedCount`, `rejectedCount`, `accepted[]` and `rejected[]`; a `400` means nothing was
   accepted — read `rejected[].message` (wrong header, wrong type, unreadable, duplicate name). Row
   level validation continues after the 202 and its outcome arrives by email (or the optional
   `upload.processed` webhook). The batch is complete only when every outstanding work item has a
   status.
6. **Correct if needed.** To change a status already reported, call `uploadAmend`
   (`POST /data/amend`) with the same file format. This is the only reversal path in the API and no
   time window is published for it; a `409` says the amend cannot be processed in the current state.
7. **Repeat within 45 days.** Schedule the next `downloadData` so that no more than 45 calendar
   days pass between accesses; after the first completed cycle each download contains only new or
   removed identifiers.

## Rules the API enforces

- **Retries.** `429` — wait `Retry-After` (30 s) and retry. `500` — retry later. `400`, `401`,
  `403`, `404`, `409` — do not retry until the cause is fixed.
- **Replay protection.** Re-uploading a file name already accepted for the current download is
  rejected with the duplicate-file message; treat that specific rejection as "already accepted",
  not as a failure. There is no Idempotency-Key header.
- **No raw identifiers.** DROP never returns plaintext consumer data; do not attempt to reverse
  hashes or log them alongside matched records.
- **Connection failures are reportable.** If the automated connection fails, the broker must
  notify CalPrivacy in writing through its DROP account within 45 days (Cal. Code Regs. tit. 11
  § 7612(b)(1)).

## References

- API operations: https://privacy.ca.gov/drop-for-data-brokers/technical-specifications/api-operations/
- Working with the data (schemas, hashing): https://privacy.ca.gov/drop-for-data-brokers/technical-specifications/working-with-data/
- Errors: `errors/california-privacy-protection-agency-problem-types.yml`
- Conventions, idempotency, reversibility: `conventions/california-privacy-protection-agency-conventions.yml`
