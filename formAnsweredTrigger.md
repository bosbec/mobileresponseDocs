# The form answered trigger #

*Will start the workflow when a form answer is posted for the selected form.*

This trigger will start the workflow and provide a FormAnswer resource to the workflow context, to get information from the form-answer you can combine the trigger with the ExtractData job.  
It is possible to configure the trigger to evaluate a metadata statement and by that be more precis in when to initiate a workflow execution.

  


**Notes:  
The workflow must be inactive in order to save and update triggers.    
The trigger will not catch any incoming form answers while the workflow is inactive.  
This trigger will need a form to be connected, or a form template name to be specified.   
Provides a Form-Answer resource to the workflow context.**


**How to:**  
In the simplest case this trigger will only need you to connect it to a form to be able to start a workflow from an incoming form answer.
