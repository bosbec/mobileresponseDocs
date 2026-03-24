# Send HTTP request

The Send HTTP request job is used to perform HTTP requests to external systems to either create a webhook or fetch data for later use within your workflow.

## Properties

The properties for configuring the request are described below.

* **Url** (required)
  * The URL to perform the HTTP request against.
* **Method** (required)
  * The HTTP method to use for the request (GET, POST, PUT, DELETE, etc.).
* **Headers** (optional)
  * Headers to include in the request. When Content-Type is provided, that value is used; otherwise the system determines the most appropriate value automatically.
* **Body** (optional)
  * The request body to send with the request.
* **Timeout** (optional)
  * The timeout duration for the request.
* **Response resource name** (required if capturing response)
  * The name of the resource where the response will be stored for use in subsequent jobs.
* **Response type** (optional; default: Auto — determined by Content-Type header)
  * Defines the expected response format. The response body will be parsed accordingly.
  * Options: Auto, Text (plain text/HTML), Json (JSON payload), Xml (XML payload)
* **Response validation** (optional; default: Valid response code)
  * Determines what constitutes a successful response.
  * Options: Valid response code (2XX only), Valid response code and response type (2XX + matching Content-Type), No validation (all responses succeed)

## Execution paths

This job supports three different execution paths based on response validation settings (configured in the Response validation property):

* **Jobs** 
  * Continue immediately after the request is sent without waiting for a response. Use for fire-and-forget webhooks.
* **Jobs to execute after successful response**
  * Continue here after receiving a successful response (determined by the Response validation setting).
* **Jobs to execute after unsuccessful response**
  * Continue here when a response returns but does not meet validation criteria.

## Response resource output

When a response is captured to a resource, the following properties are available for subsequent jobs:

* **Url**
  * The URL that was requested.
* **Status code**
  * The HTTP status code from the response.
* **Status message**
  * Descriptive text about the response status.
* **Headers**
  * All response headers received.
* **Raw body**
  * The response body in its original form.
* **Body**
  * The response body parsed according to the Response type setting (StringResource, JsonResource, or XmlResource).
* **Body type**
  * The resource type the body was parsed to.
* **Response time**
  * Duration in milliseconds until the response was received.
* **Request time**
  * Timestamp (UTC) when the request was sent.

## Best practices and tips
* Name your response resource something descriptive so that the workflow is easier to work with in the future. A more descriptive name makes the workflow more readable.
* Send the minimum data the receiving system needs. Smaller request bodies are easier to validate, reduce accidental data exposure, and make troubleshooting simpler.
* Use **Response validation** deliberately. Prefer **Valid response code and response type** when downstream jobs depend on structured JSON or XML, so invalid payloads fail early instead of propagating unexpected data.
* Route failed or unexpected responses to **Jobs to execute after unsuccessful response** when the workflow must branch on API failures, retries, or fallback handling rather than silently continuing.
* When calling authenticated APIs, resolve secrets and tokens from controlled workflow sources instead of scattering credentials across multiple jobs or hardcoded values.
* Building the request body can also be done in a JSON pipeline before running this job, saving the JSON to a JSON resource and referencing the resource using the {{resourceName}} syntax.
* Are you looking to send a response to an incoming request? Take a look at Send API Response instead.

## Related jobs
* Send API Response
* Parse JSON to resource
* Parse XML to resource
* JSON Pipeline

## References
* [Quickstart: Your first API](https://help.bosbec.com/knowledge-base/quickstart-your-first-api/)
  * Step-by-step guide to getting started with HTTP requests
* [Building your first API](https://help.bosbec.com/knowledge-base/building-your-first-api/)
  * Advanced patterns and best practices
* [Send HTTP request](https://help.bosbec.com/knowledge-base/send-http-request/)
  * Detailed job documentation