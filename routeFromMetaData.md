# Route From MetaData   #

*This job evaluates the configured routes and chooses what jobs to continue executing. Each route is a new
evaluation and a way for the workflow to continue execution with the given series of jobs*

Use this job if you want the workflow to execute different jobs depending on given criteria.  
For example if you have two **metadata** with different date-times, lets call them **metadata.last-ok** and **metadata.last-test**.   
Then we create a MetaDataRoute within this job.   
We want one set of jobs to be executed when **metadata.last-test** is later than **metadata.last-ok**.  
The settings for that MetaDataRoute should be *Meta data source* should be set to **metadata.last-test** and *Compare value source* should be set to **metadata.last-ok**. And to make the comparison test that the first metadata (**metadata.last-test**) is later than the **metadata.last-ok** we will set the *Compare operator* to **>** meaning that the source should be bigger than the value we compare it to.    
If we want something else to happen when this comparison doesn't match we connect another set of jobs to the **Route destination on no match** that is available when hovering over the job.  


When the job has two routes that are not exclusive, meaning that two or more routes can be true/matched at the same time.  
Example: route1 compares a number that may be between 1-5 while route2 compare if a number is exactly 3. Both will be true and match.  
What happens is that the workflow will behave in a way that execute first from route1 and then route2.  
If this is something that you want to do, then you will probably want to split the workflow, using the checkbox to split on each matching route.  

For more information about what operators are available and how to use them, please read the section on @{text:Comparing MetaData;link:metaDataComparison}@   
For more information about metadata and how to use it during workflow execution, please refer to the section on @{text:Workflow Context;link:workflowContext}@   

**Notes:   
The jobs connected from the "Jobs"-connector will not be executed.   
Multiple matching routes at the same time may cause unexpected behaviour**

**How to:**  
Create as many metadata routes as you need and set up the evaluation for each of them.  
Connect one or more jobs to each evaluation and they will be executed after evaluation matches.  
Connect to the RouteDestinationOnNoMatch to catch every other case when none of the
evaluation matches.  
