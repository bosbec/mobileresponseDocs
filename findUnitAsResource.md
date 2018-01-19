# Find Unit as Resource#

*This job will try to find units based on a search phrase. Experimental/Beta features are enabled and you may chose to disable. Result will be placed in a Unit-Resource.*

Will get the search phrase from workflow context.   
Will get page size (defaults to 5 if not set) and page index (defaults to first page) from workflow context.

When using the experimental mode search will try to match any data on the unit in your search.  
If non-experimental mode the search will if searchPhrase is an ID (a Guid) search for AccountId, AdministratorId or UnitId. To search for metadata type key=value (eg. firstname=TestUser would search for the metadata firstname where the value is TestUser).



**Notes:**

This job will probably merge the two modes in the future.

**How to:**

The value you want the job to search for goes in SearchPhrase.  
If you turn off the beta features, then you may search for exact metadata with key and value by setting the search phrase to key=value  

The search phrase, page -index, -size will accept values from wfc. 