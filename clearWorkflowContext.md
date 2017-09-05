# Clear workflow context #

*This job is used to clear parts of the WFC.*

Clearing temporary group will remove all members that are read into the WFC as group members.  
Clearing Groups will remove all groups from Workflow groups, this means that ExtractData would not find any GroupIds to read group members into the WFC. It also means that there are no Groups that SendMessageToGroups will default back to.  
Clearing IncomingUnit will remove the WFC resource IncomingUnit, and jobs that require the IncomingUnit will fail, unless it is set/made available again.  
Clearing IncomingGroupMember removes the IncomingGroupMember from WFC, with the similar consequences as removing IncomingUnit.  
ClearMetaData is a RegEx expression that will test each key in the WFC metadata and remove if it matches. This means setting ClearMetaData to: .* will cause all metadata to be removed.



**Notes:  
If ClearMetaData is left empty, then the job will NOT clear any metadata.  
ClearMetaData is a RegEx-expression.**

**How to:**  
Set what properties to clear.   
Remember that ClearMetaData is RegEx-expression and written in text, the others are true/false selected from the list.

