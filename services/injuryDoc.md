Incident Service
============
## Injury Incident ##

A predefined process to facilitate action during an injury event.

**Overview**

* Incidents can be either "Open" or "Closed". The two different states are shown separately on the left side of this view.

**Components**

Send instructions
* Use this to send instructions (to one group or several) about how to report a ticket via app-in.
* The instruction message will be sent from the predefined base app user, thereby granting all recipients the correct conversation to message in to.

Report ticket
* Initialize an injury incident by answering some start questions. Note that starting an injury ticket through the icon here in admin is non-standard, and is mostly available for testing purposes.
* The expected way to initialize an injury incident is through app-in, by sending "injury" to the predefined base app user, which will give you back a form with the start questions.
* Submitting the form will start a new incident ticket and will notify management, who are then expected to appoint a moderator to follow up the incident. This notification contains the answers from the start form.
* You - the requester - will also get a confirmation message back, to let you know that the ticket was successfully started.
* You can select to use a reminder for this when using admin, by entering an interval in minutes. It will be sent to management, if a moderator has yet to be appointed. When using app-in, a reminder is automatically activated and set to 20 minutes. 

Request check-in
* Used for calling to a meeting, in most cases. Enter a message text. Select a receiver group. All recievers get a form where they can choose to opt-in or out, as well as leave a comment.
* Currently not available to initialize via app-in.
* You can select to use a reminder for this when using admin, by entering an interval in minutes. The reminder will be sent to all those who have received, but not yet answered the check-in form.
* You can only perform *one* check-in per ticket, currently. Any additional attempts will be intercepted.

Appoint a moderator
* Task a moderator with following up the injury incident ticket. The moderator gets a message with information and a follow-up-form.
* Can also be initialized through app-in, by replying "appoint" in the ticket conversation, which will give you back a form.
* You can select to use a reminder for this when using admin, by entering an interval in minutes. Both management and the appointed moderator will get a reminders while the follow-up-form is incomplete. When using app-in, a reminder is automatically activated and set to 60 minutes.
* It is not possible to *change* an appointed moderator. If you try, a notification about this will be sent to management.
* When the moderator has submitted answers for all the questions in the follow-up-form, management gets a message about it, so that they can check it and close the ticket.

Update incident
* Send a message to a group, and set/update status and priority. It is currently the *only* way to change status and priority for this incident type, as it is not set initially, or by the appointed moderator.
* Can also be initialized through app-in, by replying "update" in the ticket conversation, which will give you back a form.
* When using admin for this, you can freely select one or more group(s) that will recieve the update. You can also skip sending to any groups, if you only want to update status and/or priority or leave a comment in the report. When using app-in, management will get the message.

Start group chat
* Select a group for which to start a group chat, and enter a start message for it, that will be sent to everyone. A new app user will be created for each ticket + group, so that the group chat is handled in a separate, named conversation in the app. All participants will get an message that the chat has been opened.
* You can't start several separate chats with the same group, for the same ticket.
* Currently not available to perform via app-in.

Close group chat
* Select an open chat to close. A message will go out to all participants that the chat has been closed. If anyone tries to send further messages there, they will again get a message that says the chat is closed.
* You can close a chat for a group, and later re-open it, if you want.
* Currently not available to perform via app-in.

Close incident
* Close the incident ticket. Management and the appointed moderator will get notified about this through a message. The message to management also contains a form you can use to add comments to the report post-closing.
* Can also be performed through app-in, by replying "close" in the ticket conversation.

Order report
* Only available for closed tickets.
* Can also be performed through app-in, by replying "report" in the ticket conversation.
* Sends the report back to the requester by mail (so e-mail address needs to be set on the unit, for this). The requester will also get an app-message saying that the report has been delivered.

**About access**

* In order to perform any of the steps for this incident type, you generally need to be represented by a unit in the "Injury incident management" group.
* The only exception to this is "Start incident", which is allowed for everyone in "Injury incident management", "Injury incident moderators" and "Injury incident others", since everyone in the organization should be able to initialize an incident.
* Connection to a unit is currently done through phone number, so units need to have that set.
* When using the service steps here in admin, the default behaviour is that the phone number of the logged in administrator is used for identification. You can override this by entering another phone number manually when performing a service step. But it needs to be the phone number of a unit that is allowed to perform the service step.
* When using app-in, you need to have registered the phone number for the app user (and have a unit with that phone number in one of the allowed groups).

**Statuses**

Each incident has one of the below status properties;
  * Investigating
  * Identified
  * Monitoring
  * Resolved
  * Handed over

**Priority**

Each incident is assigned a priority (through "Update") which ranges in severity from Lowest (1) to Highest (5).
