# Execute Workflow

The Execute Workflow job starts another workflow by searching for it by name or ID. Use it when you want to split logic into reusable workflows, trigger a public workflow from another account, or launch a subprocess with selected metadata and triggers.

## Properties

The properties for configuring the job are described below.

* **Workflow search phrase** (required)
	* Workflow name or workflow ID to search for and execute.
* **Trigger names** (optional)
	* Comma-separated list of trigger names to activate in the target workflow.
* **Initiation tags** (optional)
	* Tags that identify or categorize the workflow start in the target workflow.
* **Execute with metadata** (optional)
	* Key-value metadata passed to the target workflow at start.
* **Search public** (optional; default: false)
	* If enabled, the search includes public workflows outside the current account.
* **Ignore current workflow metadata** (optional; default: false)
	* If enabled, the current workflow context metadata is not forwarded automatically.
* **Allow recursive executions** (optional; default: false)
	* If enabled, the workflow is allowed to execute itself.
* **Exclude resources regex** (optional)
	* Regular expression used to prevent matching resources from being forwarded to the target workflow.

## Referencing syntax

Use standard workflow expressions when building metadata or search values for the target workflow.

* Read workflow context metadata with `{{metadata.key}}`.
* Pass metadata keys in **Execute with metadata** using destination keys and dynamic values, for example `customer_id` = `{{metadata.customer_id}}`.
* Use **Exclude resources regex** to omit resources whose names match a pattern when forwarding workflow context resources.

## Execution behavior

The job searches for the target workflow, starts it, and then continues based on the workflow design.

* Use **Workflow search phrase** to target a specific workflow by name or ID.
* Use **Trigger names** when the target workflow exposes more than one trigger and you want explicit control over which entry points are activated.
* By default, the current workflow context metadata is forwarded. Enable **Ignore current workflow metadata** when the called workflow should receive only the metadata you define explicitly.
* Enable **Allow recursive executions** only when self-execution is intentional and bounded.

## Best practices and tips

* Prefer workflow IDs when the target workflow name may change over time.
* Pass only the metadata the called workflow actually needs so the interface between workflows stays clear.
* Use **Ignore current workflow metadata** together with **Execute with metadata** when you want the called workflow to behave like a clean subprocess.
* Be careful with **Allow recursive executions**. Add a clear stop condition elsewhere in the workflow design to avoid runaway loops.

## Related jobs

* [routeFromMetaData.md](routeFromMetaData.md)
* [executeOrPostpone.md](executeOrPostpone.md)
* [workflow.md](workflow.md)
* [addWorkflowStartsTag.md](addWorkflowStartsTag.md)

## References

* [Getting started: Integrations](https://help.bosbec.com/knowledge-base/getting-started-integrations/)
	* Conceptual guidance for structuring workflows that coordinate data movement between systems.
