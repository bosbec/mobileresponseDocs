# Find Units by Id#

*This job will find units by id and put in temporary group or resource if a resource name is provided.*

Will find Ids (Guid) in the given source.

If the resource name is set then the result will end up as a unit-resource. Otherwise the result will end up in workflow context temporary group.

Using a standard delimiter or character like , or ; to separate Ids is preferred, but not a must.


**Notes:**

Resource name will not get value from wfc.

**How to:**

Make sure the job has ids to search with and set the ResourceName if you want the result to be a wfc Resource.
