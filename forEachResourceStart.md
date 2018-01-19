# For Each Resource Start#

*This job will start a "loop" in the workflow if there is a ForEachResourceStop downstreams from this start-job.*

Consider the case where you have a UnitResource containing 5 units and you want to update them in a series of steps. This job will let the workflow execute a sequence of jobs for each of the 5 units in the resource.  
Each time the sequence reaches the ForEachResourceStop-job, it will start over from the location of this ForEachResourceStart-job.  
And each time the loop-sequence starts; this ForEachResourceStart-job will take the next item (unit in this case) in the current resource (the unit resource in this case) and create a temporary resource with the name defined in CurrentItemName. This current item can be addressed by the given name as a single resource of the given type.



**Notes:**

Requires a ForEachResourceStop-job in order to define a loop-sequence.

**How to:**

Drag a ForEachResourceStart-job to the canvas.  
Connect the sequence of jobs to iterate over and set the resource and current-item-name.  
Finish the loop-sequence with a ForEachResourceStop-job.