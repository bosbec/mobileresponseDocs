<p>This service notifies the account administrator when errors or warnings occur during background tasks.</p>

<p><b>Overview</b></p>

<ul>
<li>The administrator will receive notifications by email.
<li>A notification will contain details for the latest log item only; the log message and and what type it is. If there have been multiple errors in the last hour, it will simply state that multiple issues have been triggered, and refer you to the account log page for details.
<li>The service will check for pending errors and/or warnings every 60 minutes.
</ul>

<p><b>Error types</b></p>

<p>Examples of the types of errors you could get notified about:</p>

<ul>
<li>Billing errors. On paying orders, mainly, but also on general errors with the payment method.
<li>Errors on import or export of files.
<li>Errors on http request, when using the Remote Http Request job.
<li>Warnings when a long-lived REST-Api Token is about to expire.
</ul>

<p><b>Gotchas</b></p>

<ul>
<li>The account owner needs to have an email address set under Account Settings -> Administrator Settings i admin, in order to receive notifications.
<li>Any account errors and -warnings are listed in admin, under Administrator Tools -> Account Log, regardless of if you have this service or not (you need to have sufficient permissions to view that page, though). This service only handles <i>notifying</i> you about them via email.
</ul>
