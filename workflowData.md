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

Syntax for accessing information in the incomingMessage:

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

A form reply can start a workflow and information about the respondent and the form answers is accessible in the Workflow Builder. To access this information, use the job "Extract data" and set the property to "UpdateMetaDataWithFormAnswers". This will transfer all information to the dynamic variables accessible in your workflow.

## Dynamic data in your workflow
Dynamic data are temporary variables used to store, process and calculate information in your workflow. This data is only available when the workflow is running, if you want to store this data temporary you need to save it to your account in a data log or a data unit.

### Metadata
Metadata contains all dynamic variables of your workflow. Store temporary data, place incoming information and calculate new data with this information. To access and store metadata in your workflow, use the syntax below:
* `metadata.[YOUR_DATA]` - Store and/or access dynamic variables in your workflow (e.g `metadata.firstname`)

### Resources

Resources are placeholders for larger enteties than metadata, e.g an API-request, a Unit on the account or a list of data logs. Use "Resources" as a pool for storing and accessing larger and more complex data entities. To access a resource in your workflow, use the syntax below:
* `[RESOURCE_NAME].[YOUR_DATA]` - Access data of a resource (e.g `found_unit.firstname`)

### Temporary group

The temporary group is, as the name would imply, a temporary recipient group in the workflow context used to send messages to. This group contains units only found in the workflow context. If you want to collect and filter certain units on your account for mailings - store them in the temporary group. In the job "Send messages to groups", toggle the checkbox "Use workflow context" to send messages to the temporary group.

### Variable functions

The Bosbec Workflow Builder include built in-functions to alter and create data. Use these functions to create and format dates or generate random characters and values.

**Datetime** - Get the current date and time, set the format inside the parenthesis or leave them blank. Format `[datetime()]` or `[datetime(yyyy-MM-dd)]`

**Subtract time** - Subtract time from a date, remember to use the same time format when subtracting or adding time. Format `[datetime(yyyy-MM-ddTHH:mm:ssZ).subtimespan(000.00:00:00)]`

**Add time** - Add time to a date, remember to use the same time format when subtracting or adding time. Format `[datetime(yyyy-MM-ddTHH:mm:ssZ).addtimespan(000.00:00:00)]`

**Generate random number** - Generate a random number within a certain range: `[rndnum(10,100)]`

**Generate random number** - Generate a random number from 0 up to a certain number: `[rndnum(50)]`

**Generate random characters** - Generate X amount of random characters: `[rndchar(X)]` from the following set of possible characters: `ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyz1234567890!#¤%/>()=?'@£$€{[]}\öäåÅÄÖ`

**Generate random alpa characters** - Generate X amount of random alpha characters (letters): `[rndalpha(5)]`

**Generate random float** - Generate decimal value ranging from 0 to 1: `[rnddecimal()]`

**Set upper case** - In the Destination property, set value to upper case: `.toupper()`

**Set lower case** - In the Destination property, set value to lower case: `.tolower()`

**Count units in resource** - Data Operations/Set Data. In the Source-property add prefix `count()` to the end of the resource. Format: `[resource_name].count()`

## Searching data on your account (page size & page index)

Working with large quantities of units on your account can quickly impact your work. In the admin panel, your Unit dashboard can grow long and it can be difficult to manage units in uyour workflow to manage statistics, mailings or other solutions you build.

In the same way your Unit dashboard divides all units in several pages you can import your unit in pages, with custom page sizes, to work with them in batches. In this way, the workflow can work faster and the Bosbec system will operate better. 

As an example, the workflow job "Unit Operations" let you find units from your account and you decide the amount of units with custom page sizes and the amount pages to import.

**Page size:** Amount of units for each page. If you want to import all your units in one batch, set this value to a high number to include all your units
**Page index:** Which page do you want to import? If you set page size to a low number, e.g. 10 units per page, you can increment the page index to work with several pages, 10 units per page. (Start with 1)

### Example, Two ways of working with 100 units:

**Method 1: Large page size**
Include all 100 units on one page by including all units on one page
Page size: 100
Page index: 1

**Method 2: Several pages with smaller amounts of units per page**
Page size: 10
Page index: metadata.index_counter
Define your index_counter in a Data Operations job before Unit Operations. "Data Operations" and "Set data". Source: 1, Destination: metadata.index_counter 
Increment your page index with "Data Operations" and "Calculate". E.g Source: [metadata.index_counter]+1, Destination: metadata.index_counter.

A general rule of thumb, if you have large quantities of units on your account, use Method 2, and work with units in batches. If you have smaller amount of units, use Method 1 to include all units on one page.
