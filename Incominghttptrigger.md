# Incoming Http Trigger
>*This trigger starts a workflow when an incoming http request matches the criteria specified with the trigger.  
>It provides a HTTP-resource in the workflow context.*  

The trigger need the **Token** property to be configured. The token is a regular Api-token for MobileResponse and you can create one in admin-ui https://admin.mobileresponse.io  
When you want to send a request and trigger a workflow via the IncomingHttpTrigger, you need to send a HTTP-request to https://in.mobileresponse.io/[YOUR-TOKEN-HERE]  
If the criteria matches the incoming request, then this trigger will put the information from the request into a named resource on workflow context.


**How to:**  

- Configure the method as one of the currently supported HTTP-methods: POST, GET or * to trigger on either one of them.
- Make sure you have a **Token** registered and use it to allow requests to in.mobileresponse.io/[YOUR-TOKEN-HERE]   
If you need to register a token head over to [https://admin.mobileresponse.io/#/rest-api](https://admin.mobileresponse.io/#/rest-api "Api-tokens")
- Configure the name of the HTTP-resource in the **IncomingResourceName**

**NOTES**

- **Sets a HTTP-resource in WorkflowContext**