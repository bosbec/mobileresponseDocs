# Save To Group

The Save To Group job saves members from the workflow context into a group. It can target an existing group or create a new group, including a dynamic group based on tags.

## Properties

The properties for configuring the job are described below.

* **Group** (optional)
	* Existing group to save members into.
* **Use workflow context groups** (optional; default: false)
	* Use members from all workflow-context groups.
* **Create new group and ignore group ID** (optional; default: false)
	* Create a new group instead of using the connected group.
* **New group name source** (optional)
	* Name for the new group when a group is being created.
* **New dynamic group tags source** (optional)
	* Comma-separated tag list used when creating a dynamic group.
* **Use workflow context temporary group** (optional; default: false)
	* Use members from the workflow-context temporary group.
* **Use incoming unit** (optional; default: false)
	* Use the incoming unit as a group member source.
* **Resource name** (optional)
	* Destination resource where the resulting group ID is stored.

## Referencing syntax

When creating new groups dynamically, the name and tag values can come from workflow data.

* Use workflow expressions such as `{{metadata.group_name}}` in **New group name source**.
* Use a comma-separated source such as `tag-a,tag-b` for **New dynamic group tags source**.

## Behavior

This job supports two main modes.

* **Save to an existing group**
	* Connect a group and choose which members from workflow context should be added.
* **Create a new group**
	* Enable **Create new group and ignore group ID** and provide a group name.

If dynamic-group tags are provided while creating a new group, the created group behaves as a dynamic group rather than a purely static one.

## Best practices and tips

* Use only the member sources you actually need so the result is predictable.
* When creating a dynamic group, keep the tag source stable and easy to audit.
* Save the resulting group ID to a resource when later jobs need to reference the created group explicitly.

## Related jobs

* Group Operations
* Unit Operations
* Find Groups

## References

* [Importing units](https://help.bosbec.com/knowledge-base/importing-units/)
	* Useful background when group members come from newly created or loaded unit data.

