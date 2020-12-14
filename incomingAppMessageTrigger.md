# Incoming app message trigger #

*Will start the workflow if an incoming app message matches the settings for this trigger.*

## Properties

### Reservation

* **Receiver*** - ID of an App-user (e.g 00000000-0000-0000-0000-000000000000)
* **Keyword** - This trigger will execute if the keyword is matched. * will not filter any incoming messages from teh sender (e.g `cancel`, or *)
* **Sender*** - Specify allowed senders. ID of an App-user. * will not filter any incoming senders. (e.g 00000000-0000-0000-0000-000000000000)

## Connections

This job can be connected to the following workflow elements.
* Jobs

## Requirements
* The workflow needs to be activated for the trigger to activate
* Any new reservations needs to be enabled. Contact our support team for further help.

## Other

The keyword is optional and can configure the trigger to react only when the first word in the app-message body matches the keyword. Will provide an `incomingMessage` to the workflow context.
