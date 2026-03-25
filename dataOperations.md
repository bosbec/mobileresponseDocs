# Data Operations

The Data Operations job performs a configurable list of ordered data transformations, mainly working with strings, within the workflow context. Use it to copy, calculate, format, encode, hash, and manipulate values.

Getting data from a key dynamically looks like this:

`{{metadata.key}}` or `{{resource.metadata.key}}`

Saving data to a key looks like this:

`metadata.key` or `resource.metadata.key`

An easy way to remember this could be "brackets replace the string".

## Properties

* **Operations** (required)
  * The ordered list of operations to execute. Each operation type has its own set of properties.
* **Execution condition** (optional)
  * Script that controls whether the job runs during workflow execution.
* **Jobs** (optional)
  * Jobs to execute after this job completes.

## Best practices and tips

* Keep operation lists focused on one transformation goal at a time so intermediate values and destinations remain easy to follow.
* Prefer extracting or filtering input values before running many transformations on them. Smaller, cleaner inputs reduce brittle expressions and unnecessary work.
* Use clear destination names for intermediate values when later jobs depend on them, especially in longer workflows.
* When the transformation target is structured JSON rather than individual values, compare this job with [jsonPipeline.md](jsonPipeline.md) before building a long sequence of string operations.

## Common transformation patterns

### Extract with regex before routing

Use **Extract value regex** to normalize values before `routeFromMetaData`.

Examples:

* Extract first subdomain from host: pattern `^[^.]+`
* Validate digits-only value: pattern `^\\d+$`
* Extract UUID from a path: pattern `[0-9a-fA-F]{8}-[0-9a-fA-F]{4}-[0-9a-fA-F]{4}-[0-9a-fA-F]{4}-[0-9a-fA-F]{12}`

### Retry counter increment

Use **Calculate data** to increment counters safely.

* **Source**: `{{metadata.retries}}+1`
* **Destination**: `metadata.retries`

Then gate retries in `routeFromMetaData` with a max-retry comparison.

### Prepare timestamp claims for JWT payloads

Use date/time and arithmetic operations to prepare `iat`/`exp` values before `createJwtSigning`.

Pattern:

1. Calculate current epoch value into metadata.
2. Add token lifetime offset (for example in seconds) for expiration.
3. Build final JSON claims in `jsonPipeline` and sign in `createJwtSigning`.

## Operations

Operations are executed in the sequence defined by the **Order** property within each operation. The **Order** property is available on every operation and is optional — operations without an explicit order value are executed in the order they are listed.

Changing the order can be done by dragging them into a different order, or by manipulating the JSON.

### Base 64

Encodes or decodes a value using Base64.

* **Source** (optional)
  * The value to encode or decode (e.g. `{{metadata.raw_value}}`).
* **Destination** (optional)
  * Where to store the result.
* **Decode** (optional)
  * Toggle to decode instead of encode.
* **Override encoding** (optional)
  * Override the default encoding.
* **Data type** (optional)
  * Options: **Text**, **Hex**

### Calculate data

Evaluates an arithmetic expression using workflow context values.

* **Source** (optional)
  * Expression to evaluate. Surround context values with `[]` (e.g. `[metadata.counter]+1`).
* **Destination** (optional)
  * Where to store the result.
* **Amount of decimals in result** (optional)
  * Number of decimal places in the result; defaults to 2.

### Calculate date time diff

Calculates the difference between two timestamps.

* **From date time** (optional)
  * Source of the first timestamp (e.g. `{{metadata.start_time}}`).
* **Until date time** (optional)
  * Source of the second timestamp (e.g. `{{metadata.end_time}}`).
* **Destination** (optional)
  * Where to store the result.
* **Output setting** (optional)
  * Output format. Options: `totaldays`, `totalhours`, `totalminutes`, `totalseconds`, `totalmilliseconds`
* **Default for missing values** (optional)
  * Whether to use a default value when one of the timestamps is missing.

### Calculate GPS distance

Calculates the distance in kilometers between two GPS coordinates.

* **Longitude 1** (optional)
  * The first longitude value (e.g. `{{metadata.longitude_1}}`).
* **Longitude 2** (optional)
  * The second longitude value (e.g. `{{metadata.longitude_2}}`).
* **Latitude 1** (optional)
  * The first latitude value (e.g. `{{metadata.latitude_1}}`).
* **Latitude 2** (optional)
  * The second latitude value (e.g. `{{metadata.latitude_2}}`).
* **Destination** (optional)
  * Where to store the result.

### Concat

Builds a string by combining workflow context values using a template.

This step is generally no longer needed with the new syntax, since strings can be combined directly in expressions like `"{{metadata.string_1}} {{metadata.string_2}}"`.

* **Source with format** (optional)
  * Template string using `{metadata.key}` placeholders (e.g. `{metadata.firstname} {metadata.lastname}`).
* **Destination** (optional)
  * Where to store the result.

### Concat group member data

Concatenates a formatted string for each member of a group, separated by a separator.

* **Data sources with format** (optional)
  * Template string with `{metadata.key}` placeholders, applied per group member.
* **Separator** (optional)
  * Text or character placed between each row.
* **Destination** (optional)
  * Where to store the result.
* **Use temporary group** (optional)
  * Use the workflow context temporary group.
* **Use context groups** (optional)
  * Use all groups in the workflow context.
* **Override replacements** (optional)
  * Character substitutions applied to group member data before concatenation.

### Concat unit resource data

Concatenates a formatted string from items in a workflow context unit resource.

* **Resource name** (optional)
  * Name of the unit resource in the workflow context.
* **Destination** (optional)
  * Where to store the result.
* **Data sources with format** (optional)
  * Template string with `{metadata.key}` placeholders, applied per unit.
* **Get data sources from metadata** (optional)
  * Alternative source for the data format template.
* **Separator** (optional)
  * Text or character placed between each row.
* **Override replacements** (optional)
  * Character substitutions applied before concatenation.

### Count group members

Counts the number of members in a group and stores the result.

* **Group identifier** (optional)
  * The group ID or source of the group identifier.
* **Destination** (optional)
  * Where to store the count.

### Create short link

Creates a shortened URL from a source value.

* **Source** (optional)
  * Source containing the full URL to shorten (e.g. `{{metadata.url}}`).
* **Destination** (optional)
  * Where to store the short link.

### Encode decode

Encodes or decodes a value using a specified encoding type.

* **Source** (optional)
  * Value or source to encode/decode (e.g. `{{metadata.raw_value}}`).
* **Destination** (optional)
  * Where to store the result.
* **Encode decode type** (optional)
  * Options: **Parse from string**, **To Base64**, **From Base64**, **To Base16 Hex**, **From Base16 Hex**, **From HTML encoding**, **To HTML encoding**, **From URL encoding**, **To URL encoding**
* **Parse encode decode type** (optional)
  * Encoding format to use (e.g. `utf-8`, `ascii`).
* **Non default encoding name** (optional)
  * Override the encoding name.

### Extract value regex

Extracts text from a source using a regex pattern.

* **Source text** (optional)
  * The text to extract from (e.g. `{{metadata.message_body}}`).
* **Regex pattern** (optional)
  * Pattern used to identify the value to extract.
* **Output source if no regex match** (optional)
  * Returns the original source if no match is found.
* **Options** (optional)
  * Options: **First match**, **Last match**, **Every match**
* **Result destination** (optional)
  * Where to store the result.

### Filter CSV string

Filters a comma-separated string against a comparison value.

* **Compare string** (optional)
  * The value to compare each CSV entry against.
* **Compare source** (optional)
  * Source of the comparison value (e.g. `{{metadata.filter_value}}`).
* **Result destination** (optional)
  * Where to store the filtered result.

### Get calculated log data

Aggregates data log values using sum, max, min, or average.

* **Log key** (optional)
  * The log key to perform the calculation on.
* **Data log calculation** (optional)
  * Options: **Sum**, **Max**, **Min**, **Average**
* **From time** (optional)
  * Start of the time range (e.g. `{{metadata.start_date}}`).
* **To time** (optional)
  * End of the time range (e.g. `{{metadata.end_date}}`).
* **Destination** (optional)
  * Where to store the result.

### Get country info

Looks up country metadata from a name or ISO code.

* **Identifier** (optional)
  * Country name or ISO code to look up (e.g. `{{metadata.country}}`).
* **Destination prefix** (optional)
  * Prefix for result keys (e.g. `country` produces `metadata.country_iso`, `metadata.country_name`, etc.).

### Get data log keys

Retrieves a list of data log keys and stores them in a resource.

* **Resource name for administrator keys** (optional)
  * Where to store the retrieved keys.
* **Page index** (optional)
  * Page index for paginated results.
* **Page size** (optional)
  * Number of keys per page.
* **Only for administrators** (optional)
  * Filter to administrator-scoped keys only.

### Get date from week number

Converts a week number and year to a date.

* **Week number source** (optional)
  * Source of the week number (e.g. `{{metadata.week_number}}`).
* **Year source** (optional)
  * Source of the year; defaults to the current year (e.g. `{{metadata.year}}`).
* **Day of week** (optional; default: Monday)
  * Options: **Sunday**, **Monday**, **Tuesday**, **Wednesday**, **Thursday**, **Friday**, **Saturday**
* **Destination** (optional)
  * Where to store the result.

### Get day of week

Returns the day of week for a given date.

* **Date source** (optional)
  * Source of the date; defaults to the execution date if empty (e.g. `{{metadata.date}}`).
* **Destination** (optional)
  * Where to store the result.

### Get last log data

Retrieves the most recent value stored for a data log key.

* **Log key** (optional)
  * The log key to read from.
* **Destination** (optional)
  * Where to store the result.

### Get relative date

Calculates a relative calendar date (e.g. the first Monday of March).

* **Ordinal position** (optional)
  * Options: **First**, **Second**, **Third**, **Fourth**, **Fifth**, **Last**
* **Day of week** (optional)
  * Options: **Sunday**, **Monday**, **Tuesday**, **Wednesday**, **Thursday**, **Friday**, **Saturday**
* **Day of week source** (optional)
  * Dynamic source for the day of week value (e.g. `{{metadata.day_of_week}}`).
* **Month** (optional)
  * Options: **January**, **February**, **March**, **May**, **June**, **July**, **August**, **September**, **October**, **November**, **December**
* **Year source** (optional; default: current year)
  * Source of the year value (e.g. `{{metadata.year}}`).
* **Destination** (optional)
  * Where to store the result.
* **Destination format** (optional; default: `yyyy-MM-dd HH:mm:ssZ`)
  * Format for the output date.

### Get week number

Returns the ISO week number for a given date.

* **Date source** (optional)
  * Source of the date (e.g. `{{metadata.date}}`).
* **Destination** (optional)
  * Where to store the result.

### Hash

Hashes a value using a standard or HMAC algorithm.

* **Source** (optional)
  * Value or source to hash (e.g. `{{metadata.password}}`).
* **Destination** (optional)
  * Where to store the result.
* **Source data type** (optional)
  * Options: **Text**, **Hex**
* **Hash method** (required)
  * The hashing configuration. Options:
  * **Standard hash** — standard algorithm (no key)
    * **Parse hash name** (optional) — set the hash algorithm from a text expression.
    * **Bosbec hash type** (optional) — Options: **Parse from string**, **MD5**, **SHA1**, **SHA256**, **SHA384**, **SHA512**
    * **Non default encoding name** (optional) — override the default encoding (ASCII).
    * **Non default output format** (optional; default: `X2`) — use `x2` for lowercase hex output.
  * **HMAC keybased algorithm** — keyed HMAC variant
    * **Key** (optional) — the secret key.
    * **Key is hex string** (optional) — treat the key as a hex-encoded value.
    * **Parse hash name** (optional) — set the hash algorithm from a text expression.
    * **Bosbec hash type** (optional) — Options: **Parse from string**, **MD5**, **SHA1**, **SHA256**, **SHA384**, **SHA512**
    * **Non default encoding name** (optional) — override the default encoding (ASCII).
    * **Non default output format** (optional; default: `X2`) — use `x2` for lowercase hex output.

### Insert regex

Inserts a value into text at a position matched by a regex pattern.

* **Source text** (optional)
  * The text to modify (e.g. `{{metadata.message_body}}`).
* **Value to insert** (optional)
  * The value to insert at the matched position (e.g. `{{metadata.prefix}}`).
* **Result destination** (optional)
  * Where to store the result.
* **Regex pattern** (optional)
  * Pattern used to find the insertion position.
* **Output source if no regex match** (optional)
  * Returns the original source if no match is found.
* **Options** (optional)
  * Options: **Before**, **After**, **First match**, **Last match**, **Every match**

### Log data

Writes a value to a data log.

* **Source** (optional)
  * The value to log (e.g. `{{metadata.val1}}`).
* **Log empty values** (optional)
  * Whether to store empty values.
* **Log key** (optional)
  * The log key to write to.
* **Log time** (optional)
  * Timestamp to associate with the log entry; defaults to execution time.
* **Data log ID destination** (optional)
  * Where to store the ID of the data log entry written.
* **Item metadata** (optional)
  * Additional key-value metadata to attach to the log entry.

### Modify date

Adds or subtracts time units from a timestamp.

* **Source** (optional)
  * Source of the timestamp to modify (e.g. `{{metadata.date_time}}`).
* **Destination** (optional)
  * Where to store the modified date.
* **Change year** (optional)
  * Years to add or subtract (e.g. `1` or `-1`).
* **Change month** (optional)
  * Months to add or subtract.
* **Change day** (optional)
  * Days to add or subtract.
* **Change hour** (optional)
  * Hours to add or subtract.
* **Change minute** (optional)
  * Minutes to add or subtract.
* **Change second** (optional)
  * Seconds to add or subtract.
* **Parse formats** (optional)
  * The expected input format (e.g. `yyyy-MM-ddTHH:mm:ssZ`). Common formats are tried automatically if omitted.
* **Destination format** (optional)
  * The desired output format (e.g. `yyyy-MM-ddTHH:mm:ssZ`).

### Pad

Pads a string to a specified total width with a given character.

* **Source** (optional)
  * Value or source of value (e.g. `{{metadata.order_id}}`).
* **Destination** (optional)
  * Where to store the result.
* **Pad type** (optional)
  * Options: **Pad left**, **Pad right**
* **Total width** (optional)
  * Total character width of the padded string.
* **Pad char** (optional)
  * The character to pad with.

### Parse epoch time

Converts a Unix timestamp (seconds or milliseconds) to a date-time string.

* **Source** (optional)
  * The epoch value to parse (e.g. `{{metadata.epoch_timestamp}}`).
* **Source is milliseconds** (optional)
  * Toggle if the input is in milliseconds rather than seconds.
* **Destination** (optional)
  * Where to store the parsed date-time.

### Parse phone

Validates and parses a phone number into its components.

* **Source** (optional)
  * Source of the phone number (e.g. `{{metadata.phonenumber}}`).
* **Country destination** (optional)
  * Where to store the country ISO code.
* **Is valid phone destination** (optional)
  * Where to store the boolean validation result (`true`/`false`).
* **Phone number destination** (optional)
  * Where to store the normalised phone number.

### Remove regex

Removes text matched by a regex pattern.

* **Source text** (optional)
  * The text to modify (e.g. `{{metadata.message_body}}`).
* **Regex pattern** (optional)
  * Pattern used to identify text to remove.
* **Regex pattern source** (optional)
  * Dynamic source for the regex pattern (e.g. `{{metadata.pattern}}`).
* **Output source if no regex match** (optional)
  * Returns the original source if no match is found.
* **Options** (optional)
  * Options: **First match**, **Last match**, **Every match**
* **Result destination** (optional)
  * Where to store the result.

### Remove resource

Removes a named resource from the workflow context.

* **Resource name** (optional)
  * Name of the resource to remove.

### Replace

Replaces a literal string within a value.

* **Source** (optional)
  * Value or template containing the text to search (e.g. `{{metadata.message_body}}`).
* **What to find** (optional)
  * The string to search for.
* **Replacement** (optional)
  * The value to replace the found string with.
* **Destination** (optional)
  * Where to store the result.

### Replace regex

Replaces text matched by a regex pattern.

* **Source text** (optional)
  * The text to modify (e.g. `{{metadata.message_body}}`).
* **Regex pattern** (optional)
  * Pattern used to identify text to replace.
* **Options** (optional)
  * Options: **First match**, **Last match**, **Every match**
* **Value to insert** (optional)
  * The replacement value.
* **Output source if no regex match** (optional)
  * Returns the original source if no match is found.
* **Result destination** (optional)
  * Where to store the result.

### Set data

Copies a value from a source to a destination in the workflow context.

* **Source** (optional)
  * Value or source of value (e.g. `{{metadata.phonenumber}}` or a literal value such as `+46700000001`).
* **Destination** (optional)
  * Where to store the value (e.g. `metadata.phonenumber` or `incomingUnit.metadata.phonenumber`).

### Split string

Splits a string on a delimiter and stores the parts as indexed metadata keys or a resource.

* **Source with format** (optional)
  * The string to split (e.g. `{{metadata.csv_row}}`).
* **Destination key** (optional)
  * Prefix for indexed result keys (e.g. `item` produces `item_0`, `item_1`, …, `item_n`). Cannot be combined with **Result as resource**.
* **Split on** (optional)
  * The delimiter to split on.
* **Result as resource** (optional)
  * Name of a resource to store all parts in. Cannot be combined with **Destination key**.

### Substring

Extracts a portion of a string by start index and maximum length.

* **Source** (optional)
  * Value or source of value to extract from (e.g. `{{metadata.message_body}}`).
* **Destination** (optional)
  * Where to store the result.
* **Start index source** (optional)
  * Dynamic source for the zero-based start index (e.g. `{{metadata.start_index}}`).
* **Substring max length source** (optional)
  * Dynamic source for the maximum number of characters to extract (e.g. `{{metadata.max_length}}`).
* **Start index** (optional)
  * The zero-based starting character position (static value).
* **Substring max length** (optional)
  * The maximum number of characters to extract (static value).
* **Substring by text element** (optional)
  * When enabled, emoji and other multi-char sequences count as a single character.

### Time based OTP code

Generates a time-based one-time password (TOTP).

* **Secret key** (optional)
  * The TOTP secret key (e.g. `{{metadata.otp_secret}}`).
* **User** (optional)
  * The user identifier associated with the TOTP (e.g. `{{metadata.username}}`).
* **Destination** (optional)
  * Where to store the generated code.

### UTF

Converts UTF-encoded text from hex notation to readable characters.

* **Source** (optional)
  * Source containing UTF-encoded data (e.g. `{{metadata.encoded_text}}`).
* **Destination** (optional)
  * Where to store the result.
* **Transformation** (optional)
  * The transformation type to apply. Options:
  * **From UTF-16 hex** — converts from UTF-16 hex notation (e.g. `\u0041`)
    * **Override default notation** (optional) — override the default `\u` prefix.
  * **From UTF-8 hex** — converts from UTF-8 hex notation (e.g. `\x41`)
    * **Override default notation** (optional) — override the default `\x` prefix.

## Execution paths

* **Jobs**
  * Jobs to execute after all operations have completed.

## Best practices and tips

* While it is often possible to do all data operations in one single job, it may be beneficial to break it up into multiple jobs for readability. For example, grouped by the data they modify. 
* **Set data** is a good way to copy or move a value between workflow context keys — use it before reaching for more complex operations.
* For date manipulation, prefer **Modify date** for relative changes (add/subtract) and **Set data** with statement syntax for static date assignments.
* The **Concat**, **Concat group member data**, and **Concat unit resource data** operations use a single-brace template format (`{metadata.key}`) in their format string — this is different from the `{{metadata.key}}` statement syntax used in other source fields.

## References

* [Working with Variables](https://help.bosbec.com/knowledge-base/working-with-variables/)
  * Syntax reference for reading (`{{metadata.key}}`) and writing (`metadata.key`) workflow context values.
* [Working with Strings](https://help.bosbec.com/knowledge-base/working-with-strings/)
  * Practical string patterns for Set data and Concat (for example `{{metadata.key1}} {{metadata.key2}}`), plus `defaultvalue(...)`, RegEx operations, Split string, Substring, and Encode Decode.
