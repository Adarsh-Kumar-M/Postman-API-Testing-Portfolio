# Review and cleanup notes

The uploaded exports remain unchanged. These portfolio copies include the following edits:

- Blank Flickr app credentials in the exported example environment, regardless of secret masking.
- Remove empty GoRest environment key and saved response examples.
- Normalize Flickr secret names and OAuth permanent-token spelling in scripts, requests, and environments.
- Remove Twitter's duplicate constant declarations; parse OAuth values by key instead of positional indexes.
- Remove response/token console logging and obsolete commented alternatives.
- Resolve raw request placeholders once in pre-request scripts, send that exact body, and parse the captured body for expected values.
- Use collection variables for persistent CRUD state between individual requests.
- Fix GoRest's missing `reqEmail` capture and `reqName`/`req_Name` mismatch.
- Make GoRest Authorization consistently `Bearer {{TokenId}}`.
- Reuse one Restful Booker `tokenId` after the explicit auth step; remove redundant per-request token generation and inconsistent token names.
- Use ordered ISO booking dates in full Booker create/update requests.
- Rename Booker's delete request and Contact List's PUT request accurately.
- Add token/status assertions and capture to the one-request Amadeus collection; replace the misleading permanent-token label.
- Implement the previously incomplete partial-response assertion using a deterministic httpbin echo payload.
- Identify the deliberately failing scripting request without removing its educational behavior.

## Limits

JSON and JavaScript syntax checks do not establish live correctness. OAuth app permissions, interactive approval, callbacks, service availability, and current endpoint validity still need manual verification. Twitter's original `/1.2/` endpoint is explicitly historical/unverified. The scripting collection's final request intentionally fails. CRUD cleanup only happens when DELETE is reached; interrupted runs may leave demo records behind.

Contact List test credentials were retained at the author's explicit request. Personal/API credentials and tokens in environments were removed from the portfolio copies.
