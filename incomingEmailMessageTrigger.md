# The incoming email message trigger #

*Will start the workflow if an incoming email matches the settings for this trigger.*

You can, by creating an IncomingEmailMessageTrigger, make a reservation for an arbitrary email at the @qlnk.se domain.  
For exampl, you may want to start your workflow when an email is sent to **my_workflow_test_1@qlnk.se**.  
To do this it is as simple as putting that email address into the setting for **"Receiver"** in the properties for this trigger.  
If you don't care about what email senders may initiate your workflow, you should just leave the **"Sender"** property with a *****
Finally you may also chose to set a keyword as a criteria for when to react and start the workflow. A Keyword is the first word in the incoming email Subject+Body. So if the incoming email is without a subject then the keyword would be the first word in the email body. If there is a subject, then the trigger will try to match the first word in the subject. Setting the **Subject** to ***** will allow anything as subject and body in the incoming email.


**Notes:  
The workflow must be inactive in order to save and update triggers.  
The trigger will not catch any incoming emails while the workflow is inactive.  

**How to:**  
Set the **Receiver**, **Keyword** and **Sender** properties, connect the trigger to a job and activate the workflow.
