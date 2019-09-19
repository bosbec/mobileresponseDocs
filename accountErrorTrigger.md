# The account error trigger #

*Will start each time an account-error (which is more of a log that ranges from information-messages to explicit error messages).*

When an account has processes such as scheduled activities or import processes the system will log warnings that are important for the user to know about. For example, the scheduler will send out a warning each time a scheduled activity is deleted, and the billing-system will send warnings if the account runs out of credits.  
This trigger (which is included in the free, AccountErrorNotifier-service that is installed automatically) will let you configure what to do with the warnings.  
For example, it can be important to know if an import process failes, and the message could be forwarded to the person responsible for providing the import file.  


**Notes:  
The workflow must be inactive in order to save and update triggers.    
Trigger won’t react to account-errors while the workflow is inactive.**


**How to:**  
Specify any conditions for example set the path pattern and upload a file to the given path and this trigger should start a workflow execution.
