# Workflow Context #

*The workflow context is a container with everything that is related to the current execution of the given workflow.*

In workflow context we make use of the initial resources (such as Incoming Message, FormAnswer and Files), of object resources (such as JsonResource, UnitResource, and so on..) and also the MetaData.  
The MetaData is refered to with a key, like **metadata.my_metadata_key** and may be used to put some data in between jobs. That metadata is not available after the workflow has completed the execution, unless it is persisted to either the workflow itself or stored in any other resource.


**Notes:   
This information is not complete, have a look at [Help pages](https://help.bosbec.io).**
