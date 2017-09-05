# Answer sender with form question #

*This job is used to answer the sender of the incoming message. And the answer to the sender of the incoming message is fetched from the form’s question with the specified name. Can only reply with SmsMessage.*


The job will test that there is a sender in the incoming message that and receive the answer/reply. Then make sure that the text message to add as SMS-text-body can be extracted from the form template. Will search for a question with the specified name (FormQuestionName) within the form’s paths (case insensitive) and use the question’s Text property for the message body.



**Notes:  
Will abort if the “sender”-unit doesn’t exist.  
Will abort if the “question” cannot be found in the form template.  
Can only reply with SMS-message.**

**How to:**
Connect to the form template.  
Set the form question name to a question-name from the form’s paths.

