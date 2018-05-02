This service notifies the account administrator of errors that occur "behind the scenes" in Mobile Response.

**Overview**

* The administrator will receive notifications by email.
* The notifications contain no error details. It is only a summary of the type(s) of error(s) and how many, within a certain period of time.
* The first error will generate an immediate notification. After that, the service will "buffer" any errors that occur, for a period. At the end of that period, the administrator will receive another.
* If a buffer-period transpires _without_ any errors, all counters will reset. The first error _after_ that will again cause an immediate notification.
* The point of this buffer period is to not spam the administrator with hundreds of emails, if something happens that causes a lot of errors.
* The default buffer-period is 60 minutes, but this can be changed. See below.

**Components**

Reset counters
* 

Update wait period
* 

**Error types**

The service currently handles these specific errors:

* Billing errors. On paying orders, mainly, but also on general errors with the payment method.
* Errors on import or export of files.
* Errors on http request, when using the Remote Http Request job.

**Gotchas**

* The administrator needs to have an email address set in order to receive error notifications.
