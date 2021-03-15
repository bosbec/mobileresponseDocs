# Remote http request #

_Send HTTP request and handle the HTTP response._

## Properties

* **Url*** - Web URL to send your request to
* **Http method*** - GET, POST, UPDATE or DELETE
* **Http header** - Headers for your request. Format: `example-header: ExampleHeader`
* **Post template** - Template and content of the request body for POST. Format: `key1=value1&key2=[metadata.value2]`
* **Content type** - Content type for POST template (e.g `application/x-www-form-urlencoded`)

### Remote http response settings

* **Continue on any requewst error** -
* **Response status code destination** - Destination of status code of response, could be a resource on the account, or in WFC as metadata (e.g `metadata.response_code`)
* **Response body destination** - Destination of body of response, could be a resource on the account, or in WFC as metadata (e.g `metadata.response_body`)
* **Response header destination** - Destination of header of response, could be a resource on the account, or in WFC as metadata (e.g `metadata.response_header`) 

## Connections

This job can be connected to the following workflow elements.

* Jobs

## Requirements

* Some properties are required input to conduct the HTTP request.

## Other
