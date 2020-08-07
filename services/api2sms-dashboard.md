<style>
    h1,h2,h3,h4,h5,p {
    color: #353A40;
}
h1 {
    font-weight: 300;
    font-size: 96px !important;
    letter-spacing: -1.5px;
}
h2 {
    font-weight: 300;
    font-size: 60px;
    letter-spacing: 0.01px;
    margin-bottom: 16px;
    padding-top: 52px;
}
h3 {
    font-weight: 400;
    font-size: 48px;
    letter-spacing: 0px;
}
h4 {
    font-weight: 400;
    font-size: 34px;
    letter-spacing: 0.25px;
}
h5 {
    font-weight: 400;
    font-size: 24px;
    letter-spacing: 0px;
}
h6 {
    font-weight: 500;
    font-size: 18px;
    letter-spacing: 0.15px;
    color: #353A40;
    text-align: left;
    line-height: normal;
}
p {
    font-weight: 400;
    font-size: 16px;
    letter-spacing: 0.01px;
}
</style>

### API2SMS Documentation

An excellent way to test your API calls is to use our Swagger Documentation. You can find this on https://rest.bosbec.io

#### Usage

##### Sending SMS

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

##### Get delivery report
To get the delivery status of messages, use the API call below. The guid in the URL is replaced by the process ID of the message you want to look up.

```JSON
GET: https://rest.bosbec.io/2/messages/00000000-0000-0000-0000-000000000000

Headers:
"api-key":"00000000-0000-0000-0000-000000000000"
"Content-type":"application/json"
```

##### Response
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

###### Possible message statuses

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
