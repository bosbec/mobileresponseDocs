# Find Or Create Units

The Find Or Create Units job searches for units based on a workflow value and creates new units only if no matching units are found and creation is allowed. Use it when an incoming sender, email address, phone number, or similar identifier should resolve to a unit automatically.

For many newer workflows, [unitPipeline.md](unitPipeline.md) can often be used instead of this job. Unit Pipeline gives you a more flexible step-based approach for finding, creating, filtering, updating, and saving units in one place.

## Properties

The properties for configuring the job are described below.

* **Search source** (required)
	* Source expression or string used when searching for units, for example `incomingmessage.sender`.
* **Single found unit as incoming unit** (optional; default: false)
	* If enabled, a single matching unit is set as `IncomingUnit`.
* **Prevent creating units** (optional; default: false)
	* If enabled, the job only searches and never creates new units.
* **Find distinct for phone number** (optional; default: false)
	* Return at most one unit per phone number.
* **Find distinct for email address** (optional; default: false)
	* Return at most one unit per email address.
* **Page index** (optional; default: 1)
	* Result page to return when many units match.
* **Page size** (optional; default: 50)
	* Number of units to return per page.

## Referencing syntax

Use workflow expressions in **Search source** when the search input comes from the current workflow context.

* `{{incomingmessage.sender}}` is a common source for incoming-message workflows.
* `{{metadata.customer_email}}` can be used when an earlier step stored the value in metadata.

## Behavior

The job behaves in three stages.

* Search for units using **Search source**.
* If no units are found and **Prevent creating units** is disabled, create a new unit using the searched value.
* If exactly one unit is found and **Single found unit as incoming unit** is enabled, set that unit as `IncomingUnit`.

The distinct options are useful when duplicate phone numbers or email addresses exist and the workflow should continue with only one result per channel value.

## Best practices and tips

* Enable creation only when the workflow is allowed to provision new units automatically.
* Use the distinct options when duplicate channel data exists and downstream jobs expect a smaller result set.
* Set `IncomingUnit` only when a single-unit outcome is the intended behavior for later jobs.
* If the workflow needs more than a simple find-or-create pattern, consider using [unitPipeline.md](unitPipeline.md) instead. It is often the better fit for newer workflows that combine search, creation, filtering, updates, and saving in one sequence.

## Related jobs

* Unit Pipeline
* Unit Operations
* Set Incoming Unit
* Get Users From Incoming Message

## References

* [Importing units](https://help.bosbec.com/knowledge-base/importing-units/)
	* Helpful background for how unit data is commonly created and updated.
