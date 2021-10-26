# Extract Data #

*This job is built to extract data from events or complex resources, for example when import is finished, when a dynamic group creation is finished. Another example is to move group members from the workflow groups to the WFC temporary group.*

There are three different features available at this moment (and you can set them either by the exact name or the number):
* GetGroupFromImportFinishedProcessEvent
  * Gets the group(s) from the ImportFinished-event and adds the group to the workflow groups (NOTE: not to the temporary group)
* MoveWorkflowGroupMembersToTemporaryGroup
  * Reads the group-members from the workflow groups, removes those groups from the current execution and adds all members from the workflow groups to the WFC temporary group instead. (This is done so that you may apply WFC temporary group-filters)
  * Unit resource will have a name like unit-resource-1 where the job will try not to overwrite, so if unit-resource-1 exists it will use unit-resource-2
* GetGroupFromDynamicGroupCreationFinishedEvent
  * Just like (1), this extraction finds out what group was just compiled and adds that group(s) to the workflow groups (NOTE: not to the temporary group)
  
**Notes:
Must manually enter one of the “extractions”.
For some of the extractions (1 & 3) it is required that the execution is triggered by a process-trigger.**

**How to:**
Enter one of the actions/extractions and the job will do that.
