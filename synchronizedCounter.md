# Synchronized Counter

The Synchronized Counter job increments a shared counter safely even when many workflows run in parallel. Use it to enforce quotas, count events, or rate-limit actions where concurrent workflow executions must not overwrite each other.

## Properties

The properties for configuring the counter are described below.

* **Counter name** (required)
	* Logical name of the counter.
* **Counter key** (required)
	* Unique key within the counter name, often built from a dynamic business value such as an email address or customer ID.
* **Counter limit** (optional)
	* Maximum allowed value. Leave empty if the counter should not have a limit.
* **Counter limit must be set** (optional; default: false)
	* Requires a limit to exist when the job runs.
* **Requested increment** (optional; default: 1)
	* Preferred amount to add during this execution.
* **Min increment chunk size** (optional; default: 1)
	* Smallest partial increment allowed when the requested increment would cross the limit.
* **Output value** (required)
	* Destination where the current counter value is written after execution.
* **Output result** (required)
	* Destination where the result text is written after execution.
* **Use counter for administrator** (optional)
	* Use another administrator context when resolving the counter.

## Referencing syntax

Counter values and outputs can be configured with dynamic workflow expressions.

* Use expressions such as `{{metadata.sender}}` to build a per-sender **Counter key**.
* Write the result destinations to metadata or another writable destination so later jobs can route on them.
* Use dynamic sources for **Requested increment** when the increment depends on runtime data.

## Result values

The job stores both the counter value and a result value.

* **OK**
	* The increment succeeded and the limit was not exceeded.
* **Limit reached**
	* The counter reached the configured limit.
* **Fail**
	* No increment was made, usually because the counter was already at or above the limit.

The workflow continues after the job even when the result is `Limit reached` or `Fail`, so the result should be used in later routing or execution rules.

## Increment behavior

The job counts upward only.

* **Requested increment** controls how much the counter should increase.
* **Min increment chunk size** allows a smaller final increment when the full requested increment would exceed the limit.
* Example: with a limit of `3`, a requested increment of `2`, and a minimum chunk size of `1`, the counter can move from `2` to `3` on the final execution.

## Best practices and tips

* Keep **Counter name** stable and use **Counter key** for the runtime-specific uniqueness.
* Always store **Output value** and **Output result** so later jobs can decide what to do.
* Use this job when the workflow must protect a shared quota or rate limit across parallel executions, not just as a general-purpose counter.
* Branch explicitly on **Output result** when limits are reached so the workflow can postpone, skip, or notify instead of continuing as if capacity is still available.
* Keep the key tied to the business boundary you actually want to protect, such as a sender, customer, campaign, or API quota bucket.
* Pair this job with [resetSynchronizedCounter.md](resetSynchronizedCounter.md) when the counter should be reset between periods or workflows.

## Related jobs

* Reset Synchronized Counter
* Find Counters
* Route From Meta Data

## References

* [Working With Variables](https://help.bosbec.com/knowledge-base/working-with-variables/)
	* Reference for building dynamic counter keys, increments, and output destinations from workflow data.
