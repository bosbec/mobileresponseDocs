# Groups

Groups are collections of units, organized based on intended use.

What a group represents depends on how the units in it are used. A group can represent recipients, products, time slots, activities, or other business concepts.

## Core concept

Groups only contain units. You cannot group other resource types directly.

Common examples:

* Send a message to multiple recipients at once
* Collect units that represent time slots in a booking flow
* Collect units that represent products in a list or selection flow

## Group types

Groups can be static or dynamic.

* Static group
	* Units are manually added and removed, either in Admin or via workflows.
* Dynamic group
	* Units are included automatically based on a tag rule and kept in sync over time.

## Metadata on groups

Groups can also have metadata.

Group metadata is currently commonly used by Admin UI to display custom properties in group member views, and can also be used in workflows depending on the solution design.

## Operations in workflows

Groups are commonly used as both sources and destinations in workflow jobs.

Common operations include:

* Load units from an existing group
* Save units to a group
* Remove units from one or more groups
* Use temporary group membership during execution-only processing

Temporary Group is execution-scoped and exists only in the current workflow run. Account groups are persistent and remain available after execution.

## Best practices

* Name groups by purpose, not by implementation details.
* Use static groups for curated sets and explicit membership control.
* Use dynamic groups when tag-based auto-sync is the desired behavior.
* Keep the unit model consistent so grouping and downstream filtering remain predictable.

## Related concepts

* Units
* Metadata
* Dynamic Group
* Group Operations
* Save To Group

## References

* [Terminology](https://help.bosbec.com/knowledge-base/terminology/)
	* Definition of groups, including static and dynamic behavior.
* [Platform-specific concepts](https://help.bosbec.com/knowledge-base/platform-specific-concepts/)
	* Context for how units and related concepts are used in integrations.