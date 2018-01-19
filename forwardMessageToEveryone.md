# Forward message to everyone #

*Use this job to forward contents of incoming message to everyone in WFC groups and WFC temporary group.*

Can be used without setting message template, but will in that case set default values to all message types (that should be Normal prio and settings defined in Account+Admin).  
It is however possible to set a custom message template and configure more details about what to send. The job replaces the message body of the parts in the message template with the information to forward from the incoming message.  

It is possible to configure a “Predefined Header”, that would result in AppSenderId (for app if valid id) SMS sender name for SMS text messages and the from-address when sending email parts. It has no effect on Iot-messages.
ShouldIncludeHeaderInMessage has effect when incoming messasge is email, and means that the email subject will be included in the beginning of the forwarded text body.



**Notes:**

Need IncomingMessage.  
No need to set message template, but will then set default values for every message type.


**How to:**

In the most simple way, just connect the job somewhere after an incoming message trigger and make sure that there are members in WFC-groups or temporary group.