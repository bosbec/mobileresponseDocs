# Answer group member #

*This job is used to answer (send a message) to the workflow context resource “IncomingGroupMember” which is set in jobs like AllowSenderFromGroupRoute.*

The goal of the job is to create an answer/reply to the group-member that is found in the IncomingGroupMember resource on WFC.  
The job need the IncomingGroupMember to be available.



**Notes:  
Will abort if required IncomingGroupMember is not set.
Will use defaulting behavior for message.**

**How to:**
Connect to the message template (message to reply with).
