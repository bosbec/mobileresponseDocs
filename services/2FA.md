There are two ways of using the service:

1. Request to generate a code and send a message to the user. Then, collect the code from the user and make a second request to verify the code.
2. Request to generate a code, send a message to the user, and ask to include the generated code in the response.

For each call to the rest API, you must include your "API-token" and declare the "content-type" to "json/application".

You can find your API token, or create a new one, under Tools -> REST-api tokens in the top navigation menu.

##### Request Case 1

Create code and send message to user

**[POST] https://rest.bosbec.io/2/workflows**

```
{
"workflowid": "00000000-0000-0000-0000-000000000000",
  "triggernames":"generate-code",
"metadata": {
  "receiver": "+46707123456"
  }
}
```

**Response**

```
{
"processId": "00000000-0000-0000-0000-000000000000",
"created": "2017-05-05T06:59:53.3720470Z"
}
```
**Request to check if code is valid**

**[POST] https://rest.bosbec.io/2/workflows**

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
  "processId": "00000000-0000-0000-0000-000000000000",
  "executionTime": 585
}
```

##### Request case 2

Create code, send message to user and include the generated code in response

**[POST] https://rest.bosbec.io/2/workflows**

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
  "processId": "00000000-0000-0000-0000-000000000000",
  "executionTime": 880
}
```
