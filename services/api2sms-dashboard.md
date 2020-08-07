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
    max-width: 600px;    
}
</style>

# API2SMS Documentation

An excellent way to test your API calls is to use our Swagger Documentation. You can find this on https://rest.bosbec.io

## Usage
Use the examples of API calls below to send your messages.

### Sending SMS

```JSON
POST: https://rest.bosbec.io/2/workflows

Headers:
"api-key":"00000000-0000-0000-0000-000000000000"
"Content-type":"application/json"

Body
{
  "workflowid": "00000000-0000-0000-0000-000000000000",
  "metadata": {
    "recipient": "+46700000000",
    "sender": "Avsändarnamn",
    "message-text": "Meddelandetext"
  }
}
```

### Get delivery report
To get the delivery status of messages, use the API call below. The guid in the URL is replaced by the process ID of the message you want to look up.

```JSON
GET: https://rest.bosbec.io/2/messages/00000000-0000-0000-0000-000000000000

Headers:
"api-key":"00000000-0000-0000-0000-000000000000"
"Content-type":"application/json"
```

### Response
The response will contain messageId, the recipient number, and the delivery status.

```JSON
{
  "processId": "00000000-0000-0000-0000-000000000000",
  "created": "2016-01-01T00:00:00.0000000Z",
  "messages": [
  {
      "messageId": "00000000-0000-0000-0000-000000000000",
      "to": "+46730000000",
      "status": "Delivered",
      "statusType": 6
   }
  ]
}
```

#### Possible message statuses

* (0) Waiting
* (1) Queued
* (2) Error
* (3) WaitingForAck
* (4) Sent
* (5) Failed
* (6) Delivered
* (7) Expired
* (8) None
* (9) Deleted
* (10) Undeliverable
* (11) Accepted
* (12) Unknown
* (13) Rejected
* (14) Throttled
