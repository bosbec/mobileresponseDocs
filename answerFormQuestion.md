# Answer form question #

*This job can answer a question in a form if there is already a form-answer created for the incoming unit. The value used to answer the form-question can be for example, set to use some metadata or the IncomingMessage-body.*

The job will try to find units based on the sender of the incoming message. That implies that there must be an incoming message.  
If unit was found in the given group, this job will set the IncomingUnit resource on WFC to the found unit, and also the IncomingGroupMember resource on WFC to the unit as GroupMember in the given group.  
Then the actual evaluation takes place and the unit is tested if it is a member in the given group. If the unit is a member then the evaluation matches and jobs connected from “Jobs when evaluation match” will be executed, not any other jobs. If the evaluation result was that the unit is not a member in the given group, then the “Jobs when evaluation do not match” will be executed.


**Notes: Will abort if required AnswerSource, FormQuestionName or Form is not set.  
Will also abort if there is no FormAnswers created for the IncomingUnit.  
Will publish a form-answered event.**

**How to:**
Set the AnswerSource to a workflow context resource where the job can find the answer (ex. **incomingmessage.body**). Se the FormQuestionName and make sure that the question-name is the same as the question from the path in the form.
And remember to connect to the Form from this job.
