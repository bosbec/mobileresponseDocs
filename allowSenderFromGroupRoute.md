# Allow Sender From Group Route   #

*This job is used for evaluating if the unit found in the incoming message is member in the given group. The job then performs routing by making a decision on what next jobs to confinue with.*

The job will try to find units based on the sender of the incoming message. That implies that there must be an incoming message.  
If unit was found in the given group, this job will set the IncomingUnit resource on WFC to the found unit, and also the IncomingGroupMember resource on WFC to the unit as GroupMember in the given group.  
Then the actual evaluation takes place and the unit is tested if it is a member in the given group. If the unit is a member then the evaluation matches and jobs connected from “Jobs when evaluation match” will be executed, not any other jobs. If the evaluation result was that the unit is not a member in the given group, then the “Jobs when evaluation do not match” will be executed.



**Notes: 
Jobs connected from the regular jobs-connection will not be executed.  
Any IncomingMessage-trigger will provide the IncomingMessage resource on WFC.  
Sets the IncomingGroupMember.  
Sets the IncomingUnit.**

**How to:**
Drag the job to the canvas and make sure that is connected after the place that sets the IncomingMessage in the workflow (ex. Somewhere in the after an IncomingMessageTrigger).  
Connect next jobs to either one of the two “Jobs when evaluation…” depending on if you want the job to execute when unit was member in group or not.
