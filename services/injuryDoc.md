Incident Service
============
## Injury Incident ##

A predefined process to facilitate action during an injury event.

**Overview**

* There are several steps that can be performed in this incident service:
  * Start incident
    * Start a new injury incident ticket by answering some start questions.
    * Can be initialized through app-in, by sending "injury" to the predefined base app user, which will give you back a form with the start questions.
    * You can select to use a reminder for this when using admin, by entering an interval in minutes. It will go to management, if a moderator has yet to be appointed. When using app-in, a reminder is automatically activated and set to 20 minutes.
  * Request check-in
    * Used for calling to a meeting, in most cases. Enter a message text. Select a receiver group. All recievers get a form where they can choose to opt-in or out, as well as leave a comment.
    * Currently not available to initialize via app-in.
    * You can select to use a reminder for this when using admin, by entering an interval in minutes. The reminder will go to all those who have not yet answered the check-in form.
    * You can only perform *one* check-in per ticket, currently. Any additional attempts will be intercepted.
  * Appoint a moderator
    * Task a person with following up the injury incident ticket through a form.
    * Can be initialized through app-in, by sending "appoint [ticket number]" to the predefined base app user, which will give you back     * You can select to use a reminder for this when using admin, by entering an interval in minutes. Both management and the appointed moderator will get a reminder. When using app-in, a reminder is automatically activated and set to 60 minutes.
    * It is not possible to *change* an appointed moderator. If you try, a notification about this will be sent to management.
a form.
  * Update incident
    * Send a message to a group, and set/update status and priority. It is currently the *only* way to change status and priority for this incident type, as it is not set initially, or by the appointed moderator.
    * Can be initialized through app-in, by sending "update [ticket number]" to the predefined base app user, which will give you back a form.
  * Start group chat
  * Close group chat
  * Close incident
    * Close the incident ticket. Management and the appointed moderator will get notified about this through a message. The message to management also contains a form you can use to add comments to the report post-closing.
    * Can be performed through app-in, by sending "close [ticket number]" to the predefined base app user.
  * Order report
    * Only available for closed tickets.
    * Can be performed through app-in, by sending "report [ticket number]" to the predefined base app user.
    * Sends the report back to the requester by mail (so e-mail address needs to be set on the unit, for this). The requester will also get an app-message saying that the report has been delivered.
* A log of all updates will be kept and can later be exported.
* Incidents can be either "Open" or "Closed". The two different states are shown separately on the left side of this view.

**About access**

* In order to perform any of the steps for this incident type, you generally need to be represented by a unit in the "Injury incident management" group.
* The only exception to this is "Start incident", which is allowed for everyone in "Injury incident management", "Injury incident moderators" and "Injury incident others", since everyone in the organization should be able to initialize an incident.
* Connection to a unit is currently done through phone number, so units need to have that set.
* When using the service steps here in admin, the default behaviour is that the phone number of the logged in administrator is used for identification. You can override this by entering another phone number manually when performing a service step.
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
