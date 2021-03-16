<!--# Workflow data -->

<!-- Workflows can manage information both on your account, as well as dynamic content in specific executions. Information or data could be sent to a workflow, calculated or created in an execution or located as a temporary resource. Use this section to understand how you can work with data and information on the Bosbec Workflow Builder. -->

## Incoming data
Depending on your workflow trigger, your workflow can react on different events. In this way, you can trigger a workflow with an SMS, email, API-request or a form reply. Here you will find information about how to access and work with incoming data to your workflow.

### Incoming message
SMS or email messages can trigger a workflow and the information about this triggering event is stored in the workflow context as the resource "incomingMessage". The `incomingMessage` consists of different parameters which hold information about the message. Below is an example of an incoming SMS message and how you can access that information in the workflow builder:

```
"incomingMessage": {
  "sender": "+46700000001",
  "message": "Hello Bosbec!",
  "to": "+46700000002",
  "toList": [
    "+46700000002"
  ],
  "metaData": null
},
```
_Example of an incoming SMS message_

Syntax för accessing information in the incomingMessage:

* `incomingmessage.body` - Access the message body
* `incomingmessage.sender` - Access the sender (String-object)
* `incomingmessage.receivers` - Get all receivers in a comma separated list (incl. CC and BCC for email)
* `incomingmessage.receiver` - Get the main recipient.
* `incomingmessage.subject` - Get the email subject.
* `incomingmessage.image` - Access the image link (app message).
* `incomingmessage.longitude` Access longitud (app message)
* `incomingmessage.latitude` Access latitud (app message)

### Incoming unit/group member

Syntax for accessing information about an incoming group member (Only accessible for the job "AllowSendersFromGroup"):
* `incominggroupmember.metadata.[YOUR_METADATA]` - Get metadata from an incoming group member

Syntax for accessing information about an incoming unit:
* `incomingunit.phone` - Get the phone number of an incoming unit
* `incomingunit.phonenumber` - Get the phone number of an incoming unit
* `incomingunit.email` - Get the email of an incoming unit
* `incomingunit.emailaddress` - Get the email of an incoming unit
* `incomingunit.metadata.[YOUR_METADATA]` - Access metadata of an incoming unit

### Incoming API-request

API-request contains information which is accessible in the Workflow Builder. The request information will be placed in the workflow resource `request_resource`. 

```
"request_resource": {
  "request": {
    "body": "{\"example-key\":\"example-value\"}",
    "headers": {
      "accept": "*/*",
      "accept-Encoding": "gzip, deflate, br",
      "authorization": "12ce70c7-637a-45fb-91c8-6dc7d5b83748",
      "host": "in.bosbec.io",
      "user-Agent": "PostmanRuntime/7.26.10",
      "content-Length": "0",
      "x-Forwarded-For": "46.59.120.112",
      "x-Forwarded-Proto": "https",
      "x-Forwarded-Port": "443",
      "x-Amzn-Trace-Id": "Root=1-ac1f01f6-86574e5688d7159bc3a19351",
      "postman-Token": "8c190e7e-e73a-485f-acbe-45ffbba00fd5"
    },
    "queryString": "?input=Would%20you%20like%20some%20pancakes?",
    "query": {
      "example-key2": "example-value2"
    },
    "token": "a7e7dab6-f930-4be2-93a0-3ab252ce6e1b",
    "requesterIpAddress": "::ffff:10.0.11.237",
    "createdOn": "2021-03-15T13:39:48.07Z",
    "_type": "incomingHttpPost"
  },
  "contentType": null,
  "multitude": "none",
  "_type": "httpRequestResource"
},
```
_Example of an API-request_

To access and parse out information from an API-request use the syntax below:
* `request_resource.body` - Access the body of the API-request
* `request_resource.headers.[YOUR_HEADER]` - Access a header in the API-request
* `request_resource.queryString` - Get the entire query string
* `request_resource.query.[YOUR_QUERY_KEY-VALUE]` - Access specific key-values in the request query.

To access specific key-values in the request body, use the job "Parse json to resource". Your request body will now be accessible as a resource. To access specific key-value, use the following syntax:
* `[RESOURCE_NAME].[KEY-VALUE]` - Access key-values of a JSON resource

### Incoming Form Answers

A form can trigger an execution of a workflow and information about the respondent and the form answers are accessible in the Workflow Builder. To access this information, use the job "Extract data" and set the property to "UpdateMetaDataWithFormAnswers". This will transfer all information to the dynamic variables of the workflow context.

## Dynamic data in your workflow
Dynamic data are temporary variables used to store, process and calculate information in your workflow execution. This data is only stored during the execution, similar to a RAM-memory of your computer - this data needs to be stored manually in a resource on the account to save it after execution.

### Metadata
Metadata contains all dynamic variables of your workflow. Store temporary data, place incoming information and calculate new data with this information. To access and store metadata in your workflow, use the syntax below:
* `metadata.[YOUR_DATA]` - Store and/or access dynamic variables in your workflow (e.g `metadata.firstname`)

### Resources

Resources are placeholders for larger enteties than metadata, e.g an API-request, a Unit on the account or a list of data logs. Use "Resources" as a pool for storing and accessing larger and more complex data entities. To access a resource in your workflow, use the syntax below:
* `[RESOURCE_NAME].[YOUR_DATA]` - Access data of a resource (e.g `found_unit.metadata.firstname`)

### Temporary group

The temporary group is, as the name would imply, a temporary recipient group in the workflow context used to send messages to. This group contains units only found in the workflow context. If you want to collect and filter certain units on your account for mailings - store them in the temporary group. In the job "Send messages to groups", toggle the checkbox "Use workflow context" to send messages to the temporary group.
