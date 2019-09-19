# The data log trigger #

*Will start the workflow when a data-log stores a new log item, if that log item matches criteria defined by this trigger.*

If there is another process on your account that store information to the DataLog, you may use this trigger to react when a value is stored in the DataLog. The trigger can be configured with the data log document id or key, and with additional criteria for metadata on that same log item.  


**Notes:  
The workflow must be inactive in order to save and update triggers.    
Trigger won’t react to data-log item updates while the workflow is inactive.**


**How to:**  
Specify any conditions.
