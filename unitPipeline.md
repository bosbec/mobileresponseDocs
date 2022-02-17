# Unit Pipeline #

*Operate on Units with different steps.*

## Properties

* **Alias** - Give your step a name 
* **Execution condition** - Add additional conditions to your step if an action fails/succeeds.

## Connections

This job can be connected to the following workflow elements:

* Jobs

## Requirements

* The workflow needs to be activated for the trigger to activate

## Other

Guide for merging duplicate units

The following steps will help you merge units with duplicate details on your account.

1. **Add a "Find Duplicate" step**
	1. Select what data you want to use to decide if a unit is a duplicate or not.
2. **Add a "Merge Units" step**
	1. To group by phone, use {{this.phone}} in "Group by expression".
3. **Decide if you want to keep the oldest or newest unit.**
4. **Add a Merge Action.**
	1. Currently only supports overwriting old unit data. This means that if the same metadata key is present on both units, the old data on the target unit will be replaced.
5. **Decide what to do with the source units**
	1. These are the units that will be merged into the target unit.
	2. Choose "Removed from account"
6. **Decide what to do with the target unit**
	1. Select "Saved to new resource" to add them to a resource in the workflow context. This will allow you to list all newly created units in the execution story.
7. **Add a "Save to account" step**
	1. This step will save the changes made to the units to the account.

Your duplicate units should now be merged!
