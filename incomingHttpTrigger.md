# The incoming http trigger #

*Will start the workflow if a request to the in.bosbec.io endpoint matches the criteria. *

This trigger will react to incoming HTTP-requests to the in.bosbec.io/[YOUR_TOKEN] where [YOUR_TOKEN] is an “AuthenticationToken” or a persisten token that you create in the admin-GUI (located at: www.bosbec.io).  
The workflow will start with a resource called HttpRequestResource that can be accessed from subsequent jobs in the workflow.    


**Notes:  
The workflow must be inactive in order to save and update triggers.  
The trigger will not catch any incoming requests while the workflow is inactive.  
Provides an incoming message to the workflow context.**


**How to:**  
Set the Method to GET / POST or use * to indicate that any method is allowed. Set the Token to the id of one of your persistent tokens (created inside www.bosbec.io). Optionally set the resource name.
