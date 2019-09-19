# The incoming iot message trigger #

*Will start the workflow if a matching MQTT-message is received.*

The trigger will let you configure the incoming topic for the Bosbec MQTT endpoint. Make sure you’ve got a device registered in order to know what topic to use for communication to and from that device.  
Set the receiver to your topic, eg. 1ab45cd8-12efg67h-12i4/my-topic and the trigger can listen to messages on that topic.  
Combine this with a keyword or a sender to be more precis in what to react to.


**Notes:  
The workflow must be inactive in order to save and update triggers.    
The trigger will not catch any incoming messages while the workflow is inactive.  
This trigger need device(s) configured.   
Provides an incoming message to the workflow context.**


**How to:**  
Set the Reciever to the topic that you expect messages to be published under. Optionally, set the Sender and Keyword.
