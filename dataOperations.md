# Data Operations

_Operations, calculations and manipulation on data in workflow context, units, groups, and more_

## Properties

### Calculate data
* **Source*** - Value or source of value. Surround any source of value with `[]` (e.g [metadata.counter]+1)
* **Destination*** - Destination of stored value, could be a resource on the account, or in WFC (e.g `metadata.counter`, or `incomingUnit.metadata.counter`)
* **Order** - Order in which the jobs are executed. Lowest value equals highest priority (e.g 0)

### Concat
* **Source with format*** - String of values (e.g `{incomingUnit.metadata.firstname} {incomingUnit.metadata.lastname}`)
* **Destination*** - Destination of stored concated string, could be a resource on the account, or in WFC (e.g `metadata.full_name`) 
* **Order** - Order in which the jobs are executed. Lowest value equals highest priority (e.g 0)

### Concat group member data
* **Data sources with format*** - String of values (e.g `{incomingUnit.metadata.firstname} {incomingUnit.metadata.lastname}`)
* **Seperator*** - Text or a single character that separates each “row” (each group-member)
* **Destination*** - Destination of stored concated string, could be a resource on the account, or in WFC (e.g `metadata.full_name`) 
* **Use temporary group** - Toggle if you want to use the wfc temporary group
* **Use context groups** - Toggle if you want to user the wfc groups.
* **Override replacement** - 
* **Order** - Order in which the jobs are executed. Lowest value equals highest priority (e.g 0)

### Concat unit resource data
* **Data sources with format*** - String of values (e.g `{incomingUnit.metadata.firstname} {incomingUnit.metadata.lastname}`)
* **Seperator*** - Text or a single character that separates each “row” (each group-member)
* **Destination*** - Destination of stored concated string, could be a resource on the account, or in WFC (e.g `metadata.full_name`) 
* **Resource name** - Name of resource in wfc.
* **Override replacement** - 
* **Order** - Order in which the jobs are executed. Lowest value equals highest priority (e.g 0)

### Count group members
* **Group identifier*** - Group ID
* **Destination*** - Destination of stored value, could be a resource on the account, or in WFC (e.g `metadata.full_name`) 
* **Order** - Order in which the jobs are executed. Lowest value equals highest priority (e.g 0)

### Extract value regex
* **Source text*** - Value or source of value.
* **Result destination*** - Destination of extracted value, could be a resource on the account, or in WFC (e.g `metadata.full_name`) 
* **Regex pattern*** - Regex pattern used to extract content from source text.
* **Matches*** - Before, After, First match, Last match or Every match.
* **Order** - Order in which the jobs are executed. Lowest value equals highest priority (e.g 0)

### Filter csv string
* **Compare string*** - 
* **Compare source*** - 
* **Result destination*** - Destination of filtered value, could be a resource on the account, or in WFC (e.g `metadata.full_name`) 
* **Order** - Order in which the jobs are executed. Lowest value equals highest priority (e.g 0)

### Get calculated log data
* **Destination*** - Destination of calculated value, could be a resource on the account, or in WFC (e.g `metadata.full_name`)
* **Sum/Max/Min/Average*** - 
* **From time*** - 
* **To time*** - 
* **Log key*** - 
* **Order** - Order in which the jobs are executed. Lowest value equals highest priority (e.g 0)

### Get data log keys
* **Resource name for adminsitrator keys*** - 
* **Page index** -

### Get last log data
* **Destination*** - Destination of log data value, could be a resource on the account, or in WFC (e.g `metadata.full_name`)
* **Log key*** - Log key
* **Order** - Order in which the jobs are executed. Lowest value equals highest priority (e.g 0)

### Insert regex
* **Source text*** - Value or source of value.
* **Value to insert*** - Value to insert with the regex pattern
* **Result destination*** - Destination of new text, could be a resource on the account, or in WFC (e.g `metadata.full_name`)
* **Regex pattern*** Regex pattern used to insert content in source text
* **Matches*** - Before, After, First match, Last match or Every match
* **Order** - Order in which the jobs are executed. Lowest value equals highest priority (e.g 0)

### Log data
* **Source*** - 
* **Log empty values** - 
* **Log key*** - 
* **Log time*** - 
* **Data log id destination*** - 
* **Item metadata** - 

### Modify date
* **Source*** - Source of timestamp  
* **Destination*** - Destination of new date, could be a resources on the account or in WFC (e.g `metadata.new_date`)
* **Change year** - New value
* **Change month** - New value
* **Change day** - New value
* **Change hour** - New value
* **Change minute** - New value
* **Change second** - New value
* **Parse formats** -New value
* **Destination format** -  
* **Order** - Order in which the jobs are executed. Lowest value equals highest priority (e.g 0)

### Parse phone
* **Source*** - Source of phone number
* **Country destination*** - Destination of country value
* **Is valid phone destination*** - Destination of boolean value if phone is valid
* **Phone number destination*** - Destination of phone number
* **Order*** - Order in which the jobs are executed. Lowest value equals highest priority (e.g 0)

### Remove regex
* **Source text*** - Value or source of value
* **Result destination*** - Destination of new text, could be a resource on the account, or in WFC (e.g metadata.full_name)
* **Regex pattern** - Regex pattern used to remove content in source text
* **Regex pattern source** - Source of regex pattern used to remove content in source text
* **Matches*** - Before, After, First match, Last match or Every match
* **Order** - Order in which the jobs are executed. Lowest value equals highest priority (e.g 0)

### Remove resource
* **Resource name*** - Name of resource to remove from WFC
* **Order** - Order in which the jobs are executed. Lowest value equals highest priority (e.g 0)

### Replace regex
* **Source text*** - Value or source of value
* **Result destination*** - Destination of new text, could be a resource on the account, or in WFC (e.g metadata.full_name)
* **Regex pattern** - Regex pattern used to replace content in source text
* **Matches*** - Before, After, First match, Last match or Every match
* **Order** - Order in which the jobs are executed. Lowest value equals highest priority (e.g 0)

### Set data
* **Source*** - Value or source of value (e.g `metadata.phonenumber`, or `+46700000001`)
* **Destination*** - Destination of stored value, could be a resource on the account, or in WFC (e.g `metadata.phonenumber`, or `incomingUnit.metadata.phonenumber`)
* **Order** - Order in which the jobs are executed. Lowest value equals highest priority (e.g 0) 

### Split string
* **Source with format** - 
* **Destination key** - 
* **Split on** - 
* **Result as resource** - 
* **Order** - Order in which the jobs are executed. Lowest value equals highest priority (e.g 0) 

### Substring
* **Source*** - Value or source of value
* **Destination*** - Destination of substring, could be a resource on the account, or in the WFC (e.g `metadata.substring`)
* **Start index** - Numerical value of the character in source which starts the string (e.g 0)
* **Substring max length** - Numerical value of the max length of the substring
* **Order** - Order in which the jobs are executed. Lowest value equals highest priority (e.g 0) 

### Time based otp code
* **Secret key** - 
* **User** - 
* **Destination** - 
* **Order** - Order in which the jobs are executed. Lowest value equals highest priority (e.g 0) 

## Connections

This job can be connected to the following workflow elements.

* Jobs
* Triggers
* Routes

## Requirements

* Fields marked with `*` require input.
* You need to ad the prefix `metadata.` to access data in your WFC

## Other

No further information available.
