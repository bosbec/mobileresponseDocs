# Bosbec Platform Global Rules & Concepts (Technical Reference)

## 1. Workflow Architecture & Lifecycle
* **Workflow (WF):** The top-level container for logic, triggered by events and executed through a series of Jobs.
* **WorkflowContext (WFC):** The runtime state for a single execution. It acts as the "working memory" between Jobs.
* **Termination:** A workflow concludes when a Job has no subsequent IDs in its `jobs` array. The final state of the WFC remains accessible for debugging.

## 2. Data Addressing & Case Sensitivity
* **MetaData Keys:** Always **lowercase** (e.g., `{{metadata.firstname}}`).
* **MetaData Values:** Retain their original casing (e.g., "Gemini Google AI").
* **System MetaData:** Prefixed with `_system_` (e.g., `_system_workflowid`).
* **Structured Data (JSON/XML):** Maintains original casing from the source (e.g., `{{my_json.ID}}` if the source is `{"ID": 1}`).
* **Resource Indexing:** Resources can be `Single` (1) or `Multiple` (2). 
    * For `Multiple` resources, use zero-based indexing: `{{my_units[0].metadata.firstname}}`.

## 3. Inbound Traffic: Channels & Triggers
* **Channels (Inbound):** Act as gatekeepers and sorters. They provide **Rate Limiting** (delay or deny).
    * *HTTP:* Filtered by subdomain, URL path, or Verb (GET/POST).
    * *Messaging (SMS/Email):* Filtered by `Keyword` (first word), `Sender`, or `Receiver`.
* **Triggers:**
    * *Message-based:* Require an Inbound Channel. Often produce a default resource like `incoming_message`.
    * *ExecutingWorkflowTrigger (EWT):* Started via API or the `ExecuteWorkflow` job. Can inherit WFC data/resources.
    * *Event/Process Triggers:* React to internal system events (ET carries JSON payloads).
    * *FileTrigger:* Reacts to file system changes.

## 4. Persistent Storage: Units & Groups
* **Units:** The primary entity model. 
    * Contain **MetaData** for properties (e.g., `order_id`).
    * Contain **Endpoints** (Communication paths like `PhoneEndpoint` or `EmailEndpoint`). In documentation, these are often referred to as "Channels" on the Unit.
* **Groups:** Containers for Units. Groups have a `Name` and their own **MetaData**.
* **UnitResource:** A temporary WFC resource used to manipulate Units. Changes are not permanent until a "Store" operation is executed.

## 5. Execution Flow & Branching
* **Sequential Execution:** Jobs execute one after another. Avoid using multiple IDs in the `jobs: []` array to keep logic predictable.
* **Branching:** Use **Route Jobs** (e.g., `RouteFromMetaData`) for conditional logic.
* **Parallelism:** * `SplitWorkflowContext`: Creates independent copies of the WFC.
    * `ExecuteWorkflow`: Triggers a separate execution, avoiding complex parallel state issues.
* **Cleanup:** Use `ClearWorkflowContext` to wipe sensitive data before the workflow ends.

## 6. Roles & Debugging
* **Administrators:** Users building workflows.
* **Units:** Data entities (customers/orders) being processed.
* **Debug Mode:** Set via `SetDebugMode`. Allows an Administrator to pause execution and "Step" through jobs manually to inspect WFC state.
