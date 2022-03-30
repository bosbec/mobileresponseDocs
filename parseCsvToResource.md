# Parse Csv to Resource

_This job will parse a csv-text in the "Csv source" either from a resource/metadata or just as csv-input.  
The result is a csv resource in the workflow context._

## Properties
* **Csv source*** - (input) A value with a csv eg. _ header1, header2\n row1, row2_ or a reference to a resource for example some data in an incoming message or metadata.
* **Destination resource name*** - (output) A name for the created csv resource.

## Other

The job will parse a CSV and if successful a CsvResource will be created in the workflow context.  
To access data after this job you can (_assuming name of resulting resource is csv1_):
* csv1.headers - returns headers/the header row
* csv1.headers[0] - will return the header from the first position (0)
* csv1.headers.count() - will return how many columns/headers
* csv.rows - will return the rows
* csv.rows[2] - will return the row from position 2
* csv.rows[3].distinct() - should return distinct values in row with position 3
* csv.getcolumn(xx) - where 'xx' is either the index/position for the header or a name of a given header, like 'firstname' in a csv: firstname, lastname \n .. 
* 
See documentation about resources and CsvResource for more in-depth understanding.
