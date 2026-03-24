# Find Units By ID

The Find Units By ID job resolves one or more unit GUIDs into actual unit objects. Use it when you already know the unit IDs and want to load those units into the workflow context for later filtering, messaging, or saving.

## Properties

The properties for configuring the lookup are described below.

* **ID source** (required)
	* Source containing one unit ID or multiple unit IDs. The value can come from workflow context and commonly uses comma- or semicolon-separated GUIDs.
* **Resource name** (optional)
	* Name of the output unit resource. If left empty, the found units are added to the workflow context temporary group instead.

## Referencing syntax

Use workflow expressions when the IDs come from metadata or another resource.

* `{{metadata.unit_id}}` can be used for a single known unit ID.
* `{{metadata.unit_ids}}` can be used when a previous step stored several IDs in one value.
* Comma-separated and semicolon-separated GUID lists are preferred when providing multiple IDs.

## Behavior

The job reads the ID value from **ID source** and resolves the matching units.

* If **Resource name** is provided, the result is stored as a unit resource in workflow context.
* If **Resource name** is left empty, the result is added to the workflow context temporary group.
* This job is useful when later workflow steps need full unit objects rather than only their IDs.

## Best practices and tips

* Use a resource output when later jobs should work with the units as a named resource rather than through the temporary group.
* Prefer consistent separators such as `,` or `;` when providing multiple IDs.
* Keep ID lookup separate from broader search logic; if you need more flexible find behavior, compare this job with Find Or Create Units or Unit Pipeline.

## Related jobs

* Find Or Create Units
* Unit Pipeline
* Set Incoming Unit

## References

* [Working With Variables](https://help.bosbec.com/knowledge-base/working-with-variables/)
	* Useful when unit IDs are read from metadata or workflow resources.
