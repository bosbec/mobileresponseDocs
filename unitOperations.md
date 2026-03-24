# Unit Operations

The Unit Operations job lets you find units from one or more sources, optionally filter the result, optionally update the found units, and finally decide how those units should be stored or deleted.

## Properties

The job is organized into stages rather than a single flat property list.

* **Find operations** (required)
	* Ordered list of find steps that add units to the working set.
* **Filter operations** (optional)
	* Ordered list of filters applied to the found units.
* **Operate on units** (optional)
	* Ordered list of operations to perform on the units, such as updating metadata.
* **Store operation** (required)
	* Final step that decides how the processed units are stored, persisted, or deleted.

## Referencing syntax

Expressions in filters and updates usually compare unit data with workflow data.

* Read unit metadata with expressions such as `{{unit.metadata.customer_id}}`.
* Read workflow context metadata with expressions such as `{{metadata.customer_id}}`.
* When updating unit metadata, use unit destinations on the left side and workflow values or static values on the right side.

## Find operations

Find steps append units to the working set instead of replacing earlier results.

Common find patterns include:

* **Find from account**
	* Search the account by phrase, including metadata-aware search such as `md:firstname=John`.
* **Find by phone** or **Find by email**
	* Search with a direct channel value.
* **Find in group**
	* Load units from a specific group.
* **Find in resource**
	* Load units from one or more workflow resources.
* **Find in workflow context**
	* Reuse units already present in the temporary group or workflow groups.
* **Create from data**
	* Create units directly from workflow values.

Each step has an order and can be configured to continue on error if partial success is acceptable.

## Filter operations

Filters narrow down the current working set.

* **Channel filter**
	* Keep or remove units based on available channels.
* **Metadata filter**
	* Compare unit values against static values or workflow values.

Use filters after broad find steps when you want a more readable pipeline than building one very complex search expression.

## Operate on units

The most common operation is metadata updates.

* **Update metadata**
	* Apply key-value updates to all units currently in the working set.

This is useful when a workflow should enrich units before saving them to the account, groups, or resources.

## Store operation

The final step decides what happens to the resulting units.

Typical outcomes include saving to the account, saving to a workflow resource, saving to workflow groups or the temporary group, or deleting units from the account.

## Best practices and tips

* Use several small find and filter steps instead of one overloaded search when readability matters.
* Turn on continue-on-error only when the workflow can safely proceed with partial results.
* When deduplication or merging is the real goal, compare this job with [unitPipeline.md](unitPipeline.md) before choosing an approach.

## Related jobs

* [unitPipeline.md](unitPipeline.md)
* [findOrCreateUnits.md](findOrCreateUnits.md)
* [saveToGroup.md](saveToGroup.md)

## References

* [Unit Pipeline – Merging Units](https://help.bosbec.com/knowledge-base/unit-pipeline-merging-units/)
	* Related guidance when the unit workflow involves deduplication or merging.
* [Importing units](https://help.bosbec.com/knowledge-base/importing-units/)
	* Background on common unit data patterns and bulk import behavior.
* [Comparison Operators](https://help.bosbec.com/knowledge-base/comparison-operators/)
	* Reference for the operators used in metadata-based unit filters.
