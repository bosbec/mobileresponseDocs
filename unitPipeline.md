# Unit Pipeline

The Unit Pipeline job manages unit resources through an ordered sequence of steps. Use this job to find, create, update, merge, filter, and manage units within a workflow.

## Properties

The property fields available in Unit Pipeline are described below.

* **Steps** (required)
  * Ordered list of pipeline steps to execute.
  * Available step types include loading resources, finding units, filtering, paging, sorting, metadata updates, merge operations, group operations, and save/delete operations.
* **Alias** (optional)
  * Step-level display name used to make the pipeline easier to read.
* **Execution condition** (optional)
  * Step-level condition for controlling whether a step should run, for example based on previous success or failure.
* **Jobs** (optional)
  * Jobs to execute after the pipeline completes.

## Steps

The step types available in Unit Pipeline are described below.

### Add Channel
Adds a channel to units in the current pipeline resource.

* **Endpoint** (optional)
  * Endpoint configuration to add.
  * Options include Account Endpoint, Administrator Endpoint, App User Endpoint, Email Endpoint, HTTP Request Endpoint, MQTT Endpoint, Phone Endpoint.

### Add Email
Adds an email channel to units in the current pipeline resource.

* **Address** (optional)
  * Email address to add.

### Add Phone
Adds a phone channel to units in the current pipeline resource.

* **Number** (optional)
  * Phone number to add.

### Append Group Connections To Metadata
Appends group connection information to metadata for units in the current resource.

* **Get count** (optional)
  * Include group count.
* **Get names** (optional)
  * Include group names.
* **Get IDs** (optional)
  * Include group IDs.
* **Optional prefix** (optional)
  * Prefix for output fields.

### Clone To Resource
Clones the current pipeline unit resource to a new unit resource.

* **Resource name** (optional)
  * Name of the target unit resource in workflow context.

### Connected Feed Channels
Filters units based on feed channel connection conditions.

* **Let filter** (optional)
  * Action for matching units.
  * Options: **Remove Unit**, **Keep Unit**.
* **Accept push** (optional)
  * Filter by push-accepting app connections.

### Create Unit
Creates unit(s) from mapping values.

* **Mappings** (optional)
  * Field mappings used when creating units.
  * Based on a key/value format. Use {{metadata.key}} to access metadata from workflow context.

### Create Units From CSV Resource
Creates unit(s) from a CSV resource.

* **CSV resource name** (optional)
  * Source CSV resource name.
* **Mappings** (optional)
  * Field mappings used when creating units.
  * Based on a key/value format.
  	* Use format "metadata.key" for key.
	* Use format {{this[0]}} to access first cell in row.
	* This example would result in units with the value from the first cell in each row saved to a key called "key".

### Create Units From JSON Resource
Creates unit(s) from a JSON resource.

* **JSON resource name** (optional)
  * Source JSON resource name.
* **Mappings** (optional)
  * Field mappings used when creating units.
  * Based on a key/value format. Use {{this.key}} to access key in JSON.

### Delete From Account
Deletes units in the current pipeline resource from the account.

### Filter By Channels
Filters units by channel conditions.

* **Where** (optional)
  * Channel match mode.
  * Options: **Has**, **Has No**.
* **Channel priority** (optional)
  * Priority level to evaluate.
  * Options: **Any**, **Primary**, **Secondary**.
* **For channels** (optional)
  * Channel type to evaluate.
  * Options: **Any**, **Phone**, **Email**, **Bosbec Message**, **Legacy App**, **HTTP Request**, **MQTT**, **HTTP Response**.
* **Let filter** (optional)
  * Action for matching units.
  * Options: **Remove Unit**, **Keep Unit**.

### Filter By Data
Filters units by data comparisons.

* **Comparison** (required)
  * Primary comparison rule. See help document [Comparison Operators](https://help.bosbec.com/knowledge-base/comparison-operators/).
* **Additional comparisons** (optional)
  * Additional rules processed in order.
  * Options: **And comparison**, **Or comparison**.
* **Let filter** (optional)
  * Action for matching units.
  * Options: **Remove Unit**, **Keep Unit**.

### Find Duplicates
Finds duplicate units on account and loads them into the current pipeline resource.

* **Duplicate type** (required)
  * Duplicate matching mode.
  * Options: **Duplicate Type**, **Phone Duplicate**, **Email Duplicate**.

### Find From Account
Finds units from account search.

* **Search phrase** (optional)
  * Free text search phrase.
* **Created before** (optional)
  * Upper creation-date limit.
* **Created after** (optional)
  * Lower creation-date limit.
* **Page index** (optional)
  * Page index for account result paging.
* **Page size** (optional)
  * Page size for account result paging.

### Find Unit By Phone
Finds unit(s) by phone number.

* **Phone** (optional)
  * Phone input (for example {{metadata.phone}}).

### Find Units
Finds units matching a selected criteria from a selected source.

* **Matching criteria** (required)
  * Unit search criteria.
  * Options: **Matches Data Advanced**, **Matches Email**, **Matches Metadata**, **Matches Phone**, **Matches Tags**, **Matches Unit ID**, **Retrieved**.
* **In source of units** (required)
  * Source of units to search.
  * Options: **From Account**, **From Group**, **From Temporary Group**, **From Unit Resources**.

### Get Matching Items From Account
Gets account units that match selected channel and/or metadata keys.

* **Channels** (optional)
  * Channel keys to match (for example phone, email).
* **Metadata** (optional)
  * Metadata keys to match.

### Load Resource
Loads a workflow unit resource into pipeline context.

* **Resource name** (optional)
  * Resource name to load.

### Merge Units
Merges units in the current pipeline resource.

More on merging units can be found on [Unit Pipeline: Merging units](https://help.bosbec.com/knowledge-base/unit-pipeline-merging-units/).

* **Group by expression** (optional)
  * Bosbec expression used to group units before merge (for example {{unit.metadata.customer_id}}).
* **Merge target** (required)
  * Selects which unit in each group is updated.
  * Options: **Target Newest**, **Target Oldest**.
* **Merge actions** (required)
  * Selects merge behavior for data transfer.
  * Option: **Overwrite Old Unit Data**.

### Page Units
Applies pagination to the current unit resource.

* **Page index** (optional)
  * Page index.
* **Page size** (optional)
  * Number of units per page.
* **Total pages destination** (optional)
  * Destination for calculated total pages.
* **Total unit count destination** (optional)
  * Destination for total units before pagination.

### Remove From Group
Removes units from group(s).

* **Group identifier** (optional)
  * One or more group identifiers (ID or name).
* **Remove from every group on account** (optional; default: false)
  * Remove matched units from all account groups.

### Remove Metadata
Removes a metadata key from units in the current pipeline resource.

* **Key** (optional)
  * Metadata key to remove.

### Rename Resource
Renames a unit resource in workflow context.

* **Resource name** (optional)
  * Existing resource name.
* **New name** (optional)
  * New resource name.

### Save As JSON Resource
Saves current pipeline unit resource as a JSON resource in workflow context.

* **Resource name** (optional)
  * Target JSON resource name.

### Save As Resource
Saves current pipeline unit resource to workflow context.

* **Resource name** (optional)
  * Target unit resource name.

### Save To Account
Saves units in the current pipeline resource to the account.

### Save To Group
Saves units in the current pipeline resource to a group.

* **Group** (optional)
  * Group target settings.
  * Options: **Existing Group** (Group ID), **New Group** (Name).

### Save To Temporary Group
Saves units in the current pipeline resource to the workflow temporary group.

### Set Metadata
Sets a metadata key/value on units in the current pipeline resource.

* **Key** (optional)
  * Metadata key name.
* **Value** (optional)
  * Metadata value (supports workflow references).

### Sort
Sorts units in the current pipeline resource.

* **Sort units** (required)
  * Sort strategy.
  * Options: **Sort Units By**, **Randomize Order**, **Sort By Metadata Key**, **Sort By Phone**, **Sort By Email**, **Sort By Created Date**.

### Take Units
Keeps only a selected number of units in the current resource.

* **Amount** (optional)
  * Number of units to keep.

### Update All Units With Feed Channels
Updates all units with feed channel data.

### Update Unit Data
Updates unit data for all units in the current resource.

* **Updates** (optional)
  * Key/value updates to apply.
    * For key, use format "unit.metadata.key" or "unit.phone".

## Pipeline behavior

* The pipeline starts with an empty unit resource in its own temporary context.
  * **Load Resource** replaces the current unit resource in the pipeline context.
  * **Find** steps append units to the current unit-resource in the pipeline context.
* The pipeline context is discarded when execution is complete.

## Best practices and tips

* Start the pipeline by loading a resource or finding them from the account.
* Perform the filters, followed by updates.
* Save changes to resource to reference the units later in the process.
* Save changes to account to persist the created or changed units.

## References

* [Unit Pipeline: Merging units](https://help.bosbec.com/knowledge-base/unit-pipeline-merging-units/)
  * Detailed step-by-step guide for duplicate merge scenarios.
* [Comparison Operators](https://help.bosbec.com/knowledge-base/comparison-operators/)
  * Document describing the available operators used throughout the platform.