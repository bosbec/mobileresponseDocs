Incident Service
============
## Injury Incident ##

A predefined process to facilitate action during an injury event.

**Overview**

* There are several steps that can be performed in this incident service:
  * Start incident
  * Request check-in (= call to a meeting, in most cases)
  * Appoint a moderator (= a person tasked with folloing up the injury incident ticket through a form. Ticket alias is set in this form)
  * Update incident (= send a message to a group, and set/update status and priority)
  * Start group chat
  * Close group chat
  * Close incident
  * Order report
* A log of all updates will be kept and can later be exported.
* Incidents can be either "Open" or "Closed". The two different states are shown separately on the left side of this view.

**Start**

* The process can be started through this user interface, or by messaging "injury" to a predefined app user, which will then send you back a form with the start questions.

**Access**

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
