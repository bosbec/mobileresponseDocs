# Route From Meta Data

The Route From Meta Data job branches workflow execution based on metadata values in the workflow context. Use it when different sets of jobs should run depending on comparisons such as status values, text matches, numbers, dates, or time windows.

## Properties

The properties for configuring the job are described below.

* **Meta data routes** (required)
	* List of route definitions. Each route contains a metadata source, a compare operator, and either a static compare value or a compare value source.
* **Route destination on no match** (optional)
	* Fallback path used when none of the configured routes match.
* **Split workflow context on multiple matches** (optional; default: false)
	* If enabled, the workflow context is split when several routes match so each route continues in its own context.

## Referencing syntax

Route definitions usually compare workflow metadata or other dynamic values.

* Read metadata with `{{metadata.key}}`.
* Use **Compare value source** when the value to compare against should also come from metadata or another resource, for example `{{metadata.last_ok}}`.
* Use date expressions such as `{{datetime(yyyy-MM-dd)}}` when working with time-based routes.

## Route behavior

Each route evaluates one condition.

* **Meta data source**
	* The value to evaluate, for example `{{metadata.status}}`.
* **Compare operator**
	* Determines how the comparison is performed, for example `=`, `>`, `contains`, `before`, or `regex`.
* **Compare value**
	* Static comparison value such as `OK`.
* **Compare value source**
	* Dynamic comparison value read from workflow context.

For example, if `{{metadata.last_test}}` should be later than `{{metadata.last_ok}}`, set the metadata source to `{{metadata.last_test}}`, the compare value source to `{{metadata.last_ok}}`, and the operator to `>`.

## Multiple matches

Several routes can match during the same execution.

* Without **Split workflow context on multiple matches**, matching routes continue one after another in the same workflow context.
* With **Split workflow context on multiple matches** enabled, each matching route gets its own workflow-context copy, which reduces interference between branches.
* Jobs connected to route outputs are the paths that execute. The ordinary `Jobs` connector is not used for route matches.

## Best practices and tips

* Use **Route destination on no match** to make the fallback behavior explicit.
* Avoid designing routes so that multiple branches match at the same time when possible.
* When the logic can be expressed as a sequence of decisions, prefer chaining multiple [routeFromMetaData.md](routeFromMetaData.md) jobs instead of relying on several matches in a single job. This reduces the risk of race conditions or conflicting workflow-context changes further downstream.
* Enable **Split workflow context on multiple matches** when several routes may match and the branches should not modify the same workflow context.
* Prefer **Compare value source** over copying values into static fields when both sides of the comparison are dynamic.
* Route on stable, well-named metadata keys so branching remains understandable and does not depend on temporary or ambiguous values.

## Related jobs

* Execute Workflow
* Filter Workflow Context
* Comparing MetaData

## References

* [Route From Meta Data](https://help.bosbec.com/knowledge-base/route-from-meta-data/)
	* Detailed examples of metadata routes, time-based routes, and multiple-match behavior.
* [Comparison Operators](https://help.bosbec.com/knowledge-base/comparison-operators/)
	* Complete list of supported operators and how they behave.
* [Working With Variables](https://help.bosbec.com/knowledge-base/working-with-variables/)
	* Reference for metadata expressions and date/time functions.
