# Incoming http trigger #


_Will start the workflow if a request to the in.bosbec.io endpoint matches the criteria_

## Properties

* **Method** - Choose the http method the trigger will match on, choose * if it should match on any method
* **Token** - Enter a token that should be used when executing the trigger. Any token can be used, but preferrable a REST API-token/Authentication token because they have a longer lifetime. These are found and created under "Administrator Tools"->REST-Api tokens (format: 00000000-0000-0000-0000-000000000000). The token can be left empty if you want to use different tokens. ***Optional***
* **Path** - By setting this value your request must have a matching path. This should preferrable be used in combination with the subdomain option. ***Optional***
* **Sub domain** - This option enables you to use a subdomain infront of the normal in.bosbec.io domain. ***Optional***
* **Is public** - By setting this to "true" the trigger can be triggered without any provided token. It can be a good option when a resource needs to be shared and it is not possible or required to require authentication. Keep in mind that the resource will be available to anyone with the correct path. ***Optional***
* **Incoming http request resource name** - The name where the request resource will be stored when running the workflow.
* **Incoming unit resource name** - The resource name for the related unit when running the workflow.

## Connections

This job can be connected to the following workflow elements.

* Jobs

## Requirements

* The workflow needs to be activated for the trigger to activate.

## Usage

This trigger reacts to HTTPS-requests to our in.bosbec.io api. The path is different depending on the settings done for the trigger.

The request must use a http verb matching what's configured for the trigger (GET, POST, DELETE...).

When token is provided you can call either:

* https://in.bosbec.io/2/[YOUR_TOKEN] where [YOUR_TOKEN] is the token.
* https://in.bosbec.io/2 and the token as the header `api-key`.

When a path is provided you can call either:

* https://in.bosbec.io/2/[TOKEN]/[PATH] where [TOKEN] is any valid token, or the provided token.
* https://in.bosbec.io/2/[PATH] and any vald token as the header `api-key`.

When a sub domain is provided you can call:

* https://[domain].in.bosbec.io/[TOKEN] where [TOKEN] is any valid token, or the provided token.
* https://[domain].in.bosbec.io/ and any valid token as the header `api-key`.

When both domain and path is given a request can be formed as below.

* https://[domain].in.bosbec.io/[PATH] and any valid token as the header `api-key`.

When is public is set to `true`:

* The requests are formed as above, but don't require any token


When trying to access data from the incoming request, assuming that the request-resource has name `request1`:

* `request1.header.content-type` would get the value in the content-type header.
* `request1.body` gets the body
* `request1.headers` gets all headers comma-separated
* `request1.path` gets the path 
* `request1.full_path` gets the full path
* `request1.method` gets the method eg. post/get
* `request1.querykeys` gets the keys in the query as comma-separated
* `request1.query.x` gets the value for the query-parameter 'x'
* `request1.contenttype` a shortcut to get the contet-type header
* `request1.ip` gets the requester-ip


## Authentication tokens
The authentication tokens used must have permissions to run the trigger or workflow. When resticting the permissions it's possible to set that only a specific trigger or workflow can be started.

One or multiple values can be defined in each Allow definition.

To define a trigger use the following resource configuration:
```
{
    "Resource": "triggers",
    "Allow": [
        "sometrigger",
        "bf3c798a-76ce-4e20-b4c0-5ccb43dc5f07"
    ],
    "Deny": []
}
```
sometrigger is the trigger name
bf3c798a-76ce-4e20-b4c0-5ccb43dc5f07 represents a trigger id that can be triggered


To define a workflow use the following resource configuration:
```
{
    "Resource": "workflows",
    "Allow": [
        "someworkflow",
        "20edb780-a43c-4671-9182-9990bfa7169d"
    ],
    "Deny": []
}
```
someworkflow is the wokflow name
20edb780-a43c-4671-9182-9990bfa7169d represents a trigger id that can be triggered

## Other

If it's possible use the api-token header instead of adding your token to the request path.
