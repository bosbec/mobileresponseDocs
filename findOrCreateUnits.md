# Find or Create Units #

*This job will first try to find units. If it cannot find units, it will create a unit matching what was searched for.*

Will first try to get the value from WFC-resource in SearchSource. The value found in SearchSource will be used to try to find units.

Depending on the property PreventCreatingUnits this job can be configured to create new unit if finding existing units isn’t successful.

If units are found, then the FindDistinctForX. comes into play. With these properties set it is possible to make sure that only one unit with each phone number/email is returned as the find-result.

If SingleFoundUnitAsIncomingUnit is set to true AND the find-part of this job resulted in a single unit found, then this job will set the IncomingUnit resource.

**Notes:**

Can set Incoming Unit

**How to:**

Set FindDistinctForX properties if you need to find only one unit.
