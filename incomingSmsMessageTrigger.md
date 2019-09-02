# The incoming sms message trigger #

*Will start the workflow if an incoming sms matches the settings for this trigger.*

You can, by creating an IncomingSmsMessageTrigger, make a reservation for a SMS number that can be ordered from support@bosbec.com
For example, you may want to start your workflow when a sms is sent to **12345** (NOTE: this differs from how the email-trigger is configured; you **need** the number to be connected as an incoming number for the bosbec platform).  
To do this, you can get in touch with support@bosbec.com and order an incoming number. Or if you already have a number from before, then it is as simple as putting that phonenumber-number into the setting for **"Receiver"** in the properties for this trigger.  
If you don't care about what SMS senders may initiate your workflow, you should just leave the **"Sender"** property with a *****
Finally you may also chose to set a keyword as a criteria for when to react and start the workflow.   
A Keyword is the first word in the incoming SMS Body.


**Notes:  
The workflow must be inactive in order to save and update triggers.  
The trigger will not catch any incoming SMS messages while the workflow is inactive.  

**How to:**  
Set the **Receiver**, **Keyword** and **Sender** properties, connect the trigger to a job and activate the workflow.
