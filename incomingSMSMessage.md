### Incoming SMS message

SMS messages can trigger a workflow and the information about this triggering event is stored in the workflow context as the resource "incomingMessage". The `incomingMessage` consists of different parameters which hold information about the message. 

Syntax for accessing information in the incomingMessage:

* `incomingmessage.body` - Access the message body
* `incomingmessage.sender` - Access the sender (String-object)
* `incomingmessage.receivers` - Get all receivers in a comma separated list (incl. CC and BCC for email)
* `incomingmessage.receiver` - Get the main recipient.

### Example

Store the incoming message body in your metadata using Data Operations and "Set data", with the source `incomingmessage.body` and destination `metadata.message-text`. Use the set metadata to extract information from the message text, or forward the information to another recipient.
