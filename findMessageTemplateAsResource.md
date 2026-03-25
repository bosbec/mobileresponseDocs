# Find Message Template As Resource

The Find Message Template As Resource job finds message templates by name, ID, or metadata filter and stores the result as a workflow resource. Use it when later jobs should work with a message template loaded dynamically at runtime.

## Properties

The properties for configuring the job are described below.

* **Search phrase** (optional)
	* Name or ID of the message template to find.
* **Resource name** (required)
	* Name of the workflow resource that stores the result.
* **Page index** (optional)
	* Result page to return when many templates match.
* **Page size** (optional)
	* Number of templates to return per page.
* **Meta data filter** (optional)
	* Key-value filter used to narrow down templates by metadata.
* **Incoming message resource name** (optional)
	* Alias for the event resource when needed by the job configuration.

## Referencing syntax

Metadata filters are key-value pairs.

* Use metadata keys together with the values you want to match.
* A simple search can combine **Search phrase** with a metadata filter when both name and metadata should be considered.

## Behavior

The job finds matching templates and stores them in the named workflow resource.

* Search by **Search phrase** when the name or ID is known.
* Use **Meta data filter** when the workflow should select templates by attributes such as language, type, or message code.
* Use pagination when browsing or narrowing down larger template sets.

## Best practices and tips

* Give the result resource a descriptive name so later message jobs are easier to read.
* Use metadata filters when template selection should be stable even if names change.
* Keep pagination explicit if the workflow may return more than one matching template.
* Use metadata that reflects stable business dimensions such as language, message type, or channel rather than display names that are more likely to drift over time.
* Narrow the search as much as possible before downstream send steps so the workflow resolves one intended template instead of passing along an ambiguous result set.

## Related jobs

* Create Message Template As Resource
* Message templates
* Send Message To Groups

## References

* [Working With Variables](https://help.bosbec.com/knowledge-base/working-with-variables/)
	* Useful when filter values or resource names depend on workflow expressions.
