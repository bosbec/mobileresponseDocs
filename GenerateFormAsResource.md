# Generate form as resource #

*This job can 'generate' a form and put it as a form-resource in wf-context.*

The phrase generate a form, in this case, means to use a form-template and create a published version of the form, that can be used to send to many receivers without generating a unique form at send time, but instead during the workflow.

May be used with a standard setting (Generate settings) or for unit setting (Generate for unit settings).  

When using generate for unit-setting:

* If the unit source setting is 'temporarygroup' --> This job will generate a form for each unit in wfc temporary group. 
* If the unit source setting is 'incomingunit' --> This job will generate one form for the incoming unit.
* If the unit source setting is a match to a unit resource in wfc --> This job will generate a form for each unit in that unit resource
 

When using the standard setting, this job will generate a form without any receiver. That means that the answer will not know who answered this. It also means that this is a suitable alternative if you need to create an "open" form that can be used over and over again. Eg. as a registration-form.

In order to get the link to the generated form the message template should (instead of using the normal '[form]' keyword in the message body) use the keyword '[formlinkfor()]' where you may put the metadata-key within the parentheses so that when the system is sending a message to the user, the system can look for a generated-form-id in the given metadata. 


**Notes:**

Require the user to set a resource name in order to get the form resource with a name into the wfc.  


**How to:**

Connect to a form template, and this job can generate forms for the given units.  
