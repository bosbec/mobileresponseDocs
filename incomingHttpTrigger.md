# Incoming http trigger #


_Will start the workflow if a request to the in.bosbec.io endpoint matches the criteria_

## Properties

* **Method*** - GET/POST, or use * to indicate that any method is allowed
* **Token*** - REST API-token/Authentication token. Must be a persistent token. Found under "Administrator Tools"->REST-Api tokens (format: 00000000-0000-0000-0000-000000000000)
* **Incoming Resource Name**: -

## Connections

This job can be connected to the following workflow elements.

* Jobs

## Requirements

* The workflow needs to be activated for the trigger to activate.
* Your token needs to be of type "persistent"
* Format for URL used for the trigger to react: `https://in.bosbec.io/2/00000000-0000-0000-0000-000000000000`

## Other

This trigger will react to incoming HTTP-requests to the in.bosbec.io/[YOUR_TOKEN] where [YOUR_TOKEN] is an “AuthenticationToken” or a persisten token that you create in the admin-GUI (located at: www.bosbec.io).  
The workflow will start with a resource called HttpRequestResource that can be accessed from subsequent jobs in the workflow.    
