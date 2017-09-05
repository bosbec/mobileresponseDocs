# Allow Form Answer From Groups Route   #

*This job is used for evaluating if the unit found in the form-answer is member in any of the given groups. The job then performs routing by making a decision on what next jobs to confinue with*

The job will first make sure that there is a FormAnswer in the WFC.  
Then that it can match the form answer to a unit.  
Then the actual evaluation takes place and the unit is tested whether or not it is a member in any of the given groups. If the unit is a member then the evaluation matches and jobs connected from “Jobs when evaluation match” will be executed, not any other jobs.




**Notes: 
Jobs connected from the regular jobs-connection will not be executed.
FormAnswerTrigger will provide a FormAnswer in the WFC.**

**How to:**
Make sure that the job is connected after the place that sets the FormAnswer in the workflow (ex. Somewhere in the job-chain after a FormAnsweredTrigger).  
Connect next jobs to either one of the two “Jobs when evaluation…” depending on if you want the job to execute when unit was member in any of the groups or not.
