# Resource pipeline step conditions #

The step conditions are evaluated before each step is run.

## Conditions
The available conditions are the following.

### Default execution condition
Steps with this will always run.

### Previous step succeeded condition
Steps with this will only run if the step before was successful.

### Previous step failed condition
Steps with this will only run if the step before was unsuccessful.

### Expression condition
Steps with this will only run the expression matchs the expected value.

#### Properties
  * Expression      - An expression for looking up a value
  * ExpectedValue   - Some value that should be matched