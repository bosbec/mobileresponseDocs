# Set Debug Mode

The Set Debug Mode job is used to pause workflow execution so you can inspect the current state and step through the workflow manually during troubleshooting. In practice, it behaves like a breakpoint placed directly in the workflow.

## Properties

The properties for configuring the job are described below.

* **Debug mode** (optional; default: false)
	* Set to `true` to pause execution at this point in the workflow. Set to `false` when you want the workflow to continue without stopping here.

## Execution behavior

This job affects the currently running workflow execution only.

* When **Debug mode** is enabled, execution pauses at this job so you can inspect the workflow state and continue step by step.
* When **Debug mode** is disabled, execution passes through the job without stopping.
* This job is useful when you want the breakpoint to exist as a visible job in the workflow itself.

## Best practices and tips

* Place the job immediately before the part of the workflow you want to inspect.
* Remove it or disable **Debug mode** after troubleshooting so normal workflow runs do not stop unexpectedly.
* There is now also an alternative breakpoint mechanism in the workflow builder: click the arrow between two jobs and select `Set breakpoint`.
* Use the arrow-based breakpoint when you want a lighter-weight breakpoint without adding a dedicated job to the workflow.

## Related jobs

* Place holder
* Execute Workflow

## References

* [Getting started: Integrations](https://help.bosbec.com/knowledge-base/getting-started-integrations/)
	* Background guidance for troubleshooting and validating workflow-based integrations.

