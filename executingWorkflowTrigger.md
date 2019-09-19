# The executing workflow trigger #

*Will start the workflow when an API-request to the api2.bosbec.io/workflows/execute is issued.*

This trigger is used for almost every service that can be accessed from the services section in www.bosbec.io. The trigger will react to API-request to api2.bosbec.io/workflows/execute and to api2.bosbec.io/workflows/execute-with-parameters. The latter is preferred, since it will provide the workflow with metadata specified in the request.  
The trigger needs no setup. Drag it to the canvas and connect to jobs. The metadata provided by the API-request will be available when the workflow starts.



**Notes:  
The workflow must be inactive in order to save and update triggers.    
Trigger won’t execute workflow while workflow is inactive.**


**How to:**  
Specify any conditions for example set the path pattern and upload a file to the given path and this trigger should start a workflow execution.
