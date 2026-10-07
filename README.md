# Postman API Testing Portfolio

Hands-on API testing projects by **Adarsh Kumar M**, QA Engineer / Software Engineer in Test.

This portfolio contains **7 Postman collections, 39 requests, and 6 example environments** covering REST CRUD workflows, authentication, request chaining, dynamic test data, and JavaScript response assertions.

## Projects and coverage

| Collection | Requests | What it demonstrates |
| --- | ---: | --- |
| [Restful Booker](collections/Restful-Booker-CRUD.postman_collection.json) | 9 | List, create, retrieve, authenticate, PUT, PATCH, verify updates, and delete a booking; cookie token authentication |
| [GoRest](collections/GoRest-CRUD.postman_collection.json) | 8 | User CRUD, bearer authentication, generated names/emails, field comparisons, and a 404 check after deletion |
| [Contact List](collections/Contact-List-CRUD.postman_collection.json) | 8 | Login, create/list/retrieve/update/delete contacts, response checks, and logout |
| [Flickr OAuth 1.0](collections/OAuth-Flickr.postman_collection.json) | 4 | Request token, browser authorization, verifier exchange, and signed protected-resource request |
| [Twitter OAuth 1.0](collections/OAuth-Twitter.postman_collection.json) | 4 | Request/access token parsing and OAuth 1.0 signing; historical learning example requiring endpoint/access review |
| [Amadeus OAuth 2.0](collections/OAuth-Amadeus.postman_collection.json) | 1 | Client-credentials token request, token assertion, and environment capture |
| [Scripting Examples](collections/Postman-Scripting-Examples.postman_collection.json) | 5 | Array traversal, allowed-value assertions, partial response checks, request delay, and intentional fail/skip behavior |

## Skills demonstrated

- REST methods: GET, POST, PUT, PATCH, DELETE.
- Status-code, content-type, response-field, and request/response comparison assertions.
- Chaining requests through captured resource IDs and authentication tokens.
- Resolving generated test data once before sending and reusing the same values in assertions.
- Postman collection/environment variables and JavaScript pre-request/post-response scripts.
- Bearer tokens, cookie authentication, OAuth 1.0 signatures, and OAuth 2.0 client credentials.
- Cleanup through DELETE operations; GoRest also verifies that a deleted user returns 404.

These are learning projects against third-party APIs. This repository does not claim production coverage, performance/security testing, data-driven CSV runs, or completed CI integration.

## Repository layout

- `collections/`: importable collection JSON files.
- `environments/`: example environments; API credentials and OAuth tokens are blank.
- `docs/REVIEW-NOTES.md`: cleanup details, test limitations, and special cases.
- `docs/GITHUB-SETUP.md`: publishing instructions.

## Import and run

1. Import the collection JSON into Postman.
2. Import the matching `environments/<project>.example.postman_environment.json`.
3. Select that environment before sending requests. The scripting examples do not need an environment.
4. Fill any required credentials locally as described below.
5. For CRUD workflows, run requests in their numbered order using Collection Runner. Run one iteration first.
6. Inspect the test results and Postman Console. Capture your own run evidence before presenting these as verified against a live API.

Captured CRUD state is stored in collection variables so it is available when requests are sent individually too. Rerun from creation/login to refresh IDs and tokens; GET/PUT/PATCH/DELETE steps depend on earlier requests.

### Restful Booker

Use `Restful-Booker.example.postman_environment.json`. `BaseURI` is also present at collection scope; the environment value takes precedence. The public demo authentication values `admin` / `password123` are retained in the auth request. Authentication runs once at step 4; update/delete steps reuse `tokenId`. Fixed ISO booking dates ensure valid, ordered input while names and other fields remain generated.

### GoRest

Use `GoRest.example.postman_environment.json`. Set `TokenId` to your raw access token; the requests add `Bearer ` themselves. Do not include the prefix twice. Start with user creation and finish with the deleted-user 404 check.

### Contact List

Use `Contact-List.example.postman_environment.json`. The login body retains the author's deliberately shared practice-account email/password. They are test credentials, not recommended credentials for your own account. Prefer replacing them locally with an account you create for this demo service. The login assertions expect the sample account email and first name; update those assertions if using your own account.

This workflow creates and deletes a contact within the selected account. The PUT request is labeled as an update, rather than a partial update; no PATCH request is present in this collection.

### Flickr OAuth 1.0

Use `OAuth-Flickr.example.postman_environment.json`. Supply your own `consumerKey`, `consumerSecret`, and `callbackUrl` matching your app configuration. Run step 1, open the step-2 authorization URL in a browser, approve access, and set `OAuthVerifier` from the callback before step 3. Step 4 uses the captured access token and secret. Browser authorization is manual, so this is not an unattended collection run.

### Twitter OAuth 1.0

Use `OAuth-Twitter.example.postman_environment.json`. Supply your own app credentials, authorize in a browser, and set `verifierToken` before exchanging tokens. The exported protected-resource URL contains `/1.2/statuses/home_timeline.json`; it is preserved as historical practice material and must be checked/replaced against current provider documentation before use. Account access, callback settings, HTTP methods, and endpoints also require live verification. This collection demonstrates the OAuth structure; it is not certified as a working current Twitter integration.

### Amadeus OAuth 2.0

Use `OAuth-Amadeus.example.postman_environment.json`. Supply `clientId` and `clientSecret` for the test API. The single request asks for an access token using `client_credentials`, asserts its presence, and stores `accessToken`. Access tokens expire; this is not a permanent-token flow. No protected-resource CRUD requests are included.

### Scripting examples

The first three examples use httpbin response echoing for assertions. The delay and fail/skip requests retain the exported Beeceptor demo endpoint. The final request **intentionally fails one test and skips another** to demonstrate the APIs; omit it when expecting a green collection run. Availability and response shape of public demo endpoints may change.

## Credential handling

Flickr/Twitter app secrets, GoRest tokens, Amadeus secrets, OAuth verifiers, and captured OAuth tokens are blank in the example environments. A Postman `secret` type masks values in the UI; it does not remove exported values.

Keep filled-in environments local, using a filename ending in `.local.postman_environment.json` (ignored by Git). Do not overwrite and commit the example environments with private credentials. Before re-exporting collections, clear captured authentication variables and check saved examples for sensitive response data.

## Validation status

The prepared files were checked for JSON readability and JavaScript syntax. Script cleanup addresses variable mismatches, duplicate declarations, raw-body parsing, and dynamic-value correlation. No authenticated live API execution was performed during preparation. A green run must be established in Postman with your own account configuration; no CI badges or fabricated run results are included.

## Next improvements

- Record a verified CRUD run and add a sanitized result screenshot.
- Add negative scenarios for validation errors and unauthorized requests.
- Add Newman execution and GitHub Actions after establishing stable, passing workflows.

## Author

[Adarsh Kumar M](https://github.com/Adarsh-Kumar-M) — QA Engineer / Software Engineer in Test.
