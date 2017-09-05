# Calculate value from metadata #

*This job will perform mathematical calculations based a mathematical expression that may contain WFC resources. Will put the result in WFC resource specified in MetadataDestination.*

To calculate something based on values in WFC resources this job can be configured with an expression like this:  
<code>
[metadata.counter]+1
</code>

Will put the result in the specified MetadataDestination (a WFC resource).


**Notes:  
Will abort if the Expression cannot be parsed/found as WFC resource.**

**How to:**  
Set the Expression to some expression like the example above and make use of WFC resources.  
Set the MetadataDestination to WFC resource where you want the result to go. 


