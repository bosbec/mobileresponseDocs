# Untag units #

*This job removes tags from units in WFC temporary group and WFC groups.*

The job will read members from all WFC groups and put in WFC-temporary group before removing tags.  
Can remove many tags.


**Notes:   
Removes tags from units on account, not just during the execution.  
Will read WFC-groups into WFC temporary group before removing tags.**

**How to:**  
Set a single tag in the Tag-text field to remove a certain fixed tag.  
Set TagsFromWorkflowMetaData to a WFC-resource and it will split the content of the resources value with comma, semi-colon and space and then remove all of them as tags to remove.
