# Send API Response

The Send API Response job sends an HTTP response back to the caller of an Incoming HTTP Trigger. Use this job to control the response body, content type, status code, and headers returned to the HTTP client.

## Properties

The properties for configuring the response are described below.

* **Response body** (optional; default: Ok)
	* Template for the HTTP response body. Supports statement syntax for dynamic values.
* **Response content type** (optional)
	* The content type of the response (for example: application/json, text/plain).
* **Response status code** (optional)
	* The HTTP status code to return (for example: 200, 400, 404).
* **Response headers** (optional)
	* Custom HTTP response headers as key-value pairs. If not set, default headers are used.

## Best practices and tips

* Use this job together with Incoming HTTP Trigger to ensure callers receive an explicit response.
* Return a clear status code and body that matches your API contract so integrations are easier to debug.
* Set Response content type explicitly when returning JSON or plain text to avoid ambiguity for the caller.
* Include only the headers you need in Response headers to keep responses predictable.
* Keep the response body focused on the fields the caller actually needs. Smaller, explicit responses are easier to consume and reduce accidental data leakage.
* Use error status codes and response bodies consistently across failure paths so external systems can react predictably when validation or downstream processing fails.

## Related jobs and triggers

* Incoming HTTP Trigger
* Send HTTP request
* JSON Pipeline

## References

* [Quickstart: Your first API](https://help.bosbec.com/knowledge-base/quickstart-your-first-api/)
	* Step-by-step guide to getting started with API workflows.
* [Building your first API](https://help.bosbec.com/knowledge-base/building-your-first-api/)
	* Advanced patterns and best practices for API workflows.

