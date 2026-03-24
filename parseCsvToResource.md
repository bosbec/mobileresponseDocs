# Parse CSV to Resource

The Parse CSV to Resource job parses CSV-formatted text and creates a CsvResource in the workflow context. Use it when you receive rows of tabular data that need to be accessed by headers, rows, or columns in later workflow steps.

## Properties

The properties for configuring the parser are described below.

* **CSV source** (required)
	* Source containing the CSV text to parse, such as `{{incomingmessage.body}}` or a metadata value.
* **Parse first row as headers** (optional; default: true)
	* If enabled, the first row is treated as column headers.
* **Override allow fill on mismatch** (optional; default: true)
	* If enabled, shorter rows are padded to match the expected column count.
* **Override new line strict** (optional; default: true)
	* If enabled, newline matching is handled strictly when custom newline settings are used.
* **Override new line** (optional)
	* Custom row separator for non-standard CSV input.
* **Override escape character for quotes** (optional)
	* Custom escape character for quoted values.
* **Override delimiter** (optional)
	* Custom field delimiter such as `;`, `|`, or tab.
* **Destination resource name** (required)
	* Name of the CsvResource created in the workflow context.

## Referencing syntax

After parsing, the resulting CsvResource can be accessed through headers, rows, and helper functions.

* `{{csv1.headers}}` returns all headers.
* `{{csv1.headers[0]}}` returns the header at index `0`.
* `{{csv1.headers.count()}}` returns the number of headers.
* `{{csv1.rows}}` returns all rows.
* `{{csv1.rows[2]}}` returns the row at index `2`.
* `{{csv1.getcolumn(0)}}` returns the first column.
* `{{csv1.getcolumn(firstname)}}` returns the column named `firstname` when headers are enabled.

## Resulting resource

If parsing succeeds, the job creates a CsvResource that downstream jobs can inspect or iterate over.

* Headers can be read by position when the first row is treated as headers.
* Rows can be accessed directly or processed one by one together with [forEachResourceStart.md](forEachResourceStart.md).
* Column access is useful when later jobs need all values for one field.

## Best practices and tips

* Enable **Parse first row as headers** whenever the incoming CSV includes field names; it makes downstream expressions easier to understand.
* Use a custom delimiter only when the source data actually requires it.
* If the input may contain uneven rows, decide explicitly whether padding mismatched rows is safer than failing early.

## Related jobs

* For Each Resource Start
* CSV Pipeline
* Parse JSON to Resource

## References

* [Parse CSV to Resource](https://help.bosbec.com/knowledge-base/parse-csv-to-resource/)
	* Complete property guide and examples for accessing CSV resources.
* [For Each Resource](https://help.bosbec.com/knowledge-base/for-each-resource/)
	* Useful when iterating through parsed CSV rows one item at a time.
* [Working With Variables](https://help.bosbec.com/knowledge-base/working-with-variables/)
	* Reference for workflow expressions used in source and downstream access syntax.
