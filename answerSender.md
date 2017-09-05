# Answer sender #

*This job is used to answer the sender of the incoming message or “sender” of the form answer*


The goal of the job is to create an answer/reply to the sender of the incoming message or to the “sender” of the form answer.  
Prioritizes like this: If there is an IncomingMessage then this will be the sender to answer. If there is no IncomingMessage, but there is a FormAnswer, then answer the “sender” of that FormAnswer.  
Incoming message will be set if the execution was started with an IncomingMessageTrigger, and FormAnswer will be available if the FormAnsweredTrigger has started the execution.



**Notes:  
Will abort if required IncomingMessage or FormAnswer is not set.
Will abort if the “sender”-unit doesn’t exist.
Will use defaulting behavior for message..**

**How to:**
Connect to the message template (message to reply with).
