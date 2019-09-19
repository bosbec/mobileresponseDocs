# The process trigger #

*Will start a workflow if a given event occurs within a process on the account.*

This trigger is used to react to the following events:

  * ImportCommandReceived – When the importer first starts the import
  * ImportFailed – When an import-process fail to finish with successful result.
  * ImportFinished – When an import-process has finished.
  * DynamicGroupCreationFinished – When a putting together a dynamic group is done and members matching the given criteria are members in that group.
  
Anyone of the bolded words in the listing above are valid values for the EventType.  
Apart from setting the EventType you may want to specify metadata key and a regex-pattern to test the MetaData of the incoming event.




**Notes:  
The workflow must be inactive in order to save and update triggers.   
The trigger will not react to any events while the workflow is inactive.  
This trigger needs the event type to be defined. **


**How to:**  
Set the Event type to one of the items in the list above. Optionally, set the Meta data key and Regex pattern to have the opportunity to direct different instances, eg. Import 1 triggered in one workflow and import 2 triggered in workflow 2.
