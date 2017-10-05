# Stop scheduled next jobs #

*This job should be used together with ScheduleNextJobs, and the responsibility for this job is to abort a scheduled execution of next jobs.*

Use the schedule-id (the result from ScheduleNextJobs) to abort the scheduled execution of a next job.


**Notes:   
Cannot abort the execution of a next job if it already has started or executed.**

**How to:**  
Set the SchedulingIdSource to the metadata or WFC-resource that contains a scheduling-id to stop.