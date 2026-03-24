# Notify UI

The Notify UI job sends a toast notification to the Bosbec admin user interface. Use it when a workflow should surface status information, links, or short results directly to one administrator or to all administrators on the account.

## Properties

This documentation is based on the currently used configuration pattern for the job.

* **Topic** (required)
	* Destination channel that determines who should see the notification.
* **Custom data** (required)
	* Payload for the notification. The `message` field contains the text shown in the toast.

## Referencing syntax

The topic decides the audience.

* Use `{{currentuser.accountid}}.notification` to notify all administrators on the account.
* Use `{{currentuser.administratorId}}.notification` to notify one administrator.

The custom data payload should include `message`. You can also include `persistant` set to `true` if the toast should remain visible until dismissed.

## Notification behavior

The notification appears in the admin UI as a toast.

* The target user must be logged in to the Bosbec admin UI when the notification is sent.
* The message can contain dynamic workflow values, for example timestamps or links.
* If `persistant` is omitted, the toast closes automatically after a short time.

## Best practices and tips

* Keep UI notifications short and action-oriented.
* Use account-wide topics only for information relevant to multiple administrators.
* Prefer persistent notifications only when the message requires deliberate acknowledgement.
* Send UI notifications for operational visibility or manual follow-up, not as the only record of an important workflow outcome. Store key results in workflow data or logs when they matter later.
* Include just enough context in the message for the administrator to understand the event, such as a correlation ID, order ID, or a short status summary.

## Related jobs

* Add Workflow Starts Tag
* Set Debug Mode
* Execute Workflow

## References

* [Working With Variables](https://help.bosbec.com/knowledge-base/working-with-variables/)
	* Useful for building dynamic topic values and notification messages.
