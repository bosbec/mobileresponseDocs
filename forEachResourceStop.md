# For Each Resource Stop

The For Each Resource Stop job marks the end of a loop started by For Each Resource Start. When execution reaches this job, the workflow returns to the matching start job, loads the next item from the resource, and repeats the loop until all items have been processed.

## Properties

The properties for configuring the loop stop are described below.

* **Nested for each name** (optional)
	* Advanced identifier used to match this stop job with the correct For Each Resource Start job when you have nested loops in the same workflow.

## Execution behavior

This job does not process data by itself. Instead, it controls how the loop continues.

* If there are more items left in the resource, execution returns to the matching start job and runs the loop body again.
* If there are no items left, the workflow leaves the loop and continues on the `When completed` path configured from the start job.
* When **Nested for each name** is used, the value must match the corresponding start job so the correct loop pair is used.

## Best practices and tips

* Always pair this job with [forEachResourceStart.md](forEachResourceStart.md); the loop will not work correctly without a matching start job.
* Use **Nested for each name** only when you actually need nested loops. Leave it empty for simpler workflows.
* Keep the jobs inside the loop focused on the current item so the loop is easy to reason about and debug.

## Related jobs

* For Each Resource Start
* Parse CSV to Resource
* Unit Pipeline

## References

* [For Each Resource](https://help.bosbec.com/knowledge-base/for-each-resource/)
	* Explains how the start and stop jobs work together and how to reference the current item during iteration.
