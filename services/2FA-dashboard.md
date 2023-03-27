<style>
    .dashboard-container h1,.dashboard-container h2,.dashboard-container h3,.dashboard-container h4,.dashboard-container h5,.dashboard-container p {
    color: #353A40;
}
.dashboard-container h1 {
    font-weight: 400;
    font-size: 32px !important;
    margin-top: 0;
}
.dashboard-container h2 {
    font-weight: 400;
    font-size: 24px;
}
.dashboard-container h3 {
    font-weight: 400;
    font-size: 20px;
}
.dashboard-container h4 {
    font-weight: 400;
    font-size: 16px;
}
.dashboard-container h5 {
    font-weight: 400;
    font-size: 13px;
    letter-spacing: 0px;
}
.dashboard-container p {
    font-weight: 400;
    font-size: 13px;
}
.service-component {
    max-width: 580px;    
}
</style>

# Two-factor authentication

Two-factor authentication, or multi-factor authentication, is a method for granting access to a user after successfully presenting at least two pieces of evidence. This evidence, or factors, is a combination of something they know (e.g., password) and something they have (2FA-code) or something they are. This documentation will explain how the Bosbec Two-factor authentication service is used.

## Usage
There are two ways of using the service:

1. Request to generate a code and send a message to the user. Then, collect the code from the user and make a second request to verify the code.
2. Request to generate a code, send a message to the user, and ask t include the generated code in the response.

For each call to the REST API, you must include your API token and declare the "content-type" to "json/application". You can find your API-token or create a new one on the Bosbec admin interface. Select "Administrator Tools" -> "REST Api-token" in the navigation menu.



### **Request case 1: Create a code and send message to user**

**POST-request https://rest.bosbec.io/2/workflows**

```JSON
{
  "workflowid": "00000000-0000-0000-0000-000000000000",
  "triggernames":"generate-code",
  "metadata": {
    "receiver": "+46707123456"
  }
}
```

**Response**

```JSON
{
    "processId": "00000000-0000-0000-0000-000000000000",
    "created": "2017-05-05T06:59:53.3720470Z"
}
```

### **Request case 2: Request to check if code is valid**

**POST-request https://rest.bosbec.io/2/workflows**
```JSON
{
    "workflowId":"00000000-0000-0000-0000-000000000000",
    "triggernames": "validate-code",
    "metadata": {
        "current-code":"12345"
    },
    "RequestSettings": {
        "content-type":"json",
        "ResponseData": {
            "code-is-valid": "metadata.code-is-valid"
        }
    }
}
```

**Response**
```JSON
{
    "data": {
        "code-is-valid":"false"
    },
    "processId": "00000000-0000-0000-0000-000000000000",
    "executionTime": 585 
}
```

### ***Request case 3: Create code, send message to user and include the generated code in the response***

**POST-request https://rest.bosbec.io/2/workflows**

```JSON
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


```JSON
{
  "data": {
    "current-code": "12345"
  },
  "processId": "00000000-0000-0000-0000-000000000000",
  "executionTime": 880
}
```
