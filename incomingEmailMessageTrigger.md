# Incoming email message trigger #

_Will start the workflow if an incoming email matches the settings for this trigger._

## Properties

### Reservation

* **Receiver*** - Adress of the receiver (e.g `example@qlnk.se`)
* **Keyword*** - This trigger will execute if the keyword is matched. `*` will not filter any incoming emails from the sender. (e.g `cancel`, or `*`)
* **Sender*** - Specify allowed sender domains. `*` will not filter any incoming senders. (e.g `firstname@bosbec.com`, `*@bosbec.com` or `*`) 

## Connections

This job can be connected to the following workflow elements.

* Jobs

## Requirements

* The workflow needs to be activated for the trigger to activate.
* Any new reservations needs to be enabled. Contact our support team for further help.

## Other
 A Keyword is the first word in the incoming email Subject+Body. So if the incoming email is without a subject then the keyword would be the first word in the email body. If there is a subject, then the trigger will try to match the first word in the subject.
