# Send message to groups except in group #

*This job works like SendMessageToGroups but will remove units that are present in the “ExceptGroup”. Think of this as a SendMessageToGroups with a stop-group that stops some units from receiving messages (will not stop if a new unit with same phone/email… is created).*


Sends to groups, but not to the members of the Except-group.  
See SendMessageToGroups for more details.  


**Notes:   
Sets defaults for MessageTemplates (only app-message in this case)  
Defaults to WFC-groups and WFC-temporary group.**

**How to:**  
Set the except-group.
Set the message tempalate.
(Optionally) Set the groups.
