# Reset Synchronized Counter

The Reset Synchronized Counter job resets an existing synchronized counter to a specific value. Use it together with [synchronizedCounter.md](synchronizedCounter.md) when a quota, rate limit, or event counter should be cleared or reinitialized between periods, workflows, or business events.

## Properties

The properties for configuring the reset are described below.

* **Counter name** (required)
	* Logical name of the counter to reset.
* **Counter key** (required)
	* Unique key within the counter name that identifies which counter instance should be reset.
* **Use counter for administrator** (optional)
	* Use another administrator context when resolving which counter to reset.
* **Reset value** (required)
	* Value the counter should be set to after the reset.
* **Counter limit** (optional)
	* New counter limit to apply at the same time as the reset.

## Referencing syntax

Counter identifiers and reset values can be configured with dynamic workflow expressions.

* Use expressions such as `{{metadata.sender}}` to target a specific counter key.
* Use workflow values in **Reset value** when the counter should be reset to something other than a fixed number.
* Use **Use counter for administrator** when the counter belongs to another administrator context on the same account.

## Reset behavior

This job updates an existing synchronized counter rather than incrementing it.

* **Counter name** and **Counter key** identify which counter should be reset.
* **Reset value** defines the new current value of that counter.
* **Counter limit** can also be changed during the reset if the limit should be updated for future executions.

This makes the job useful for resetting counters at the start of a new period, after a successful workflow branch, or when a manual override is needed.

## Best practices and tips

* Use the same **Counter name** and **Counter key** conventions here as in [synchronizedCounter.md](synchronizedCounter.md) so the intended counter is reset reliably.
* Reset counters deliberately at clear lifecycle boundaries such as daily quotas, campaign restarts, or successful completion of a guarded process.
* Update **Counter limit** only when the reset should also change the future threshold, not just the current value.

## Related jobs

* [synchronizedCounter.md](synchronizedCounter.md)
* [findCounters.md](findCounters.md)
* [routeFromMetaData.md](routeFromMetaData.md)

## References

* [Working With Variables](https://help.bosbec.com/knowledge-base/working-with-variables/)
	* Reference for building dynamic counter names, keys, and reset values from workflow data.

