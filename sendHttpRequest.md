# Send http request

The send http request job is an easy way to perform http requests to external systems to either create a web hook or fetch data for later use within your workflow.

## Properties

The properties for configuring the request are described below.

* **Url** - The url to perform the http request against.
* **Method** - The http method to use for the http request.
* **Headers** - The headers to include in the request. When the header Content-Type is provided, the provided value will be used. When not provided the system determines the most appropriate.
* **Body** - The request body to send with the request.
* **Timeout** - The timeout for the request.
* **Response resource name** - The name of the response resource, where the response is stored.
* **Response type** - In the response type, it's possible to define the type of response that's expected. The response resource will automatically try to parse the response to the provided format.  
Available options are:
  * Auto - The response type till be determined by the Content-Type header from the response.
  * Text - The response is plain text, suitable for html responses.
  * Json - The response has a json payload. The response body will be parsed to a JsonResource.
  * Xml - The response has a xml payload. The response body will be parsed to a XmlResource.
* **Response validation** - Determines how the response should be validated as successful or failed.  
Available options are:
  * Valid response code - Regards all 2XX response codes as successful.
  * Valid response code and response type - The response code must match 2XX and the Content-Type header must match the chosen _Response type_. If _Auto_ is chosen, any Content-Type is valid.
  * No validation - All responses are always regarded as successful.

## Routing

When creating connections to jobs that should be executed after this job, there are three different types of connections that occour at different times. When a response is successful or unsuccessful depends on the setting chosen for property _Response validation_.

* **Jobs** - Will continue immidiately after the request has been sent wihout waiting for the response.
* **Jobs to execute after successful response** - Will continue here after a successful response has been received.
* **Jobs to execute after an unsuccessful response** - Will continue here when a response has returned.

## Response resource

The response resource contains information from the received response that can be used later on in the workflow. The _Body_ will be a parsed resource from the _RawBody_ using the settings provided in the _Response Type_ property.

### Response properties

The properties from the response are:

* **Url** - The url that was requested.
* **Status code** - The status code for the response.
* **Status message** - Information about the response status.
* **Headers** - Contains all response headers received from response.
* **Raw body** - The received body, as we received it.
* **Body** - The received body, parsed to a resource.
* **Body type** - The type of resource the body was parsed to. _StringResource_, _JsonResource_ or _XmlResource_.
* **Response time** - How long time it took before the response was received, in ms.
* **Request time** - The time when the actual request was performed, in UTC.
