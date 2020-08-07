<link rel="stylesheet" type="text/css" href="https://raw.githubusercontent.com/bosbec/mobileresponseDocs/master/services/text-dashboard.css">

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
