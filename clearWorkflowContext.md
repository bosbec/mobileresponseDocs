# Clear Workflow Context

The Clear Workflow Context job removes selected data from the current workflow context. Use it to reset temporary state between workflow steps, clean up after a branch, or make sure downstream jobs do not accidentally reuse earlier metadata or resources.

## Properties

The properties for configuring the cleanup are described below.

* **Clear temporary group** (optional; default: false)
	* Removes all members from the workflow context temporary group.
* **Clear groups** (optional; default: false)
	* Removes workflow groups from the workflow context.
* **Clear incoming unit** (optional; default: false)
	* Removes the `IncomingUnit` resource from the workflow context.
* **Clear files** (optional; default: false)
	* Removes files stored in the workflow context.
* **Clear incoming group member** (optional; default: false)
	* Removes the `IncomingGroupMember` resource from the workflow context.
* **Clear meta data** (optional)
	* Regular expression used to match metadata keys that should be removed.
* **Clear resources** (optional)
	* Regular expression used to match resource names that should be removed.

## Referencing syntax

The two pattern-based properties use regular expressions.

* Leave **Clear meta data** empty to keep all metadata.
* Use `.*` in **Clear meta data** to remove all metadata keys.
* Leave **Clear resources** empty to keep all resources.
* Use targeted patterns such as `^tmp_` when you want to clear only temporary keys or resources with a naming convention.
* Use the format `^name$` when you want to match one exact metadata key or one exact resource name only. For example, `^customer_id$` matches only that metadata key, and `^request$` matches only a resource named `request`.

## Cleanup behavior

Each option affects a different part of the workflow context.

* Clearing groups removes fallback groups that some downstream jobs rely on.
* Clearing the incoming unit or incoming group member can cause later jobs to fail if they require those resources.
* Regex-based clearing is applied by name, so the pattern should be reviewed carefully before using broad matches.

## Best practices and tips

* Clear only the parts of the workflow context you no longer need.
* Prefer targeted regex patterns over `.*` unless a full reset is intentional.
* Adopt temporary naming conventions such as `tmp_` or another clear prefix so cleanup patterns stay precise and safe.
* Clean up after a branch or subprocess has finished, not before. Downstream jobs often depend on incoming units, groups, or response resources remaining available until the end of that path.
* When a workflow later depends on `IncomingUnit`, groups, or files, clear those values only after the dependent jobs have finished.

## Common cleanup patterns

### Remove only temporary resources

If temporary resources follow a naming convention, clear them by prefix:

* **Clear resources**: `^tmp_`

### Clear specific resources after an iteration

To remove only known intermediate resources, match exact names:

* **Clear resources**: `^call_log_response$|^call_log_json$`

### Targeted metadata cleanup

To remove one metadata key only:

* **Clear meta data**: `^retry_count$`

Targeted cleanup keeps required context intact while preventing stale temporary values from leaking into later branches.

## Related jobs

* Filter Workflow Context
* Split Workflow Context
* Workflow Context

## References

* [Working With Variables](https://help.bosbec.com/knowledge-base/working-with-variables/)
	* Background on metadata and resource naming within the workflow context.
* [Working With Strings](https://help.bosbec.com/knowledge-base/working-with-strings/)
	* Useful when writing regex patterns for metadata or resource cleanup.

