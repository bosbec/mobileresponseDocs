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

**About roles**

There are three roles in this setup: Management, moderators and others.

Managament receives notifications about started and stopped tickets as well as feedback messages if errors occur. They also receive reports by mail when those are ordered.

Moderators are responsible for one group of people each. If they are selected in an incident ticket, they will receive a form listing all those people. They can select or de-select people in this form themselves, or they can wait for people to check themselves in, in which case it will be reflected on the moderators form as well. NOTE: This is not done in real time. You need to close and open the form again in order to refresh it.

**About access**

* In order to perform any of the steps for this incident type, the requester needs to be represented by a unit in the management group.
* Connection to a unit is currently done through phone number, so units need to have that set.
* When using the service in admin - which is the only option for now - the requester is automatically set to the logged in administrator, so make sure that there is a unit in the management group that has the same phone number as the administrator. If not, no action will be allowed.
