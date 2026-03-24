# Answer Sender

The Answer Sender job replies to the originator of an incoming message or form answer. Use it when a workflow should answer the person who started the conversation without having to build the recipient selection manually.

## Properties

The properties for configuring the reply are described below.

* **Message** (optional)
	* Connected message template used for the reply.
* **Message resource** (optional)
	* Message resource to use instead of a directly connected message template.
* **Override answer sender source** (optional; default: incomingunit)
	* Source used to override which unit receives the reply.

## Referencing syntax

You can override the reply target using a workflow expression.

* Use `incomingunit` to rely on the default reply target.
* Use another resource or expression in **Override answer sender source** when the reply should go to a different unit selected earlier in the workflow.

## Sender selection

The job resolves the reply target in a defined order.

* First, it tries the sender from `IncomingMessage`.
* If no incoming message is available, it falls back to the sender of `FormAnswer`.
* If neither source exists, the job aborts.

The job also aborts if the sender unit cannot be resolved.

## Best practices and tips

* Use a connected message template when the reply content is static or centrally managed.
* Use **Message resource** when the workflow selects or builds the message dynamically.
* Override the sender source only when the workflow intentionally answers a different resolved unit than the default sender.

## Related jobs

* [answerFormQuestion.md](answerFormQuestion.md)
* [sendMessageToGroups.md](sendMessageToGroups.md)
* [messageTemplate.md](messageTemplate.md)

## References

* [Working With Variables](https://help.bosbec.com/knowledge-base/working-with-variables/)
	* Helpful when the reply target or message resource comes from workflow expressions.
