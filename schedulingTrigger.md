# The scheduling trigger #

*Will start a workflow on a given schedule.*

This trigger is used to start a workflow once or repeat the execution according to a schedule. For example, you may configure one workflow to execute every Monday, while another will execute every hour of every day.  
This trigger is useful for scenarios where you have recurring tasks, for example heartbeat and monitoring of some external system or daily import/exports.



**Notes:  
The workflow must be inactive in order to save and update triggers.    
The trigger will not start while the workflow is inactive. **


**How to:**  
Set the Event type to one of the items in the list above. Optionally, set the Meta data key and Regex pattern to have the opportunity to direct different instances, eg. Import 1 triggered in one workflow and import 2 triggered in workflow 2.
