# Place custom billing order

_Will create an order in the billingsystem with the current billingtags and provided specifications._

## Properties

* Response message destination, a metadata variable that will be updated after the JobsAfter...Response.
* Order specification json (as sample from Requirements below)

## Connections

Do connect from the two specific 'JobsAfterFailResponse' and 'JobsAfterOkResponse' to continue after the order has been processed.

## Requirements

* Order specifications must be in json format, either single document or array of documents: 
<code>
{
    ""type"" : ""sms"",
    ""isocode"" : ""se"",
    ""amount"" : ""5.5""
}
</code>
or
<code>
[
  {
    ""type"" : ""sms"",
    ""isocode"" : ""se"",
    ""amount"" : ""5.5""
  }, ...
]
</code>

## Other

No further information available.
