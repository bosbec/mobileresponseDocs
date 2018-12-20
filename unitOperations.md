# Unit operations #

*This job can perform operations related to units. Eg. get units, move within workflow context...*


There are a number of different operations to choose between and the basic concept is:  
1.  Find units from one or more sources; could be from account or from within the current execution of the workflow. Each additional find-operation will not modify what was found, but add to the set of found units.  
2. Filter the units that were found in the first step(s); each filter will continue working with a subset of units that was the result from previous filter-step(s).  
3. The store-operation can be used to either put the found+processed units in a destination such as the temporary group in the current execution or used to remove units eg. from the account.   



**Notes:  
Find-steps can be unsuccessful, and a setting to continue on error must be set if that is the desired behaviour.**

**How to:**
Add one or more find-operations to get units to process, optionally you may filter the given units before you let the job store or delete the resulting units from a given destination. 


**Find Operations**
  *  FindFromAccount: Search for whole "words" such as **John Doe**, and the search will look for **John** OR **Doe**. To search for exact phrase **"John Doe"** use quotation marks around the whole phrase you expect to search for. To search for John as first name, prefix the search with **md:** for metadata and **firstname=** the meta data key; **"md:firstname=John**. Words in quotation marks must all be present to be included in the found units. !Tip: Use a combination of find-operations and filter the result before store!
