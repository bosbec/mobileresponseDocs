# Send Message To Groups

The Send Message To Groups job sends a message template to one or more groups. If no explicit groups are connected, it can fall back to groups and units already present in the workflow context.

## Properties

The properties for configuring the send are described below.

* **Message** (optional)
	* Connected message template to send.
* **Groups** (optional)
	* Explicit groups to receive the message.
* **Send only to active units** (optional; default: false)
	* If enabled, only active units in the target groups are used as recipients.
* **Use workflow context units** (optional; default: false)
	* Include units already present in the workflow context.
* **Override message text** (optional)
	* Replace the message template body with a custom value.
* **Override form template ID** (optional)
	* Override the form template used in the message.
* **Message resource** (optional)
	* Message resource to use instead of a directly connected message template.
* **Add files as metadata for app messages** (optional; default: false)
	* Attach workflow files as metadata for app-message sends.
* **Ignore send if no receivers** (optional; default: false)
	* Skip the send without raising an account error when no recipients are found.

## Referencing syntax

Use workflow expressions when overriding message content dynamically.

* Use **Override message text** for runtime-specific content.
* Use **Message resource** when the message template was loaded or created earlier in the workflow.

## Receiver selection

The job can gather recipients from several places.

* Use explicitly connected groups when the audience is known in advance.
* If no groups are connected, the job can default to workflow-context groups and the temporary group.
* Enable **Use workflow context units** when units already loaded into workflow context should also be considered.

For app messages, the job also applies default app-message settings such as sender and inbox values from merged settings when needed.

## Best practices and tips

* Connect groups explicitly when the intended audience should be obvious from the workflow design.
* Use **Ignore send if no receivers** only when an empty recipient set is expected and should not be treated as an error.
* Keep message selection clear: use either a connected message template or a message resource when possible, rather than mixing both patterns unnecessarily.

## Related jobs

* [messageTemplate.md](messageTemplate.md)
* [sendMessageToUnits.md](sendMessageToUnits.md)
* [findMessageTemplateAsResource.md](findMessageTemplateAsResource.md)

## References

* [Working With Variables](https://help.bosbec.com/knowledge-base/working-with-variables/)
	* Useful when overriding message text or selecting a message resource dynamically.
