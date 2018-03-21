There are two ways of using the service:

1. Make a request to generate a code and send message to the user. Collect the code from the
user and make a second request to verify the code.
2. Make a request to generate a code and send message to the user and ask to include the
generated code in the response.

For each call to the rest api you must include your “api-token” and declare the “content-type” to
“json/application”.

You can find your api token, or create a new one, under Tools -> REST-api tokens in the top navigation menu.

**Request Case 1**

Create code and send message to user

**[POST] https://rest.mobileresponse.io/1/workflows**

```
{
"workflowid": "00000000-0000-0000-0000-000000000000",
"metadata": {
  "receiver": "+46707123456"
  }
}
```

**Response**

```
{
"processId": "5506eeff-169a-406b-b4a5-87d7f49148df",
"created": "2017-05-05T06:59:53.3720470Z"
}
```
**Request to check if code is valid**

**[POST] https://rest.mobileresponse.io/1/workflows**

```
{
  "workflowid":"00000000-0000-0000-0000-000000000000",
    "triggernames":"validate-code",
    "metadata": {
    "current-code":"12345"
},
"RequestSettings" : {
    "content-type": "json",
    "ResponseData": {
      "code-is-valid": "metadata.code-is-valid"
    }
  }
}
```

**Response**

```
{
  "data": {
    "code-is-valid": "false"
  },
  "processId": "ff5ba0a0-09c3-4ebb-99e5-64eca041096d",
  "executionTime": 585
}
```

**Request case 2**

Create code, send message to user and include the generated code in response

**[POST] https://rest.mobileresponse.io/1/workflows**

```
{
  "workflowid": "00000000-0000-0000-0000-000000000000",
  "triggernames":"generate-code",
  "metadata": {
    "receiver": "+46707123456"
},
"RequestSettings": {
  "content-type": "json",
  "ResponseData": {
    "current-code": "incomingunit.metadata.current-code"
    }
  }
}
```

**Response**

```
{
  "data": {
    "current-code": "12345"
  },
  "processId": "5c657f4a-1f7d-4c7f-8b91-f11d88d1b834",
  "executionTime": 880
}
```
