Incident Service
============
## Unspecified Incident ##

A predefined process to facilitate action during an unspecified event.

**Overview**

* On initialization, the user adds a alias, status, priority, group and a message. 
* The information is sent to the group in Bosbec application. 
* As this incident is unspecified there are several optional steps.
  * Start group chat
  * Create tasklist
  * Close group chat
  * Update incident
* In every step the user has the ability to send information to a selected group.
* A log of all incoming updates will be kept and can later be exported.
* Incidents can be either "Open" or "Closed". The two different states are shown separately on the left side of this view.

**Start**

* The process can be started through this user interface.

**Statuses**

Each incident has one of the below status properties;
  * Investigating
  * Identified
  * Monitoring
  * Resolved
  * Closed, Handed over

**Priority**

Each incident is assigned a priority which ranges in severity from Lowest (1) to Highest (5).

When creating a **tasklist** the user enter alternatives, reminder and which group the tasklist is sent to. The reminder send a message to the group in a given interval and reminds them to answer the tasklist in the application.
