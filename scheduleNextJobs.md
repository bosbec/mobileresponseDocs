# Schedule next jobs  #

*This job can both execute jobs directly after being executed or start next jobs with a scheduling rule.*

If you would like to schedule the execution of the next job you could use this job. Set the date time source to use a WFC value and schedule the execution of the next job.  
Allowing scheduled execution to start in the past can be a good idea if you need the next job to be executed even if the expected scheduling time has passed when executing this job.  
You can set custom date time parse formats (see parsing formats for Microsoft dotnet, or the section in this document on dates in MR).  
Remember to set the destination for scheduling id if you want to be able to stop the scheduled execution.  
In case of error and you cannot stop an execution, you can set the workflow or next job to inactive and it will not execute.  




**Notes:   
Remember to set destination for scheduling id.**

**How to:**  
Set the source and/or rule for execution (see section on scheduling for more information).  
Connect next job(s) from the “Scheduled jobs” if you want them to execute on schedule.  
Connect next job(s) from the regular “jobs” if you want to execute without schedule.  
