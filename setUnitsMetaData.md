# Set units metadata#

*This job will set a given metadata on each unit in WFC-temporary group + WFC-groups + those connected in workflow builder.*

The job will get all members from WFC-groups and add to WFC-temporary group.
Then try to find the connected units from the account.
Finally the job will set the given metadata on each of the units.



**Notes:   
Will put WFC-group members in temporary group before adding metadata.**

**How to:**  
Set the property to allow getting metadata values from workflow context. 
(Optionally) connect certain given units to the job to set their metadata as well as the ones in WFC-groups and WFC-temporary group.
