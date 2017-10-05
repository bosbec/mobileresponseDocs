# Untag units #

*This job tags units in WFC temporary group and WFC groups.*

The job will read members from all WFC groups and put in WFC-temporary group before adding tags.  
Can add many tags.



**Notes:   
Adds tags to units on account, not just during the execution.  
Will read WFC-groups into WFC temporary group before adding tags.**

**How to:**  
Set a single tag in the Tag-text field to add that tag.  
Set TagsFromWorkflowMetaData to a WFC-resource and it will split the content of the resources value with comma, semi-colon and space and then add all of them as tags to each unit.

