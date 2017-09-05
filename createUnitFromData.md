# Create units from data #

*This job can create units from data. Set the data in the “Resource to unit map” or make use of data in WFC resources. The result of the job can set the Incoming Unit.*

The Resource to unit map is the key to making the most of this job. Set a key which will map to a property on a Unit, and set the value direct or to some WFC resource’s-value.   
It is possible, but not necessary to prefix keywords with “unit” (ex. unit.phone). Things you can set (the keys):
  
**phone -> Will set the phone**  
**email -> Will set the Email**  
**metadata.test1 -> Will set the metadata with name “test1”**   
**tags -> A key that starts with tags will set a tag ex.**

- **tags1 -> Will set a tag**
- **tags2 -> Will set another tag**
 
Setting the result as incoming unit is optional via the setting with the same name.


**Notes:  
Can set IncomingUnit  
Will not update, only create new unit.**

**How to:**  
Example: Setting the “Resource to unit map” like the example on the right, will result in a Unit with
Phone = +46701234567  
Metadata.firstname = Myname  
Tags = [test1]     (if the WFC-metadata “current-tag” has the value “test1”)
