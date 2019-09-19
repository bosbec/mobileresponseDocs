# The get users from incoming message #

*This job gets Units (users is a legacy terminology for unit-like concept) from the incoming message.*

This job has settings to define where to look for units in an incoming message (called the FindUserLocation).  
The job was originally designed to find units from incoming emails but will use the same FindUserLocation alternatives with similar locations in the different message types.  

  * None		- Will not find units
  * Receiver fiends	- “To/receiver” for app and sms messages, to + cc + bcc for emails
  * Sender	- From in every message type
  * Header	- Subject in emails, and none in the other types
  * Body		- The message body in all types
  * Attachments	- Not implemented




**Notes:  
Requires an incoming message.  
Will create units if no match is found.  
Will set the incoming unit if a single unit is the result of the create/find units.  
FindUserLocation alternative “Attachment” is not implemented.**


**How to:**  
Connect after an incoming message trigger (any kind of incoming message trigger).
Set the alternatives for where to look for units and whether or not to ignore setting a single found unit as incoming unit.
