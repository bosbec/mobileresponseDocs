<p>This service is responsible for notifying the administrator about certain events that occur during backend tasks.</p>

<p><b>Overview</b></p>

<ul>
<li>The events you could choose to be notified about are those that appear under Administrator Tools -> Account Log in this admin web.
<li>There is a little cog icon in the bottom left corner of that page. It opens "Account Log Settings", where you can set which <b>types</b> and from which <b>level</b> you would like to recieve notifications.
<li>The <b>levels</b> are, in order of impact, from minor to major: Debug -> Info -> Warning -> Error.
<li>By default, you will be notified about events of <i>any</i> type, and from level "Warning" (meaning "Warning" and "Error").
<li>Also by default, you will receive notifications by email and by push, provided you have taken the steps to enable those (see Gotchas, below).
<li>The service will check for pending notifications every 60 minutes. This is to avoid spamming you with notifications.
<li>A notification will contain details for the <i>latest</i> log item only; the log message and and what type it is. If there have been multiple errors in the last hour, it will simply state that multiple issues have been triggered, including the specified latest one. Notification will always refer you to the account log page for details.
</ul>
<br>

<p><b>Notification types</b></p>

<p>Examples of the types of notifications you could get:</p>

<ul>
<li>Billing errors. On paying orders, mainly, but also if there are any general issues with the payment method, for example.
<li>Errors on import or export of files.
<li>Errors on http request, when using the Remote Http Request job in a workflow.
<li>Workflow execution errors, in general.
<li>Warnings when a long-lived Api Token is about to expire.
<li>Warnings when trying to send messages to no recipients (like an empty group).
</ul>
<br>

<p><b>Gotchas</b></p>

<ul>
<li>To receive notifications by <b>email</b>, you need to have an email address set under Account Settings -> Administrator Settings in this admin web.
<li>To receive notifications by <b>push</b>, you need to use the Bocbec Admin app. As soon as you have logged in to that, you should be able to receive push notifications.
<li>Any Account Log events are listed here in admin, under Administrator Tools -> Account Log, regardless of if you have this service or not (you need to have sufficient permissions to view that page, though). This service only handles <i>notifying</i> you about some of them.
<li>The "Account Log Settings" governing notifications, have <i>no effect</i> if you don't have this Account Notifier service installed.
</ul>
