# Name of job

_One sentence description of the job, adding a small context_

## Properties

* **Name of parameter*** - Short explanation (e.g with an example) (Required)
* **Name of parameter** - Short explanation (e.g with an example)

## Connections

This job can be connected to the following workflow elements.

* Triggers
* Message Templates

## Requirements

* This requirement needs to be satisfied for the job to work
* This is another requirement

## Other

Put additional information and details about the job here

___

# Data Operations

_Operations, calculations and manipulation on data in workflow context, units, groups, and more_

## Properties

### Calculate data
* **Source*** - Value or source of value. Surround any source of value with `[]` (e.g [metadata.counter]+1)
* **Destination*** - Destination of stored value, could be a resource on the account, or in WFC (e.g `metadata.counter`, or `incomingUnit.metadata.counter`)
* **Order** - Order in which the jobs are executed. Lowest value equals highest priority (e.g 0)

### Concat
* **Source with format*** - String of values (e.g `{incomingUnit.metadata.firstname} {incomingUnit.metadata.lastname}`)
* **Destination*** - Destination of stored concated string, could be a resource on the accound, or in WFC (e.g `metadata.full_name`) 
* **Order** - Order in which the jobs are executed. Lowest value equals highest priority (e.g 0)

### Set data
* **Source*** - Value or source of value (e.g `metadata.phonenumber`, or `+46700000001`)
* **Destination*** - Destination of stored value, could be a resource on the account, or in WFC (e.g `metadata.phonenumber`, or `incomingUnit.metadata.phonenumber`)
* **Order** - Order in which the jobs are executed. Lowest value equals highest priority (e.g 0) 

## Connections

This job can be connected to the following workflow elements.

* Jobs
* Triggers
* Routes

## Requirements

* Fields marked with `*` require input.
* You need to ad the prefix `metadata.` to access data in your WFC

## Other

No further information available.
