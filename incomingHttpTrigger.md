# Incoming HTTP Trigger


_Starts the workflow when an HTTP-in API request matches the trigger criteria._

## Properties

* **Method** - Choose the HTTP method the trigger will match on. Choose `*` if it should match any method.
* **Token** - Enter a token to execute the trigger. Any token can be used, but preferably a REST API token/authentication token because it has a longer lifetime. Tokens are found and created under `Administrator Tools -> REST API tokens` (format: `00000000-0000-0000-0000-000000000000`). The token can be left empty if you want to support different tokens. ***Optional***
* **Path** - By setting this value, your request must have a matching path. This is preferably used in combination with the subdomain option. ***Optional***
* **Sub domain** - Enables use of a subdomain in front of the normal `in.bosbec.io` domain. ***Optional, but recommended***
* **Is public** - By setting this to "true" the trigger can be triggered without any provided token. It can be a good option when a resource needs to be shared and it is not possible or required to require authentication. Keep in mind that the resource will be available to anyone with the correct path. ***Optional***
* **Incoming http request resource name** - The name where the request resource will be stored when running the workflow.
* **Incoming unit resource name** - The resource name for the related unit when running the workflow.

## Connections

This job can be connected to the following workflow elements.

* Jobs

## Requirements

* The workflow needs to be activated for the trigger to activate.

## Usage

Incoming HTTP traffic first enters an HTTP channel and is then filtered by triggers. A common setup is to keep the channel relatively open for one external system and use trigger settings (method/path) to route requests to the correct workflow.

This trigger reacts to HTTPS requests that match both the channel and trigger criteria.

The request must use an HTTP verb matching what is configured for the trigger (`GET`, `POST`, `DELETE`, ...).

When token is provided you can call either:

* https://in.bosbec.io/2/[YOUR_TOKEN] where [YOUR_TOKEN] is the token.
* https://in.bosbec.io/2 and the token as the header `api-key` or `Authorization` (preferred way).

When a path is provided you can call either:

* https://in.bosbec.io/2/[TOKEN]/[PATH] where [TOKEN] is any valid token, or the provided token.
* https://in.bosbec.io/2/[PATH] and any valid token as the header `api-key` or `Authorization` (preferred way).

When a sub domain is provided you can call:

* https://[domain].in.bosbec.io/[TOKEN] where [TOKEN] is any valid token, or the provided token.
* https://[domain].in.bosbec.io/ and any valid token as the header `api-key` or `Authorization` (preferred way).

When both domain and path is given a request can be formed as below.

* https://[domain].in.bosbec.io/[PATH] and any valid token as the header `api-key` or `Authorization` (preferred way).

When is public is set to `true`:

* The requests are formed as above, but don't require any token


When trying to access data from the incoming request, assuming that the request-resource has name `request1`:

* `{{request1.header.content-type}}` would get the value in the content-type header.
* `{{request1.body}}` gets the body
* `{{request1.headers}}` gets all headers comma-separated
* `{{request1.path}}` gets the path 
* `{{request1.full_path}}` gets the full path
* `{{request1.method}}` gets the method, for example post/get
* `{{request1.querykeys}}` gets the keys in the query as comma-separated
* `{{request1.query.x}}` gets the value for the query-parameter 'x'
* `{{request1.contenttype}}` a shortcut to get the content-type header
* `{{request1.ip}}` gets the requester-ip

## Channels and trigger alignment

The incoming channel and trigger can share overlapping properties, especially method and path.

Recommended approach:

1. Configure the HTTP channel as the broad entry point for a source system.
2. Use one or more triggers to filter by method/path and start specific workflows.

For HTTP channels, the channel-level matching properties are:

* Method
* Subdomain
* Domain
* Path

Channel fields left empty are treated as wildcards and are not required to match.


## Authentication tokens

Authentication tokens must have permission to run the trigger or workflow. When restricting permissions, you can allow only a specific trigger or workflow.

Webhook authentication usually follows one of these modes:

1. Public trigger (no authentication required).
2. Trigger requires a valid token.
3. Trigger requires a specific token.

## Other

If possible, use the API token header instead of adding the token to the request path.
If workflow execution stops before a response is returned, for example after a Remote HTTP Request before API response creation, add the header `processing-until-response: true`. This keeps processing active until a response is created (or timeout is reached).
You can also set a custom timeout with `processing-time-out: 1000`, where the value is milliseconds to wait.

## Testing incoming webhooks

When testing webhook setup, start with a simple trigger/workflow path that returns `200` on successful receipt. After connectivity is verified, add routing, validation, and business logic branches.

## Best practices

* Prefer explicit HTTP methods over `*` unless a single endpoint truly must accept multiple verbs.
* For public endpoints (`Is public = true`), validate input early using `dataOperations` and `routeFromMetaData` before any account updates or external requests.
* Prefer tokens in request headers (`api-key` or `Authorization`) over query strings to reduce leakage through logs and browser history.
* Keep trigger paths stable and descriptive so downstream routing and monitoring stay predictable.
* When building callback endpoints, return a quick response (often `204`) and move heavy processing to asynchronous workflow paths.

## Common trigger patterns

### Public callback endpoint with whitelist validation

Use this pattern for event callbacks where the source system calls your endpoint and only expects acknowledgement.

1. Configure trigger with explicit method and path.
2. Validate critical query values in `routeFromMetaData` using strict regex (whitelist).
3. Route invalid values to a safe fallback branch.
4. Return `204` quickly using `sendApiResponse`.

This keeps callback endpoints deterministic and reduces accidental processing of malformed input.

### Header-first authentication

When the endpoint is not public, prefer header-based auth over path/query token patterns.

* Use `Authorization` or `api-key` headers.
* Keep tokens out of URL paths and query strings.
* Restrict token permissions to only the required trigger or workflow.

## Security notes

* For `Is public = true` triggers, treat all incoming values as untrusted until validated.
* Avoid exposing sensitive values in error responses from public paths.
* If wildcard method (`*`) is enabled, route on `{{request_resource.method}}` early so only expected verbs continue.
