# Json pipeline #

The json pipeline job sets up a pipeline for managing json resources.

A pipeline job consists of a number of steps that are run in the provided order. In each step the resource and workflow can be referenced.

## Referencing

Throughout the pipeline a resource gets sent between each step. In each step-property this resource can be referenced using the following syntax: ```{{this.somekey}}```. It's also possible to fetch values from the workflow, so if you want to add some value from a metadata key you can du this with the following syntax: ```{{workflow.metadata.somekey}}```.

## Conditions

Between every step is a condition. A condition lets you set if the step should be run or not depending on the previous steps. More about conditions can be found here: [Conditions](resourcePipelineStepConditions.md)

## Steps

The **json pipeline** has the following steps available.

### Load resource step
Loads a resource from the workflow, so it can be altered with the other steps. The loaded resource needs to be a json resource.  
Often a pipeline starts by loading some existing resource.

#### Properties
  * ResourceName    - The name of the resource to load

### Save resource step
Saves the resource from the to the workflow so it can be used by other jobs.  
Often a pipeline ends with saving the resource to the workflow.

#### Properties
  * ResourceName    - The resource name to save to. Will overwrite if the resource already exists.

### Add key step
Adds a key to the json resource with the given value.

#### Properties:
  * Key     - The key to add to the json
  * Value   - The value to add to key
  
### Set key value step
Sets the value to the given key in the json resource, if the key doesn't exist, the value won't be set.

#### Properties:
  * Key     - The key to set in the json
  * Value   - The value to set to the key

### Remove key step
Removes a key from the json resource.

#### Properties:
  * Key     - The key to remove from the json

### Parse json step
Tries to parse the given json and will if successful replace the existing resource.

#### Properties:
  * JsonSource     - The key to remove from the json

### Transform json step
Transforms the json resource according to the given transformation.

#### Properties:
  * Transformation - The key to remove from the json

#### Examples
Below are some transformation examples:
```
Transform some existing json to another with other keys:
Current:                | Transformation:                | Result:
{                       | {                              | {
    "key1" : "value1",  |   "first" : "{{this.key1}}",   |   "first" : "value1",
    "key2" : "value2"   |   "second" : "{{this.key2}}",  |   "second" : "value2"
}                       | }                              | }

Transform using values from meta data in the workflow:
workflow.metadata.key = "SomeValue"

Current:                | Transformation:                           | Result:
{                       | {                                         | {
    "key1" : "value1",  |   "first" : "{{this.key1}}",              |   "first" : "value1",
    "key2" : "value2"   |   "second" : "{{workflow.metadata.key}}", |   "second" : "SomeValue"
}                       | }                                         | }

Transform using json in meta data in the workflow:
workflow.metadata.json = "{ \"key\" : \"value\" }"

Current:           | Transformation:                        | Result:
{                  | {                                      | {
    "key1" : "1",  |   "key1" : "{{this.key1}}",            |   "key1" : "value1",
    "key2" : "2"   |   "key2" : {{workflow.metadata.json}}, |   "key2" : {
}                  | }                                      |               "key" : "value"
                   |                                        |            }
                   |                                        | }

It's also possible to add lookups to keys and combine multiple lookups.
```