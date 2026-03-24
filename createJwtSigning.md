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
* Store private keys securely and inject them from controlled workflow sources rather than hardcoding them broadly in multiple jobs.
* Use a clear destination name so later HTTP or API jobs can reference the signed token without ambiguity.

## Related jobs

* Send HTTP Request
* Verify JWT
* Extend Token Expiration

## References

* [Working With Variables](https://help.bosbec.com/knowledge-base/working-with-variables/)
	* Useful when building JWT payloads or storing the resulting token in workflow context.