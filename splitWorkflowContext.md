# Split workflow context #

*This job splits the current executing workflow context into different copies for each connected job.*

When this job executes it will see how many jobs are connected as next jobs and create a new copy of the current workflow context for each of the next job and then execute them.

This is very useful if you’ve loaded a number of units into the WFC-temporary group and would like to have some receive one message and another part of them receiving another message. Once you have a copy of the WFC you don’t have to worry about both processes removing each other’s units.


**Notes:   
Use this job to make sure that parallel job-executions don’t touch each other’s WFC-resources.**

**How to:**  
Just connect as many next jobs to this as you like, and the job will create a fresh copy of the current executing workflow context for each of the next jobs.