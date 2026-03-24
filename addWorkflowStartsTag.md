# Add Workflow Starts Tag

The Add Workflow Starts Tag job sets a searchable tag on the current workflow-start instance. Use it to attach dynamic values to a workflow execution so that the workflow start can be found or filtered later using meaningful runtime tags.

## Properties

The properties for configuring the job are described below.

* **Tag source** (required)
  * Source expression or statement that resolves to the tag value to add at runtime.

## Referencing syntax

Use standard statement syntax when building the tag value.

* Read metadata with `{{metadata.key}}`.
* Read resource values with expressions such as `{{resourceName.key}}`.
* Build descriptive tags from dynamic values, for example `order:{{metadata.order_id}}`.

## Execution behavior

This job updates the current workflow-start record rather than a unit, group, or ordinary workflow context metadata key.

* The resolved tag value is added to the current workflow-start instance.
* The tag can then be used to search for or filter workflow-start records later.
* The workflow continues immediately after the tag is added.

## Best practices and tips

* Keep tags short, descriptive, and consistent so they remain useful for searching.
* Prefer stable business identifiers such as order IDs, customer IDs, or correlation IDs over free-form text.
* Use prefixes such as `order:` or `integration:` when you want tags from different use cases to stay easy to distinguish.

## Related jobs

* Execute Workflow
* Notify UI
* Workflow

## References

* [Working With Variables](https://help.bosbec.com/knowledge-base/working-with-variables/)
  * Reference for building dynamic tag values from metadata and resource expressions.