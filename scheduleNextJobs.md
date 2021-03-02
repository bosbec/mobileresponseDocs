# Schedule next jobs  #

*This job can both execute jobs directly after being executed or start next jobs with a scheduling rule.*

## Properties

* **Scheduled date time source*** - Source of timestamp for execution of scheduled jobs
* **Scheduling id destination*** - Destination of schedule ID, if you do not require this variable, set a metadata (e.g `metadata.scheduleid`)
* **Scheduled jobs** - Use arrows to connect the scheduled jobs
* **Allow scheduling start time is in the past** - Allow execution of the "Scheduled date time source" is before current execution timestamp.
* **Date time parse format*** - Set the format of the "Scheduled date time source" (e.g `yyyy-MM-dd HH:mm:ssZ`)
* **Add scheduling rule** - Set a scheduling rule (see Scheduling trigger for more information)
* **Scheduling alias** - Alias for the scheduling item
* **Scheduling description** - Description for the scheduling item

## Connections

This job can be connected to the following workflow elements.

* Jobs

## Requirements

* Input for certain property-fields are required.

## Other
If you would like to schedule the execution of the next job you could use this job. Set the date time source to use a WFC value and schedule the execution of the next job.  
Allowing scheduled execution to start in the past can be a good idea if you need the next job to be executed even if the expected scheduling time has passed when executing this job.  
You can set custom date time parse formats (see parsing formats for Microsoft dotnet, or the section in this document on dates in MR).  
Remember to set the destination for scheduling id if you want to be able to stop the scheduled execution.  
In case of error and you cannot stop an execution, you can set the workflow or next job to inactive and it will not execute.  

Set the source and/or rule for execution (see section on scheduling for more information).  
Connect next job(s) from the “Scheduled jobs” if you want them to execute on schedule.  
Connect next job(s) from the regular “jobs” if you want to execute without schedule.  
