# Extract Data

The Extract Data job pulls structured data out of events or workflow resources and moves it into workflow context in a form that later jobs can use. Use it when a trigger or process event contains groups, members, form answers, metadata, or units that should be promoted into workflow groups, temporary group, resources, or metadata.

## Properties

The properties for configuring the job are described below.

* **From** (required)
  * Extraction mode that decides what should be extracted and where the result should be placed.

## Referencing syntax

This job is mode-driven rather than expression-driven. You select one extraction mode and the job performs the corresponding action on the current workflow context.

## Extraction modes

The available extraction modes determine what kind of data is moved into workflow context.

* **GetGroupFromImportFinishedProcessEvent**
  * Extracts groups from an import-finished process event and adds them to workflow groups.
* **MoveWorkflowGroupMembersToTemporaryGroup**
  * Reads members from workflow groups, removes those groups from the current execution, and moves the members into the workflow context temporary group.
* **GetGroupFromDynamicGroupCreationFinishedEvent**
  * Extracts groups from a dynamic-group-creation-finished event and adds them to workflow groups.
* **UpdateIncomingUnitWithFormAnswers**
  * Updates the incoming unit with data from form answers.
* **UpdateMetaDataWithFormAnswers**
  * Writes form-answer data into workflow context metadata.
* **MoveTemporaryGroupToUnitResourceExtraction**
  * Moves units from the temporary group into a unit resource.
* **MoveAllUnitResourcesToTemporaryGroup**
  * Collects units from unit resources and moves them into the temporary group.
* **GetMetaDataFromImportFinishedProcessEvent**
  * Extracts metadata from an import-finished process event into workflow context.
* **MoveIncomingUnitToTemporaryGroup**
  * Adds the incoming unit to the temporary group.

## Execution behavior

The job performs exactly one extraction mode per execution.

* Some event-based extractions require the workflow to have been triggered by a compatible process trigger.
* Group-oriented extractions can place groups in workflow groups rather than the temporary group, depending on the mode.
* Temporary-group and resource-move modes are useful when later jobs expect data in a specific workflow-context location.

## Best practices and tips

* Choose the extraction mode based on where downstream jobs expect to find the data: workflow groups, temporary group, metadata, or a resource.
* Keep process-trigger-dependent modes near the relevant trigger flow so the required event data is still available and easy to understand.

## Related jobs

* Clear Workflow Context
* Filter Workflow Context
* Move Workflow Group Members To Temporary Group

## References

* [Working With Variables](https://help.bosbec.com/knowledge-base/working-with-variables/)
  * Useful background for understanding where extracted metadata and resources end up in workflow context.
