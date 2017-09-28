# Find Groups #

*This job finds groups and add the found groups to workflow context groups.*

The search text source is used as search-phrase when finding groups. It may be a list of group-ids or a name of groups. Can use RegEx as search. Case-insensitive search.

Use the AllowedMaximumGroupsFound to control how many groups that may match the search. For example, specify that if should max find 1 group, and the finding resulted in 2 groups, then this job will NOT add groups to WFC groups and the result will be false.

**Notes:**

Can add groups to WFC groups.

Can use RegEx as search.

Case-insensitive search


**How to:**

Set the amount of groups that the job may find (or set to < 1 to allow any number of found groups)

Use WFC-resource or a specified text to search for groups in the SearchTextSource.
