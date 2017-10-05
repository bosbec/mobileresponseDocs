# Set group member metadata #

*This job sets the metadata of the groupmember (NOT the unit).*

Gets the value to set from ValueSource (which gets a value from a WFC-resource) or defaults to what is written in Value.
The Key is a fixed value and cannot find it’s value from WFC-resources.



**Notes:   
If no incoming unit is present it will set metadata for all members in the selected group.  
If Incoming unit is set the job will only set metadata for that if the incoming units is a group member in the given group.  
Also note that this job sets the GroupMember’s metadata, not the units metadata, but the overridden data for the unit when the unit is treated as member of a group.**

**How to:**  
Connect a group where to set group-member metadata.
Make sure to clear IncomingUnit if you want to set the metadata for all group members.
Set the Key and the Value/ValueSource

