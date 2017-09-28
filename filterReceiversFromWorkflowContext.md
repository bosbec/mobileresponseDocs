# Filter Receivers From Workflow Context #

*This jobs filters receiver(s) in the WFC temporary group.*

You may choose to keep or remove the receivers that match the filter with the Keep filtered-property.
Explanation of what the filters does
* ShouldRemoveDeliveredAppMessageReceivers
  * An app-message is delivered when the app-users opens the MobileRespnose app (more precise it is when the app calls the What-is-new function in the app-API)
* ShouldRemoveMessageReceiversWithoutAppUser
  * Removes every unit that doesn’t have the AttachedAppUser set
* ShouldRemoveReceiversWhoCompletedFromInCurrentProcess
  * Removes the receivers that has submitted a form answer.
  * “in current process” means that the form must be generated in the same process as currently executing.
* ShouldRemoveReceiversWithMetadata
  * Will remove receivers that match the metadata defined in the metadata-key and -value properties.
* ShouldRemoveReceiversWhoMatchIncomingSender
  * Requires an incoming message.
  * Removes receivers that matches the incoming message’s sender
  
**Notes:
This job is very old and will most likely be replaced in the future. Signs of this is the inconsistent naming ShouldRemove… KeepFiltered.**

**How to:**
Just set the properties and remember to set KeepFiltered depending on whether or not you want to keep the receivers that match the filters.
