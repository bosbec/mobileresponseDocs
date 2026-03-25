# Parse JSON to Resource

The Parse JSON to Resource job parses JSON text from a workflow value and creates a JsonResource in the workflow context. Use it when incoming payloads, metadata values, or other resources contain JSON that should be accessed as structured data later in the workflow.

## Properties

The properties for configuring the parser are described below.

* **JSON source** (required)
	* Source containing the JSON text to parse. This can be a raw JSON string or a workflow expression such as `{{incomingmessage.body}}` or `{{metadata.my_json}}`.
* **Destination resource name** (required)
	* Name of the JsonResource created in the workflow context.
* **Deny lookup destination resource name** (optional)
	* If enabled, the destination resource name is used exactly as entered instead of being resolved as a lookup.

## Referencing syntax

After parsing, access values using dot notation on the destination resource.

* For `{"sample":"value"}` stored as `my_json`, use `{{my_json.sample}}`.
* Nested values can be accessed with deeper paths such as `{{my_json.customer.id}}`.
* For arrays, use index syntax such as `{{my_json.items[0].name}}`.

## Resulting resource

If parsing succeeds, the job creates a JsonResource in the workflow context.

* The destination resource can be used directly in later jobs.
* Downstream jobs can read specific properties without reparsing the JSON.
* Invalid JSON input causes the parse to fail, so it is usually best to validate or isolate the source first when the payload may be inconsistent.

## Best practices and tips

* Give the destination resource a descriptive name so downstream expressions stay readable.
* When the source can contain malformed or mixed content, validate or isolate the JSON-producing part before parsing so downstream steps do not depend on ambiguous input.
* Parse once and reuse the resulting JsonResource instead of repeatedly handling the same payload as plain text.
* When the JSON contains arrays, keep extraction expressions simple and move advanced array filtering into dedicated steps only when needed.

## Error handling pattern

When JSON input may be invalid, design an explicit failure path.

Suggested pattern:

1. Extract or isolate the expected JSON input source before parsing.
2. Run this job to parse into a dedicated destination resource.
3. Route downstream processing based on whether required parsed keys are available.
4. Return a clear API response (for example `400`) or fallback handling when parsing fails.

This keeps malformed input from propagating into account updates or external API requests.

## Related composition pattern

Common API flow:

* `incomingHttpTrigger` -> `parseJsonToResource` -> validation route (`routeFromMetaData`) -> processing jobs -> `sendApiResponse`

Using this sequence keeps request parsing, validation, and response behavior explicit.

## Related jobs

* Parse CSV to Resource
* Parse XML to Resource
* JSON Pipeline

## References

* [Working With Variables](https://help.bosbec.com/knowledge-base/working-with-variables/)
	* Reference for workflow expressions and resource access syntax.
* [Accessing Values Inside JSON Arrays](https://help.bosbec.com/knowledge-base/accessing-values-inside-json-arrays/)
	* Examples of reading nested JSON arrays and filtering array items.
