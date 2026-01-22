# Notify UI #

*This job is used to send information to the user in the admin pages as bosbec.io*


This job will send a notification to the "Admin UI" found at bosbec.io.  
Depending on what is set in the "topic" property, you can either send information to just one administrator on your account or to all administrators.  
Note that the user must bed logged in at bosbec.io at send time, for the message to appear as a toast/notification in the upper right corner.  

To send a message to everyone on your account **topic** should be set to:
```{{currentuser.accountid}}.notification```  
And if you just want to send something to one administrator (for example the one running the workflow) set to:
<code>{{currentuser.administratorId}}.notification</code>  

Provide the custom data **"message"** to specify what information to display to the user.  
For example: 
Link: <a style= "color: #72c1ff" target="_blank" href="https://www.google.com/">https://www.google.com/</a>
Sent at: {{datetime(HH:mm:ss)}} 

Will provide 
Link: https://www.google.com/ Sent at: 15:22:11


**Notes:  
* Will not work unless you provide a correct **topic** and custom data with **message**.  
* Optional parameter for custom data is the **persistant** which should be set to **true** if you want the toast to stay until the user click the close button.  
* If the **persistant** is left out, the toast will automatically close after a few seconds.  

**How to:**
* Set topic and custom data message
