# Data log trigger #

*Will start the workflow when a data-log stores a new log item, if that log item matches criteria defined by this trigger.*

## Properties

* **Data log document id*** - 
* **Data log key*** - 

### Criteria: Log item value criteria

* **Left side*** - 
* **Right side*** - 
* **Operator*** - 

### Criteria: Data log match criteria

No parameters available

## Connections

This job can be connected to the following workflow elements.
* Jobs

## Requirements
* The workflow needs to be activated for the trigger to activate.

## Other
If there is another process on your account that store information to the DataLog, you may use this trigger to react when a value is stored in the DataLog. The trigger can be configured with the data log document id or key, and with additional criteria for metadata on that same log item.  
