# The Get Meta Data #

*This job manipulates data on the WFC. It has a few more features than SetDataOperation in
DataOperations, but can basically do the same thing. This is the only job that can get app-user
properties.*

A source can be for example any metadata in the current execution context.  
For example I may have initiated the workflow with a metadata **"message"** that has the value **"Hello workflow!"**. And I can get the value "Hello workflow!" by setting the source to **metadata.message** in this case.

The GetMetadata-job can get information from an incoming form answer or from an incoming message. For example sources can be:  
  * **incomingmessage.sender** would get the sender-email of an incoming email message.
The GetMetadata job can also get the FormAnswer-respondent, that is the unit that answered the
form answer. Get this by using formanswer.answerer or formanswer.respondent  
If GetMetaData gets the FormAnswer-respondent it will be added to the WFC temporary group  

Finally GetMetaData can also get results from FormAnswers, by using the name of the question (ex. question1) we can write:
**formanswer.question.question1** and get the result into a WFC-resource.



**Notes:  
Need an incoming app message to get properties of incoming app message sender.  
Need an incoming form answer to work with the form-answers.  
If getting form-answer-respondent, the job will add it to WFC temporary group.  
For more details on WFC-resources see the section that describes it in more details**

**How to:**  
Set the source and destination.  
