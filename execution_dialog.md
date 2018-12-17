# Execut the workflow #

*This window will help you execute a workflow.*

This window will let you configure the data to send in to your workflow by enter the key and value combination in the first tab "EXECUTE".  
Should you at any time want to know what data will be sent to the API, or if you for example want to export the current execution-configuration as cURL command, just click the "REQUEST PREVIEW" tab and you will have the resources you need. *Also, this is a great way to copy your request and import into POSTMAN or other similar tools*.   


### EXECUTE ###
If your trigger doesn't show up in the list, this means that you cannot execute that trigger. For example it may be the wrong type of trigger or that it has not yet been activated. To troubleshoot, try to reload your workflow builder and se if the issue still persists.  
Click the blue text "Suggest available keys" to let the workflow builder enter all keys that you have used somewhere in the workflow. *This is a good way to make sure you don't get typo in the meta-data names*.

### History ###
You get a short history of the request for workflow execution that you've issued with this session of you click your way to the history icon (right next to the x that closes this window).  
This information is here so that you may know what process id each request resulted in. It is also possible to preview what data was sent to the API. 


**Notes:
To execute a workflow you need an ExecutingWorkflowTrigger!**
