# Parse Json to Resource

_This job will parse a json in the "Json source" either from a resource/metadata or just as json-input.  
The result is a json resource in the workflow context._

## Properties
* **Json source*** - (input) A value with a json eg. _{"sample" : "json"}_ or a reference to a resource (could for example be a UnitResource) or metadata in the workflow context _metadata.my_json_
* **Destination resource name*** - (output) A name for the created json resource.

## Other

The job will parse a JSON and if successful a JsonResource will be created in the workflow context.  
To use and access data in the json use dot-notation eg. from a simple json _{"sample" : "value"}_ in a resource called _my_json_ you could access the value with **my_json.sample**.  
See documentation about resources and JsonResource for more in-depth understanding.
