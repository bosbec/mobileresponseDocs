# Getting started: API-requests


## Table of Contents

- Introduction
- Obtain an API-token
- REST-API
   - Set up the REST-API request
   - Data:
   - Request:
   - Response handling:
   - Step-by-step: Process input and output data with REST-API
- HTTP-IN
   - Set up the HTTP-IN URL
   - Step-by-step: Initiate a workflow with HTTP-IN
- Further reading


## Introduction

This document describes techniques of integrating with Bosbec systems and is divided into two
different alternatives of integration; REST API-requests and HTTP-IN API-calls, depending on the type
of communication and requirements for the system. With the use of these techniques, it’s possible
to present live results from forms, retrieve staffing information, update incident management
information, etc. It’s also possible to initiate **workflows** , processes in the Bosbec systems which can
send out messages and emails to your staff, process and structure data, or in other means
streamline and improve the flow of the organisation.

An API, Application Programming Interface, is a set of rules that allow different systems to
communicate. An API will thereby enable functionality and features to be used and shared by
various systems, instead of being developed from scratch. Thus, making the development more
efficient. REST, or Representational State Transfer, determines how that API looks. This is also a set
of rules on how you can use and create these APIs. One of these rules states that you can retrieve a
piece of information with a link to a certain URL.

Each URL is called a **request,** and the data sent back to the system is called a **response.** While REST
API-calls can be more dynamic and offers the possibility to customize the request to receive a certain
response, the HTTP-IN call simple, easy to use and doesn’t require much more than a valid URL.

Bosbec offers functionality to retrieve information in both techniques, and below follows a
description of how you can use them, with examples and templates to get you started quickly.


## Obtain an API-token

For both API-request, an API-token is needed. This token will identify the targeted workflow, but also
act as a validation that a permission for the request is valid. Fortunately, only one token is needed
and it can be used for both REST-API requests aswell as HTTP-IN requests.

Acquire the API-token on the admin page of Bosbec. The proceedings are as follows:

1. Log in to your administrator account at https://bosbec.io/
2. In the navigation sidebar to the left of the admin page, locate “Administrator Tools”, click it
    and select “REST-Api tokens”.
    
![image1](help.bosbec.io/tutorials/img/getting-started-api-requests/image1.png)

3. To create a new API-token, click the plus-sign located in the top right corner.

![image2](help.bosbec.io/tutorials/img/getting-started-api-requests/image2.png)

4. Click “Create” when the pop-up appears, and now your new API-token will be available in
    the list which can be used for both REST-API requests as well as HTTP-IN requests.
    
![image3](help.bosbec.io/tutorials/img/getting-started-api-requests/image3.png)

## REST-API

REST-APIs are dynamic and customizable, where the response can be determined in the request.
Thus, giving full control on what information should be retrieved from Bosbec. This section will go
through the process of setting up the REST-API request and initiate the execution of a Bosbec
process.

### Set up the REST-API request

The anatomy of a request consists of three entities and this section will provide a template to use for
communication with Bosbec and your end system. The following example is written in, although not
restricted to, Javascript. This type of requests works for many programming languages and systems.

### Data:
```
var data = {
  workflowId: "XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX",
  metadata: {
    formid: $scope.formId,
  },
  TriggerNames: "TRIGGER_NAME",
  RequestSettings: {
    "content-type": "application/json",
    ResponseData: {
      // Specify which data you want to get from the Bosbec platform
      answer_summary: "metadata.answer_summary"
    },
  },
};
```
_Code 1: Data which will be sent in the REST API-request_

This is where you decide which information should be accessed from Bosbec. Data also consists of
information that Bosbec workflows should process. To present a form-result, the metadata should
contain an ID for a specific form, and the ResponseData should contain the information from the
form that should be presented.

- **workflowId –** Specify the workflow that should be triggered. This information can be found
    in the settings for the workflow on the admin page.
- **metadata –** Contains the information that the workflow should process, such as staffing
    information, or in the example of Figure 1, input on a web application
- **TriggerNames –** Each workflow have a trigger which will initiate the execution. This trigger
    has a name and needs to be specified in the **data** , since a workflow can have many triggers.
- **RequestSettings –** By providing this property to the **data** , one can customize the response of
    the request. Which data should be returned in the callback? In Figure 1 , a csv-formatted
    string is returned, containing a summary of form answers.
- **content-type –** Should be specified as “json” to get the response as JSON-data, although this
    may vary due to the type of your system.
- **ResponseData –** Defines what resources should be sent back to the system from the call.


### Request:
```
var request = {
  url: "https://rest.bosbec.io/2/workflows/",
  method: "POST",
  headers: {
    "Content-Type": "application/json",
    "api-key": "XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX",
  },
  timeout: 15 * 1000,
  data: data,
};
```
_Code 2: The request to Bosbec_

This is the request to Bosbec REST API and should contain the information that makes the request
arrive correctly.

- **url -** REST-API requests are sent to: https://rest.bosbec.io/2/workflows/
- **method –** Define the method of request. POST, GET, PUT, PATCH or DELETE
- **headers –** The header of the request payload provides information to Bosbec on how the
    request should be processed. An api-key might be necessary to make the request
    authorized.
- **time-out –** Specify how long the request should wait if a response is not received.
- **data –** Provide the data for the request payload.

### Response handling:
```
$http(request).then(
  function (response) {
    // Process the data, e.g plot the data with chart.js
  },
  function (e) {
    error(e);
  }
);
```
_Code 3: Handle the callback from Bosbec_

In Javascript, the request is sent with the use of $http and through this asynchronous call, the
response is processed in a Javascript function.

### Step-by-step: Process input and output data with REST-API

This tutorial will teach the process of how to send data to a Bosbec workflow, process the
information and export that data to an end system. A requirements for this tutorial is that an API-
token is obtained.

The following scenario will act as a practical example of how you can send information to a Bosbec
Workflow with a REST-API request.

- An end system built in Javascript will send user input to the workflow with a REST-API call.
- The workflow will be triggered by the call and built to manipulate the data in the REST-API
    payload.


1. Create the workflow.
    - The workflow is the actual code of your solution and is built in a graphical user interface
       called “Workflow Builder”, a sandbox environment where any solution is built, which
       also is responsible for handling the REST-API call.
    - In the navigation bar on the left side of the admin page, click “Workflows”.

![image4](help.bosbec.io/tutorials/img/getting-started-api-requests/image4.png)

    - Click the plus-sign in the top right corner to create a new workflow.

![image5](help.bosbec.io/tutorials/img/getting-started-api-requests/image5.png)

- Give your workflow a name. For this example the name will be ”rest-api-request”. The
    workflow will be created, and the admin page will redirect to the Workflow Builder. To start
    building your solution, click the button “Open in Workflow Builder”.

![image6](help.bosbec.io/tutorials/img/getting-started-api-requests/image6.png)

![image7](help.bosbec.io/tutorials/img/getting-started-api-requests/image7.png)


- Add a trigger, which will initiate the workflow by
    the REST-API call.
    A trigger is in the toolbar located to the left of
    the Workflow Builder.
    Select the orange lightbulb-job and drag it
    somewhere on the canvas.
    Select “Execution workflow trigger”.

![image8](help.bosbec.io/tutorials/img/getting-started-api-requests/image8.png)

- Give the workflow trigger a name, which will
    later be used in the REST-API call of the end
    system.

![image9](help.bosbec.io/tutorials/img/getting-started-api-requests/image9.png)

- The data which was sent in the REST-API request will be available in the execution data
       of the workflow. This scope of information is called a **workflow context**. So, everything
       that is related to a specific workflow execution (REST-API call, groups, services, export
       data, etc.) is stored in the workflow context. The information that was sent in the REST-
       API call is stored in the workflow contexts **metadata**.


- To access the user input, which was sent by the end system, create a job which will
    handle the input. Use a Data Operation, the red cogwheel-job located in the toolbar on
    the left side of the screen. Drag it to the canvas, next to the trigger. In the search-field,
    search for “Data Operations”, and click it in the list below.

![image10](help.bosbec.io/tutorials/img/getting-started-api-requests/image10.png)

- Click the newly added Data operations-job, select “New Operation” and choose
    “setData”.
- In this example the variable will be named “user_input” and stored in metadata of the
    workflow context. The source is the input from the REST-API (which by the end system is
    called form_input), which is stored in **metadata**. The destination is your new variable.


![image11](help.bosbec.io/tutorials/img/getting-started-api-requests/image11.png)

- Connect the trigger to the newly added job to complete the flow of the work. Hover
    over the “Job”-bar of the orange trigger and drag it to the job you wish to connect.

![image12](help.bosbec.io/tutorials/img/getting-started-api-requests/image12.png)

- Activate the workflow in the top right corner of the screen to make it listen for REST-API
    requests.

![image13](help.bosbec.io/tutorials/img/getting-started-api-requests/image13.png)

2. Build the REST-API request on the end system. In this simple Javascript application, a request
    is built in the same manner which was presented in this document.
    - The source code of the application is presented here:

```
angular.module("app", []).controller("RestApiController", [
  "$scope",
  "$http",
  function ($scope, $http) {
    $scope.submitFormId = function () {

      var data = {
        workflowId: "aaccdb7c- 7805 - 4d66- 8672 - 343fca298c14",
        metadata: {
          form_input: $scope.formId,
        },
        TriggerNames: "handle_rest_api_input",
        RequestSettings: {
          "content-type": "application/json",
          ResponseData: {
            user_input: "metadata.user_input",
          },
        },
      };

      var request = {
        url: "https://rest.bosbec.io/2/workflows/",
        method: "POST",
        headers: {
          "Content-Type": "application/json",
          "api-key": "ac2e5f79-1eca- 4700 - 8a67-453a670fe682",
        },
        timeout: 15 * 1000,
        data: data,
      };

      $http(request).then(
        function (response) {
          console.log(response.data.data.user_input);
        },
        function (e) {
          error(e);
          console.log("Something went wrong");
        }
      );

    };
  },
]);
```

- The user input is captured by the AngularJS controller $scope.formId and packaged in
    the REST-API payload in metadata.


- To get the workflow ID, go to the Workflow-menu on the admin page and click on the
    workflow. A navigation bar will appear on the right side where you will find the
    workflow ID.

![image14](help.bosbec.io/tutorials/img/getting-started-api-requests/image14.png)

- In the request header, add your API-token as “api-key”.
- In ResponseData you can define what data you wish to be sent back to the end system
    as a response. In this example should the newly created variable be sent back.
3. View the results.
- After transmitting the REST-API request of the end system, you can view the result of
the execution in the **workflow context**. Right-click on the workflow and select
“Workflow execution contexts”.

![image15](help.bosbec.io/tutorials/img/getting-started-api-requests/image15.png)

- Select the latest execution in the list and look through the workflow context. There you
    will find a variable with the value “Hello Bosbec!” which was sent as input by the REST
    API-call.

![image16](help.bosbec.io/tutorials/img/getting-started-api-requests/image16.png)

- That is it! From here on now you can modify the input and the output. This input could
    be a staff member which you want to add to a group. The output could be an updated
    group of staff members.


## HTTP-IN

The HTTP-IN call method is suitable for systems that are to be integrated with Bosbec in a more
simple manner. The API for Bosbec is developed that only a valid URL is enough to trigger a workflow
and initiate a process or service within Bosbec. Although, the workflow can still be customized that
data of your choosing can still be exported with only an URL-adress. The requests are being sent to
https://in.bosbec.io/ and by attaching an API token to the URL you will:

1. Associate the token with a corresponding workflow and initiate a workflow sequence.
2. Authenticate the permission of the call, since the API token also acts as a key for the
    request.

### Set up the HTTP-IN URL

The URL only consists of the token, henceforth the template for the HTTP-IN is presented in Figure 4.

https://in.bosbec.io/[API-TOKEN]
_Code 4: Template for HTTP-IN API Request_

The API token can be obtained on the admin page (https://bosbec.io/). Administrator Tools -> REST-
API tokens. Click the plus sign and create a new token. This process is clarified in the Step-by-step
section.

### Step-by-step: Initiate a workflow with HTTP-IN

This is a practical example on how to initiate a workflow sequence with the use of HTTP-IN. The
workflow is initiated with the use of Postman, although any system or browser how can call an URL
address can implement this.

1. Obtain your API-token:
    - If you do not already have a token, create one on the admin page.
    - Traverse to the REST-API token-page, explained below.

![image17](help.bosbec.io/tutorials/img/getting-started-api-requests/image17.png)

- Click the plus-sign in the top right corner to create a new token.

![image18](help.bosbec.io/tutorials/img/getting-started-api-requests/image18.png)

- Your API-token is now available in the list on the “REST-API tokens”-page.

![image19](help.bosbec.io/tutorials/img/getting-started-api-requests/image19.png)

2. Create your HTTP-IN URL:
    - The HTTP-IN URL would therefore look like:

``` https://in.bosbec.io/50f22459-7dde-4ff1-8d16-ed0e83ec ```

_Code 5: HTTP-IN URL_


3. Set up your workflow
    - This workflow will, when triggered by the HTTP-IN, create a unit on the Bosbec Admin
       account. A unit which can be a any arbitrary entity of your choosing, such as a staffing
       member, a certain state of an application, or hold larger amounts of data.

![image20](help.bosbec.io/tutorials/img/getting-started-api-requests/image20.png)

4. Execute the workflow with HTTP-IN
    - This request is sent through Postman, although any browser or URL-handler will be able
       to initiate this request.


![image21](help.bosbec.io/tutorials/img/getting-started-api-requests/image21.png)

5. See the results on the admin page
    - When traversing to the Unit-page, a “John Doe”-unit has successfully been created!

![image22](help.bosbec.io/tutorials/img/getting-started-api-requests/image22.png)

## Further reading
