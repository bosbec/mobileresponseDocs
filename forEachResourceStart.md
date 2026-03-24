# For Each Resource Start

The For Each Resource Start job begins a loop over the items in a resource. For every iteration, it exposes the current item as a temporary resource so the jobs inside the loop can process one item at a time.

## Properties

The properties for configuring the loop are described below.

* **Resource to iterate** (required)
	* The resource whose items should be processed sequentially.
* **Current item name** (required)
	* Name of the temporary resource created for the current item during each iteration.
* **Nested for each name** (optional)
	* Advanced identifier used when you have nested loops and need to pair the correct start and stop jobs.

## Referencing syntax

Use the name from **Current item name** to access the current item inside the loop.

* Read the current item with expressions such as `{{currentItemName.key}}`.
* For a unit resource, you might reference `{{one_unit.metadata.firstname}}`.
* For a data log item resource, you might reference `{{log_item.value}}`.

## Execution behavior

This job defines two distinct paths.

* **For each**
	* Jobs on this path run once for every item in the resource.
* **When completed**
	* Jobs on this path run after all items have been processed.

When the loop reaches [forEachResourceStop.md](forEachResourceStop.md), execution returns here and the next item is loaded into the temporary resource.

## Best practices and tips

* Choose a clear **Current item name** so expressions inside the loop remain readable.
* Keep the loop body focused on work that belongs to one item at a time.
* Use **Nested for each name** only when you need nested loops, and make sure the start and stop jobs use the same value.

## Related jobs

* For Each Resource Stop
* Parse CSV to Resource
* Unit Pipeline

## References

* [For Each Resource](https://help.bosbec.com/knowledge-base/for-each-resource/)
	* Overview of how to configure the start and stop jobs together.
* [Working With Variables](https://help.bosbec.com/knowledge-base/working-with-variables/)
	* Reference for reading values from the current item resource inside the loop.