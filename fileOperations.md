# File Operations

_Find, filter, operate on files_

## Properties

### Setup ftp endpoint
* **Host*** - Value or source of value (Use format metadata.key as source)
* **Port*** - Standard values are: FTP = 21, sFTP = 22, FTPS = 21 or 990
* **Directory** - Directory/Folder on ftp server to search for files (For ftp.bosbec.io use administratorId)
* **Username** - Login username
* **Password** - Login password
* **Setup name** - Set a name for this setup to use in later steps (i.e. find)
* **Use sftp** - Check this to use sFTP
* **Use ssh** - Check this to use SSH

### Find - From FTP
* **Endpoint setup source** - Name from setup ftp step

### Filter - File name regex filter
* **Regex pattern** - Regex pattern to filter files found on server

### Operate on file - Save information as resource
* **Resource name** - Name of file resource
