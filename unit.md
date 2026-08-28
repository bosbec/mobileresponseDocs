# Units

Units are the primary data storage concept in Bosbec.

A unit is a flexible entity model where you store data in metadata using key/value pairs. You decide what each unit represents based on your use case, then save the attributes you need as metadata keys.

## Core concept

Use units to model both people and non-human entities, for example:

* A person with contact details
* An order with order ID, status, and totals
* A device with battery level and temperature
* A time slot, activity, or other process state object

This means units are not primarily "receivers". A receiver is only one possible use case of a unit model.

## Data model

Data is mainly stored in metadata.

* A metadata key identifies a field, for example: order_id
* A metadata value stores the current value for that key, for example: 123456

Metadata can be used temporarily in a workflow context or stored more permanently on resources such as units.

## Referencing syntax

Read values from workflow context metadata:

* {{metadata.key}}

Read values from unit metadata:

* {{unit.metadata.key}}

Write values to metadata destinations:

* metadata.key
* unit.metadata.key

## Channels on units

Units can also include channels such as phone, email, app user, or IoT/MQTT-related endpoints when communication is needed.

Channels are optional. Many unit models use no communication channels at all and only store structured metadata.

## Operational usage in workflows

In workflows, units are often processed through a staged pattern:

* Find or load units from account, groups, temporary group, or resources
* Filter units by channel or metadata criteria
* Update unit metadata or channels as needed
* Persist units to account, group, temporary group, or workflow resource

Temporary Group is execution-scoped and useful for in-run processing. Account-level resources such as units and groups are persistent and remain available after workflow completion.

## Best practices

* Define a clear metadata naming strategy early (for example: snake_case keys).
* Store canonical identifiers on units (for example: customer_id, order_id, external_id).
* Use metadata for the current state; use Data log when historical change tracking is required.
* Model units around business entities first, then add channels only when messaging is part of the flow.

## Related concepts

* Metadata
* Workflow Context
* Data log
* Groups
* Unit Operations
* Unit Pipeline

## References

* [Platform-specific concepts](https://help.bosbec.com/knowledge-base/platform-specific-concepts/)
	* Overview of core Bosbec concepts including Units as primary storage.
* [Working with variables](https://help.bosbec.com/knowledge-base/working-with-variables/)
	* Metadata syntax, resource access patterns, and expression examples.
* [Terminology](https://help.bosbec.com/knowledge-base/terminology/)
	* Definitions for Units, Metadata, Data log, and Workflow Context.


