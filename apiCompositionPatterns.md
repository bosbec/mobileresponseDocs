# API Composition Patterns

This guide describes reusable, customer-agnostic workflow composition patterns for building HTTP APIs with jobs and triggers.

## Pattern 1: Request Parse -> Validate -> Process -> Respond

Use this as the default API composition.

1. `incomingHttpTrigger`
2. `parseJsonToResource`
3. `routeFromMetaData` (validate required values)
4. Business jobs (`unitPipeline`, `dataOperations`, `jsonPipeline`)
5. `sendApiResponse`

Best practice:

* Keep validation branches explicit.
* Return consistent status codes for the same error class.
* Build response payloads in `jsonPipeline` instead of returning internal resources directly.

## Pattern 2: Callback Endpoint Acknowledgement

Use for event callbacks where the caller only expects acknowledgement.

1. `incomingHttpTrigger` (public callback path)
2. `routeFromMetaData` whitelist checks for query/status values
3. Optional logging/tagging
4. `sendApiResponse` with `204` and empty body

Best practice:

* Acknowledge quickly, do heavy work asynchronously.
* Treat all public callback input as untrusted until validated.

## Pattern 3: External API Request with Bounded Retry

Use when external requests can fail transiently.

1. `sendHttpRequest`
2. Unsuccessful branch -> `routeFromMetaData` on status code
3. `dataOperations` retry counter increment
4. Retry gate in `routeFromMetaData`
5. Retry path or terminal fallback path

Best practice:

* Keep retries bounded.
* Tag terminal failures with non-sensitive labels.
* Avoid endless loops.

## Pattern 4: Loop-Driven Processing with Checkpointing

Use for incremental processing of collections or event history.

1. Find/load resource in `unitPipeline`
2. `forEachResourceStart`
3. Validate current item (`routeFromMetaData`)
4. Process only newer/eligible items
5. Update checkpoint metadata
6. Persist updates (`saveToAccount`) and exit loop (`forEachResourceStop`)

Best practice:

* Validate each item before expensive calls.
* Store checkpoints only after successful processing.

## Pattern 5: HTML Response Endpoints

Use when workflow endpoints deliver pages instead of JSON payloads.

1. `incomingHttpTrigger`
2. Optional metadata extraction (`dataOperations`)
3. `sendApiResponse` with `text/html`

Best practice:

* Sanitize all dynamic values inserted into HTML.
* Avoid exposing secrets or auth tokens in rendered URLs.
* Use `302` only when redirect semantics are intentional.

## Related Docs

* `incomingHttpTrigger.md`
* `parseJsonToResource.md`
* `routeFromMetaData.md`
* `sendHttpRequest.md`
* `sendApiResponse.md`
* `forEachResourceStart.md`
* `forEachResourceStop.md`
* `jsonPipeline.md`
* `dataOperations.md`
