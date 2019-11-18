<p>This service notifies the account administrator of errors that occur "behind the scenes" in Bosbec.</p>

<p><b>Overview</b></p>

<ul>
<li>The administrator will receive notifications by email.
<li>The notifications contain no error details. It is only a summary of the type(s) of error(s) and how many, within a certain period of time.
<li>The first error will generate an immediate notification. After that, the service will "buffer" any errors that occur, for a period. At the end of that period, the administrator will receive another notification.
<li>If a buffer-period transpires _without_ any errors, all counters will reset. The first error _after_ that will again cause an immediate notification.
<li>The point of the buffer period is to not spam the administrator with hundreds of emails, if something happens that causes a lot of errors.
<li>The default buffer-period is 60 minutes, but this can be changed. See below.
</ul>

<p><b>Components</b></p>

<p>Update wait period</p>
<ul>
<li>This changes the buffer period, explained above. Submit number of minutes.
</ul>

<p>Reset counters</p>
<ul>
<li>Shouldn't have to be used by a regular user. It's more of a development aid. Some actions, like inactivating the workflow while it is in a buffer wait period, will cause the counters to not reset properly, causing no notifications to get sent. The counters are automatically reset at midnight every day, but you can use this function to reset them manually.
</ul>

<p><b>Error types</b></p>

<p>The service currently handles these specific errors:</p>

<ul>
<li>Billing errors. On paying orders, mainly, but also on general errors with the payment method.
<li>Errors on import or export of files.
<li>Errors on http request, when using the Remote Http Request job.
</ul>

<p><b>Gotchas</b></p>

<ul>
<li>The administrator needs to have an email address set in order to receive error notifications.
<li>Any account errors are listed in admin, under Tools -> Account errors, regardless of if you have this service or not (you need to have sufficient permissions to see them, though). The service only handles notifying you about them.
</ul>
