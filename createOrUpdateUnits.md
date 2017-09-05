# Create or update units #

*The purpose of this job is to create a custom formula to “import” units from a text.*

This job will create or update units based on what is provided in a WFC resource.  
It will find a text in a WFC resource based on what is set as “Search source”.  
It will try to parse each row in that source as a Unit, and make use of the customizable “Mapping Formula”.  
Can set the IncomingUnit resource.  
“Find distinct for …” makes sure that the job won’t find more than one unit with the same email/phone.  
Reserved words in the Mapping formula are (reserved word -> will map to unit property):  

**phone, phonenumber -> Unit.PhoneNumber**  
**email, emailaddress -> Unit.EmailAddress**  
**tags -> will map to one (1) tag, use “tags” for each column to map as tag.**
  
Anything else will be mapped as metadata with the same name as the header.  
It is possible to use multiple delimiters, but make sure the one in the mapping-formula is present in the list of MappingDelimiters.  
Places the resulting units in the temporary group.  
MappingDelimiters will default to: `;, ` 
MappingFormula will default to:` phone;email;firstname;lastname  `
	


**Notes:  
CreateOnly and UpdateOnly are to be implemented and not yet supported!  
Can set the IncomingUnit resource.  
Make sure to use the same delimiters in mapping formula as set as delimiters.  
Each character in MappingDelimiters will be interpreted as a delimiter.  
Places the resulting units in WFC temporary group.**

**How to:**  
Only thing that you must set is the search source, the other optional settings should be explained in the text above.