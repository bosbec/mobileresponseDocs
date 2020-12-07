# Form answered trigger #

_Execute a workflow when a form has been submitted._

## Properties

### Metadata match

* **Source*** - 
* **Operator*** - 
* **Value*** - 

## Connections

This job can be connected to the following workflow elements.

* Jobs

## Requirements

* The workflow needs to be activated for the trigger to activate.
* This trigger will need a form to be connected, or a form template name to be specified.   

## Other
This trigger will start the workflow and provide a FormAnswer resource to the workflow context, to get information from the form-answer you can combine the trigger with the ExtractData job.  
It is possible to configure the trigger to evaluate a metadata statement and by that be more precis in when to initiate a workflow execution.
This trigger provides a Form-Answer resource to the workflow context.
