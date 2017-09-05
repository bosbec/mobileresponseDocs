# Calculate sms amount by message length #

*Will calculate how many SMS messages a text (from WFC-resources) would result in. As example, a text with Unicode characters will often result in more SMS-messages than a text with GSM-compatible characters. Job results in setting the calculated value/result in a WFC-resource (ex. metadata.sms-count-result).*


The job can be used together with substring- or regex-jobs to control that amount of SMS-message-parts that the workflow will send. Maybe you want to trim and just give a sample of the text in the SMS message, while sending the full text in the email-body.
Need a resource from WFC in the source and will abort if no such resource is found.
Result is the number of SMS messages that the text would result in.



**Notes:  
Will abort if the no resource is found in WFC based on the property (Source)  
Can only calculate number of SMS-messages, not other types.**

**How to:**
Set the Source to some WFC resource.  
Set Destination to where you want the result to end up.

