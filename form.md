# Forms #

*Forms represents a questionnaire that can be used to gather structured information.  
Forms must be connected to a message, and will then be rendered as a link inside the message.*

A form object in the workflow builder is just the container for the form.  
You need to add paths with the questions in order to create a template that will be used by the system to create unique questionnaires for each recipient.  
For more information about paths have a look at the @{text:Path section;link:path}@

When a recipient posts the result of a form that link will be locked and it won't be possible to post a new answer. Unless you set the **IsUpdatable** or the **AllowMultipleAnswers** to true.  
Allowing multiple answers will let the respondents use the same link over and over again, and each time a new FormAnswer will be posted.  
If you need the recipients to be able to change answers that already has been posted you can set **IsUpdatable** to true, and the respondent may now post the form again.  
*In this case the posted FormAnswer will change and you will not have all history of what answers had different values at any given time.*
