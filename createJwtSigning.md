# Create JWT Signing

The Create JWT Signing job creates a signed JWT (JSON Web Token) by signing a payload with a private key. Use it when a workflow needs to generate a token for authenticating against an external API or for sending signed claims to another system.

## Properties

The properties for configuring the signing are described below.

* **Payload** (required)
	* JWT payload to sign. This is typically a JSON object containing the claims that should be included in the token.
* **Private key** (required)
	* Private key used to sign the JWT.
* **Destination** (required)
	* Workflow context destination where the signed JWT will be stored.

## Referencing syntax

Payload, key, and destination can be built from workflow values.

* Use expressions such as `{{metadata.claims_json}}` when the payload is prepared earlier in the workflow.
* Use expressions such as `{{metadata.private_key}}` if the private key is resolved from workflow context.
* Store the result in a destination that later jobs can reference, for example a metadata key used by a request-building step.

## Signing behavior

The job signs the provided payload and writes the resulting token to the chosen destination.

* The **Payload** should contain the claims required by the target system.
* The **Private key** must be the key material expected by the signing implementation.
* The resulting token can then be inserted into headers, request bodies, or other workflow values.

## Best practices and tips

* Build and validate the payload before signing so the resulting token contains only the claims you intend to send.
* Keep the payload focused on the minimum claims the target system actually requires. Smaller claim sets are easier to review and reduce unnecessary data sharing.
* Store private keys securely and inject them from controlled workflow sources rather than hardcoding them broadly in multiple jobs.
* Prefer keeping the private key in account-level secret storage or an equally controlled source, and reference it from the workflow only when the token is being built.
* Use destination names that make the token lifecycle obvious, especially when the JWT is short-lived and immediately consumed by a later HTTP request.
* Use a clear destination name so later HTTP or API jobs can reference the signed token without ambiguity.

## Common JWT flow

A common pattern is:

1. Prepare numeric time claims (`iat`, `exp`) with `dataOperations`.
2. Build the claims object with `jsonPipeline`.
3. Sign claims in this job.
4. Use the signed token in `sendHttpRequest` authorization headers.

This keeps token generation deterministic and easy to audit.

## Security notes

* Do not write private keys or signed tokens to logs.
* Avoid passing signed tokens in query strings when header-based authentication is available.
* Keep JWT lifetime short and regenerate when needed instead of reusing stale tokens across unrelated flows.

## Related jobs

* Send HTTP Request
* Verify JWT
* Extend Token Expiration

## References

* [Working With Variables](https://help.bosbec.com/knowledge-base/working-with-variables/)
	* Useful when building JWT payloads or storing the resulting token in workflow context.