# JSON Pipeline

The JSON Pipeline job runs an ordered set of JSON transformation steps on a workflow resource. Use it to load a JSON resource, modify it step by step, and save it back for later jobs.

## Properties

* **Steps** (required)
  * Ordered list of JSON pipeline steps to execute (e.g. Load resource -> Transform -> Save as resource).
* **Use syntax alt 1** (optional; default: true)
  * Controls whether syntax alternative 1 is enabled for step templates (for example `{{this.key}}` and `{{metadata.key}}`).
* **Execution condition** (optional)
  * Script that controls whether the job runs (e.g. `{{metadata.should_run}} == true`).
* **Jobs** (optional)
  * Jobs to execute after this job completes.

## Referencing syntax

The active pipeline resource can be referenced in step values using:

* `{{this.key}}`
  * Reads values from the current JSON object being processed.

Workflow context values can be referenced using:

* `{{metadata.key}}`
  * Reads values from workflow metadata.

## Step conditions

Each step can have a condition to control whether it runs. Conditions are evaluated between steps.

* [Conditions](resourcePipelineStepConditions.md)
  * How to configure pipeline step conditions.

## Steps

### Add JSON array

Adds a JSON array at a key or path in the current JSON resource.

* **Key** (optional)
  * Key or path where the array should be added (e.g. `contacts`, `customer.addresses`).
* **Add with value** (optional)
  * Defines what value should be used when creating the array item.
  * Options:
  * **Empty value**
  * **From source value**
    * **Source value** (optional) - value expression to use (e.g. `{{metadata.phone}}`).
  * **From JSON resource**
    * **Resource name** (optional) - resource to load value from (e.g. `incoming_customer_json`).

### Add key

Adds a key to the JSON resource with the specified value.

* **Key** (optional)
  * The key to add (e.g. `status`, `customer.phone`).
* **Value** (optional)
  * The value to set for the key (e.g. `Active` or `{{metadata.customer_phone}}`).

### Create from resource

Creates JSON from another resource using a template and adds the result to the pipeline context.

* **Source resource** (optional)
  * Resource to read input items from (e.g. `orders_json`).
* **JSON item template** (optional)
  * Template used to create JSON output items (e.g. `{ "id": "{{this.id}}", "name": "{{this.name}}" }`).

### Filter by expression

Filters items in a JSON array using a left-side/operator/right-side expression.

* **Left side** (optional)
  * Left part of the comparison expression (e.g. `{{this.type}}`).
* **Operator** (optional)
  * Comparison operator (e.g. `==`, `!=`, `contains`).
* **Right side** (optional)
  * Right part of the comparison expression (e.g. `mobile` or `{{metadata.target_type}}`).
* **Filter actions** (optional)
  * Options: **Remove**, **Keep**

### Load resource

Loads a JSON resource from workflow context into pipeline context.

* **Resource name** (optional)
  * Name of the resource to load (e.g. `incoming_http_response`).

### Parse JSON

Parses JSON input and replaces the current pipeline resource if parsing succeeds.

* **JSON source** (optional)
  * JSON input text to parse (e.g. `{{metadata.raw_json}}` or `{ "id": 1 }`).

### Push array item

Pushes an item into an array in the current JSON resource.

* **Source item** (optional)
  * Value or expression for the item to push (e.g. `{ "phone": "{{metadata.phone}}" }`).
* **Destination path** (optional)
  * Path to the target array in the JSON resource (e.g. `contacts`, `customer.phones`).

### Remove key

Removes a key from the JSON resource.

* **Key** (optional)
  * The key to remove (e.g. `debugInfo`, `customer.tempField`).

### Rename resource

Renames a JSON resource in workflow context.

* **Resource name** (optional)
  * Existing resource name (e.g. `response_json`).
* **New name** (optional)
  * New resource name (e.g. `customer_profile_json`).

### Save as resource

Saves the current pipeline resource back to workflow context.

* **Resource name** (optional)
  * Resource name to save to (e.g. `updated_order_json`). Existing resource with the same name is overwritten.

### Set JSON array item

Sets or inserts an item at a position in a JSON array.

* **Key** (optional)
  * Key or path to the target array (e.g. `items`, `order.lines`).
* **At position** (optional)
  * Target index in the array (e.g. `0`, `1`, or `{{metadata.array_index}}`).
* **Insert** (optional)
  * If true, inserts at position; if false, overwrites existing item at position.
* **Add with value** (optional)
  * Defines what value should be written.
  * Options:
  * **Empty value**
  * **From source value**
    * **Source value** (optional) - value expression to use (e.g. `{{metadata.new_item}}`).
  * **From JSON resource**
    * **Resource name** (optional) - resource to load value from (e.g. `item_template_json`).

### Set value

Sets a value for an existing key in the JSON resource.

* **Key** (optional)
  * The key to set (e.g. `customer.email`, `order.status`).
* **Value** (optional)
  * The value to assign (e.g. `Delivered` or `{{metadata.email}}`).

### Transform

Transforms the JSON resource according to a transformation template.

* **Transformation** (optional)
  * JSON transformation template (e.g. `{ "id": "{{this.id}}", "name": "{{metadata.customer_name}}" }`).

Example patterns:

```json
{
  "first": "{{this.key1}}",
  "second": "{{this.key2}}"
}
```

```json
{
  "first": "{{this.key1}}",
  "second": "{{metadata.key}}"
}
```

## Execution paths

* **Jobs**
  * Jobs to execute after all steps are complete.

## Best practices and tips

* Start with **Load resource** or **Transform** and end with **Save as resource** for predictable pipelines.
* Keep transformations small and explicit; multiple simple steps are usually easier to maintain than one large transformation.
* Use `{{this.key}}` for current JSON values and `{{metadata.key}}` for workflow values.
* Use **Parse JSON** when you receive raw JSON text from metadata or external responses.

## Related jobs

* Data Operations
* Send HTTP request
* Parse JSON to resource

## References

* [Working with Variables](https://help.bosbec.com/knowledge-base/working-with-variables/)
  * Expression and lookup syntax used in pipeline templates.
* [Accessing Values Inside JSON Arrays](https://help.bosbec.com/knowledge-base/accessing-values-inside-json-arrays/)
  * How to read array values using index syntax (for example `{{my_json_resource.outer[0].name}}`) and filtered expressions (for example `{{customer.phonenumbers[?(@.type == 'mobile')].number}}`), including limitations when multiple items match.