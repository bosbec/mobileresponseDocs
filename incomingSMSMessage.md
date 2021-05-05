### Incoming SMS message

SMS or email messages can trigger a workflow and the information about this triggering event is stored in the workflow context as the resource "incomingMessage". The `incomingMessage` consists of different parameters which hold information about the message. Below is an example of an incoming SMS message and how you can access that information in the Workflow Builder:

_Example of an incoming SMS message_
```
"incomingMessage": {
  "sender": "+46700000001",
  "message": "Hello Bosbec!",
  "to": "+46700000002",
  "toList": [
    "+46700000002"
  ],
  "metaData": null
},
```

Syntax for accessing information in the incomingMessage:

* `incomingmessage.body` - Access the message body
* `incomingmessage.sender` - Access the sender (String-object)
* `incomingmessage.receivers` - Get all receivers in a comma separated list (incl. CC and BCC for email)
* `incomingmessage.receiver` - Get the main recipient.
* `incomingmessage.subject` - Get the email subject.
* `incomingmessage.image` - Access the image link (app message).
* `incomingmessage.longitude` Access longitud (app message)
* `incomingmessage.latitude` Access latitud (app message)

### Incoming unit/group member

Syntax for accessing information about an incoming group member (Only accessible for the job "AllowSendersFromGroup"):
* `incominggroupmember.metadata.[YOUR_METADATA]` - Get metadata from an incoming group member

Syntax for accessing information about an incoming unit:
* `incomingunit.phone` - Get the phone number of an incoming unit
* `incomingunit.phonenumber` - Get the phone number of an incoming unit
* `incomingunit.email` - Get the email of an incoming unit
* `incomingunit.emailaddress` - Get the email of an incoming unit
* `incomingunit.metadata.[YOUR_METADATA]` - Access metadata of an incoming unit

### Example

Store the incoming message body in your metadata using Data Operations and "Set data", with the source `incomingmessage.body` and destination `metadata.message-text`. Now you can extract information from the message text, or forward the information to another recipient.
