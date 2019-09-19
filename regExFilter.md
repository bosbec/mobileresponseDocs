# The get users from incoming message #

*The regex-job is also available in DataOperations as separate operations for the different types of regex-filters.
What it does is simply execute a regex on a text and make use of options to decide on whether or not to insert, extract, replace… before, after…*

There are 4 types of filter operations:

  * Extract value - Will get a value based on the settings for that filter and put result in the destination.
  * Insert value – Will insert a value form dynamic source into the source depending on the settings for the filter and put result in destination.
  * Remove – Will remove text from the source and put result in the destination.
  * Replace – Will replace text in source with text from dynamic source and put result in destination.




**Notes:  
Most of the time it is easier to use the regex-operations in DataOperation-job instead of this.  
Dynamic source must be used when inserting or replacing.**


**How to:**  
Select what filter operation and configure it according to information above.
Set source/destination and maybe the dynamic source.

