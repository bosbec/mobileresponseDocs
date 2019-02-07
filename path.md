# Path #

*A path holds a question and link to other paths in a form.*


After creating a form you connect one or more paths to that form.  For more information about forms have a look at the @{text:Form section;link:form}@  
The path contains questions, and questions can be of different types.  
  * **Information** is not a question that respondent can answer, but a place holder for bigger chunks of information
  * **FreeText** is used when you want a more open and qualitative.
  * **Scale** will render as a "slider", a control where the respondent may answer with a value between the min- and max- values defined. Will result in a numeric answer.
  * **Choice** can be used to render either radio-buttons or checkboxes. Depending on how many alternatives that the respondent may check.  
  * **Hidden** will not render as a question, but can be used to store some data that you need when a "FormAnsweredTrigger" has reacted to the posted "FormAnswer".
  * **FileUpload** will let the respondent upload a file, that can be references in the workflows after reacting.
