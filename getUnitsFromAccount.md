# The get units from account #

*This job will find units from your account, from a number of different find criteria/options. Can be used to set the incoming unit to the result of find operation (if the result is only one unit found).
The found units can be put in a group or in WFC temporary group.*

If you set the UseWorkflowContextMetaDataValue to true, it means that phone and email criteria can get their values from WFC-resources, Ex. metadata.phone-number otherwise it will simply try to find a phone with the number metadata.phone-number and that won’t happen, since it is not a valid phone number.  
The same goes for metadata criteria; if using values from WFC the job will try to find values first, otherwise it will simply try to find what was put in as text.  
The with- and without-tags will treat every comma, semi-colon and space as a separator between tags that add to the find criteria.  


If a group is set, then the job will put found units into that group instead of adding them to WFC temporary group.


If the property SingleFoundUnitAsIncomingUnit is set to true, and the job found exactly one (1) unit. Then the job will set the found unit as the incoming unit.




**Notes:  
Can set the IncomingUnit.  
Will not create units, only find existing units.**


**How to:**  
Set the criteria for phone/email, tags and metadata.  
Toggle if a single found unit will set the incoming unit.  
Toggle whether or not to use WFC-resources / metadata to replace the critera-parts.


