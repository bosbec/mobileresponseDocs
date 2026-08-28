# Forms

Forms are questionnaires used to gather structured information.

In the current setup, forms are built in a form builder. A form can be connected to a message and rendered as a link inside that message.

## Core concept

A form is the container for the questionnaire. The form builder is where you add the questions, arrange them, and define how the respondent experience should behave.

Forms are typically used to collect answers from recipients and create form answers that can later be handled by workflows.

## Form builder structure

Use the form builder to add question blocks and structure the questionnaire as needed. Questions can be informational, interactive, hidden, or file-based depending on what you need to collect.

## Question types

The form builder supports several question types:

* Information
	* Displays text or content without collecting an answer.
	* Useful for instructions or larger explanatory sections.
* FreeText
	* Lets the respondent enter open text.
* Scale
	* Renders as a slider with a value between the configured minimum and maximum.
	* Produces a numeric answer.
* Choice
	* Renders as radio buttons or checkboxes depending on the number of alternatives and the expected selection behavior.
* Hidden
	* Does not render as a visible question.
	* Useful for storing data that should be available later when a FormAnsweredTrigger reacts to the response.
* FileUpload
	* Lets the respondent upload a file that can be referenced later in workflows.

## Answer behavior

When a recipient submits a form answer, the form is normally locked and cannot be used again.

You can change that behavior with the following options:

* IsUpdatable
	* Allows the respondent to submit the form again and update the existing answer.
* AllowMultipleAnswers
	* Allows the same link to be used multiple times, creating a new FormAnswer for each submission.

Use IsUpdatable when you want to replace the existing answer. Use AllowMultipleAnswers when you want to keep multiple submissions from the same link.

## Best practices

* Use clear section text through Information blocks when a form has multiple parts.
* Choose Hidden fields for data you need later in workflow processing.
* Use AllowMultipleAnswers only when repeat submissions are expected.
* Use IsUpdatable when respondents should be able to correct an existing answer.

## Related concepts

* Path
* Form Answer
* FormAnsweredTrigger

## References

* [Terminology](https://help.bosbec.com/knowledge-base/terminology/)
	* General platform terminology related to forms and workflows.
