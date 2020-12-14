# Account error trigger #

*Executes a workflow each time an account-error occurs*

## Properties

No parameters available

## Connections

This job can be connected to the following workflow elements:

* Jobs

## Requirements

* The workflow needs to be activated for the trigger to activate

## Other

When an account has processes such as scheduled activities or import processes the system will log warnings that are important for the user to know about. For example, the scheduler will send out a warning each time a scheduled activity is deleted, and the billing-system will send warnings if the account runs out of credits.  
This trigger (which is included in the free, AccountErrorNotifier-service that is installed automatically) will let you configure what to do with the warnings.  
For example, it can be important to know if an import process failes, and the message could be forwarded to the person responsible for providing the import file.
