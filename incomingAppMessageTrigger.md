# The incoming app message trigger #

*Will start the workflow if an incoming app message matches the settings for this trigger.*

You can, by creating an IncomingAppMessageTrigger, make a reservation for an arbitrary app-message-receiver.   
The sender and receiver should be the Id of an App-User.  
The keyword is optional and can configure the trigger to react only when the first word in the app-message body matches the keyword. 
  


**Notes:  
The workflow must be inactive in order to save and update triggers.    
The trigger will not catch any incoming messages while the workflow is inactive.  
Provides an incoming message to the workflow context.**


**How to:**  
Set the Receiver, Keyword and Sender properties, connect the trigger to a job and activate the workflow.
