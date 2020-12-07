# Executing workflow trigger #

_Used to manually execute a workflow._

## Properties

No parameters available

## Connections

This job can be connected to the following workflow elements.

* Jobs

## Requirements

* The workflow needs to be activated for the trigger to activate.

## Other

Select "Run" in the top right corner and select the name of your trigger. Click run to execute the workflow.

This trigger is used for almost every service that can be accessed from the services section in www.bosbec.io. The trigger will react to API-request to api2.bosbec.io/workflows/execute and to api2.bosbec.io/workflows/execute-with-parameters. The latter is preferred, since it will provide the workflow with metadata specified in the request. 
