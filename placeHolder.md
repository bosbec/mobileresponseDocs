# Place holder

The Place holder job performs no action on its own. Use it as a visible routing point, a temporary stub while building a workflow, or a clear end point for paths such as error handling where you want the workflow design to stay explicit.

## Properties

This job has no configurable properties.

## Execution behavior

The job does not read or write workflow data.

* It simply passes execution to the next connected jobs.
* It can be used to reserve a place for future logic without changing the current workflow path.
* It is often useful on branches that should exist explicitly, even when no processing is needed yet.

## Best practices and tips

* Use a Place holder job when you want to make workflow branches readable without introducing temporary logic.
* Keep the job name or description meaningful so it is obvious why the branch exists.
* Use this job on success or failure paths when you want the destination of a route to stay visible during design and review.

## Related jobs

* Set Debug Mode
* Send HTTP Request
* Route From Meta Data

## References

* [Working With Variables](https://help.bosbec.com/knowledge-base/working-with-variables/)
	* Useful background when a placeholder marks a branch that will later read or write workflow context values.