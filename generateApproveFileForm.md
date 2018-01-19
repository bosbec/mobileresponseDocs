# Generate approve file form #

*Use this job to generate a predefined form to collect approval for a file (ex. invoice pdf).*

The job creates a temporary form template and adds it to the workflow context, so that a SendMessage-job may generate a form-link for each receiver.  
It is possible to set the different texts in the form that presents a file, some information and two accept/reject alternatives to the respondent.  
It is also possible to add hidden data to the form and make use of that hidden data when the form-answer is incoming (via the form-answer-trigger)  
Most properties can get data from WFC-resources.



**Notes:**

Need Incoming File in wfc.


**How to:**

Using this job is pretty much the same as ForwardMessageToEveryone, except you need a specified group in this case.
