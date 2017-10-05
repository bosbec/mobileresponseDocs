# Unique sender route #

*Will make sure that the sender of the incoming message only passes through to the “Jobs when evaluation match” one time.*

This job can be configured with a manually created group or it will automatically generate a group upon first execution and update itself.  
The job stores units in a group to make sure that the incoming sender only can pass through to the “JobsWhenEvaluationMatch” one time, and the rest of the times it will continue with “JobsWhenEvaluationDoNotMatch”.



**Notes:   
Requires sender of incoming message**

**How to:**
Create a group or let the job create it for you once executed the first time.  
Connect jobs to the “JobsWhenEvaluationMatch” if you just want those jobs to be executed one time per unit/sender.

