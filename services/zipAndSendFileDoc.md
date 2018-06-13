This service provides a way to send zipped files to recipients, by mail.

**Overview**

The service does two things:

1) Whenever a file is uploaded to the Mobile Response file library (through admin, for example), the workflow will create a unit containing information about that file. These "file reference units" can then be found in the dynamic group "Uploaded files" on the account.

2) When the service is run, you will be prompted to select a file, a group to send to and some optional settings (see below). This will result in mails with attached zip files.

**Components**

Zip and send file
* When you click this, you are prompted to select, in order:
1) The file you want to zip and send. The files are listed by file name and creation time. They are represented by units in the group "Uploaded files" (see above).
2) The receiving group(s). All members of these groups will receive the zip by mail.
3) The zip filename. Optional. Is you leave it blank, it will be set to [original filename] + .zip.
4) The zip password. Optional. If you leave it blank, the zip will not be password protected.
5) Mail subject. Optional If you leave it blank, it will be set to "A zipped file from Mobile Response".
6) Mail body. Optional. If you leave it blank, it will be set to "Attached is a a zipped file from Mobile Response."

**Gotchas**

* The service only sends e-mails, currently. Make sure the recieving group members have e-mail addresses set on them.
* Since files are selected through "file reference units", which are created by this service, you cannot select files that you uploaded before installing the service.
