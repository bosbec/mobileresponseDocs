# Route From MetaData   #

*This job evaluates the configured routes and chooses what jobs to continue executing. Each route is a new
evaluation and a way for the workflow to continue execution with the given series of jobs*

Use this job if you want the workflow to execute different jobs depending on given criteria.  
For example if you have two **metadata** with different date-times, lets call them **metadata.last-run** and **metadata.current-run**.   
Then we create two MetaDataRoutes within this job.  
The first is configured with 

[test-link](https://raw.githubusercontent.com/bosbec/mobileresponseDocs/master/dataOperations.md)


**Notes:   
The jobs connected from the "Jobs"-connector will not be executed.**

**How to:**  
Create as many metadata routes as you need and set up the evaluation for each of them.  
Connect one or more jobs to each evaluation and they will be executed after evaluation matches.  
Connect to the RouteDestinationOnNoMatch to catch every other case when none of the
evaluation matches.  
