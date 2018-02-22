Incident Service
============
## Checkin Incident ##

A predefined process to facilitate action during an event which requires check-in from a range of people in the organization.

**Overview**

* Incidents can be either "Open" or "Closed". The two different states are shown separately on the left side of this view.

**Components**

Request check-in
* Select receiving moderators (this also selects their groups). Write the message that will be sent to each moderator, and then write the message that will be sent to each individual in their groups.
* When run, this action initializes a new incident ticket and sends a confirmation about this to everyone in management. Immediately after that, all moderators receive a message with the text you submitted plus a checkbox form listing all the people in their group. All the people in each moderators' group receives the sencond message you composed, plus a form with a simple check-in-form.

Close incident
* Close the incident ticket. Management will get notified about this through sms.

Order report
* Only available for closed tickets.
* Compiles a report for the selected ticket and sends that to everyone in management by mail (so e-mail addresses needs to be set on the units there).

**About access**

* In order to perform any of the steps for this incident type, you generally need to be represented by a unit in the "Checkin incident management" group.
* Connection to a unit is currently done through phone number, so units need to have that set.
* When using the service steps here in admin, the default behaviour is that the phone number of the logged in administrator is used for identification. You can override this by entering another phone number manually when performing a service step. But it needs to be the phone number of a unit that is allowed to perform the service step.
* When using app-in, you need to have registered the phone number for the app user (and have a unit with that phone number in one of the allowed groups).
