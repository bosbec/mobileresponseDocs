# Filter Workflow Context #

*The purpose of this job is to filter contents of the workflow context. There is only one implemented filter and that is the TemporaryGroupMetaDataFilter.*

Since Temporary Group Metadata filter is the only implementation for the workflow context filters in this job, this is an explanation of what that filter does.

The metadata key must be the actual key (may not include metadata-part “metadata.my-key”)

The CompareValueSource will try to find a value in WFC-resource and make the comparison with the resource instead of a fixes value (as in the case with CompareValue). Will default to comparing with the CompareValue if no resource value was found to compare with.

The comparison will first try to compare as number, if it isn’t numbers the job will try to compare as DateTime, and finally if it isn’t DateTime either the comparison will interpret values as string/text and make the comparison.

To understand how the comparison works check out the section on MetaData-comparison.

**Notes:
See Metadata-comparison section for more details.**

**How to:**

Select the filter (only TemporaryGroupMetadataFilter available).

Set the properties to compare the metadata.
