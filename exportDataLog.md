# Export Data Log #

*Exports the data log(s) to workflow context resource with a custom set of rules for the export.*

The settings available can be found below.

```
{
    "MailSubject" : "Export Datalog",
    "MailTo" : "",
    "MailFrom" : "exports@bosbec.io",
    "Delimiter" : ";",
    "TextWrapper" : "\"",
    "PeriodStart" : "2019-12-11",
    "PeriodEnd" : "2020-01-10",
        "ExportResultDestination" : "metadata.result-destination",
        "FileIdDestination" : "metadata.result-fileid",
        "HeadersToInclude" : []
}
```

**Notes:
This job needs data in the data log in order to run**
