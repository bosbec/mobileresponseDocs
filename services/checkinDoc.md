Incident Service
============
## Checkin Incident ##

A predefined process to facilitate action during an event which requires check-in from a range of people in the organization.

**Overview**

* Incidents can be either "Open" or "Closed". The two different states are shown separately on the left side of this view.

**Components**

Request check-in
* Select receiving moderators (this also selects their groups). Write the message that will be sent to each moderator, and then write the message that will be sent to each individual in their groups.
* When run, this action initializes a new incident ticket and sends a confirmation about this to everyone in management by sms. Immediately after that, all moderators receive an sms message with the text you submitted plus a checkbox form listing all the people in their group. All the people in each moderators' group receives the second message you composed, as sms, along with a simple check-in-form.

Close incident
* Close the incident ticket. Management will get notified about this through sms.

Order report
* Only available for closed tickets.
* Compiles a report for the selected ticket and sends that to everyone in management by mail (so e-mail addresses needs to be set on the units there, if they are to recieve anything).

**About roles**

There are three roles in this setup: Management, moderators and others.

* "Managament" receives notifications about started and stopped tickets as well as feedback messages if errors occur. They also receive reports by mail when those are ordered. The administrator running the service needs to be represented by a unit in this group as well, in order for anything to be run at all.
* "Moderators" are responsible for one group of people each. They can be teachers, middle-management etc. If they are selected in an incident ticket, they will receive a form listing all those people. They can select or de-select people in this form themselves, or they can wait for people to check themselves in. In the latter case, it will be reflected on the moderators form as well. NOTE that this is not done in real time, though. You need to close and open the form again in order to refresh it. All of the moderator forms for a ticket can be viewed by the administrator, in the details for that ticket. Also NOTE that any explicit checking by the moderator on his/her form overrides that of the other person in question. If a person checks in and the moderator removes that check, it is only the moderator that can check him/her in again.
* "Others" are the people in the moderators' groups. They can be students or employees, for example - the people you want to be able to check in. If their moderator is chosen for a ticket, they will receive a check-in form. When answered, they will show up as checked in in the moderator form, which is also visible for the administrator.

**About access**

* In order to perform any of the steps for this incident type, the requester needs to be represented by a unit in the management group.
* Connection to a unit is currently done through phone number, so units need to have that set. Also make sure that there aren't several units on the account with the same phone number, as this will cause issues (especially for the management units).
* When using the service in admin - which is the only option for now - the requester is automatically set to the logged in administrator, so make sure that there is a unit in the management group that has the same phone number as the administrator. If not, no action will be allowed.
