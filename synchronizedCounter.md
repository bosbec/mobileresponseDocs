# Unique sender route #

*This job is a counter, and the synchronized-part of the name indicates that it will synchronize the counting even if there are many workflows that simultaneously want to increase the counter.*

The counter name is just the name of a counter and in combination with the counter key it creates a unique counter with a counter limit and current value and so on.  
For example, if I want my counter to limit the executions per incoming email address, I would set up a counter with the name **emailcounter** and dynamically use the different email sender addresses as a key.  

> So if sender1@mobileresponse.io sends email to the workflow the counter **emailcounter + sender1@mobileresponse.io** will increase its current value, but the counter **emailcounter + another_sender@mobileresponse.io** will not increase.

**CounterName**, **CounterKey**, **CounterLimit**, **RequestedIncrement**, **MinIncrementChunkSize** can all be set either as the value direct or set as a WFC-resource containing the value.  
*RequestedIncrement* and *MinIncrementChunkSize* will default to 1 if no other valid value is set.



When the counter is executed, it will produce a result and a current value that can be put in any available workflow metadata or equivalent resource.
The results are:

- OK – which means that increasing the current value for the counter was OK, no limit was reached or already passed. Ex. the limit is 10 and the counter is now 3.
- Limit reached – which means that there are no more room to continue counting. Ex. the limit was 10 and the counter is now 10.
- Fail – means that it is not possible to increase the counter, and no increment has been made. Ex. limit was 10, counter value was 10 before trying to increase, counter value is 10 after job execution as well.

Another thing to mention here is that the RequestedIncrement and MinIncrementChunkSize can be for some cases when counting.   
The RequestedIncrement is how much we want to increase the counter with at the time of execution. (It can be a dynamic value from a WFC resource or a fixes value configured on the job).  
For example RequestedIncrement can by 2 and each time the counter is executed the value will increase with 2. Ex. **First execution: 2**, **Second execution 4** …  

MinIncrementChunkSize, on the other hand is used together with the RequestedIncrement. It tells the job if it is allowed to increase the counter-value by a part of the RequestedIncrement.  
So if the RequestedIncrement is 2, but the MinIncrementChunkSize is 1 it means that such a counter can have an odd number (ex. 3) as limit, even though we increase it with 2 (most of the time). Ex. **First execution: 2**, **Sencond execution**: *cannot increase with RequestedIncrement (2), will attempt a smaller chunk (1), and that works result:* **3**



**Notes:   
The job will execute next jobs even if the result is Limit reached or Fail, and you need to use the result in ExeccutionRules or MetadataRoutes.  
For now this job is designed to be used with counting “up”, that is +, adding and increasing the numbers.**

**Tip: Use in combination with the ResetSynchronizedCounter job!**
 


**How to:**
Set a counter name (usually you will just need one counter name for a workflow, since you have counter key to make it unique within a workflow)
Set the counter key, counter limit... and the other properties as described above.
Remember to set the output value and result to make use of it when routing after the job is executed.
