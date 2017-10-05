# Send Message With File Information To Groups #

*This job sends file-information as AppMessageMetadata to group members.*

The job was designed as a Proof of concept when workflows began to handle files and are focused on forwarding file-information to app-messages.  
Adds AppMessageMetadata with the file information (the files in WFC-files resources)



**Notes:   
Sets defaults for MessageTemplates (only app-message in this case)
Defaults to WFC-groups and WFC-temporary group.
Need files in WFC-resource.**

**How to:**  
Basically it can be used lik SendMessageToGroups.