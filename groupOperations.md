# Group Operations

The Group Operations job is the main pipeline job for working with groups. It lets you find groups, optionally filter them, perform group-level operations, and then decide how the resulting groups should be stored or deleted.

## Properties

The job is organized into four pipeline stages.

* **Find steps** (required)
	* Ordered list of steps that load or create groups.
* **Filter steps** (optional)
	* Ordered list of metadata-based filters applied to the found groups.
* **Operate on group steps** (optional)
	* Ordered list of operations such as adding members, removing members, or updating group metadata.
* **Store step** (required)
	* Final step that decides whether the groups are saved to the account, saved to workflow context, saved to a resource, deleted, or left unsaved.

## Referencing syntax

Group filters and updates typically use metadata comparisons.

* Use group metadata keys when comparing group properties.
* Use workflow metadata expressions when the comparison value should come from the current workflow context.
* When updating group data, define the metadata keys to write and the values that should be stored.

## Find, filter, operate, store

The pipeline follows a consistent sequence.

* **Find**
	* Load groups from the account, from a resource, from workflow context, or create a new group.
* **Filter**
	* Keep or remove groups based on metadata comparisons.
* **Operate**
	* Add members, remove members, or update group data.
* **Store**
	* Save the result to the account, to workflow groups, to a named resource, delete from the account, or do not save.

## Best practices and tips

* Use filters before member operations when only a subset of groups should be changed.
* Save to a resource when later jobs need the resulting groups without immediately persisting changes to the account.
* Keep group-metadata updates focused on a small number of keys so the pipeline remains easy to review.

## Related jobs

* Save To Group
* Groups
* Unit Operations

## References

* [Working With Variables](https://help.bosbec.com/knowledge-base/working-with-variables/)
	* Useful when group filters or updates depend on workflow metadata values.
* [Comparison Operators](https://help.bosbec.com/knowledge-base/comparison-operators/)
	* Reference for the operators used when filtering groups by metadata comparisons.


