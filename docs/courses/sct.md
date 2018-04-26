## Submission Correctness Tests

Automated and meaningful feedback is an important aspect of the learning experience on DataCamp. When students make a mistake in a coding exercise, we want to tell them what they are doing wrong. The life and blood of the automated system that points out mistakes and guides students to the correct solution is the Submission Correctness Test, or SCT.

The SCT is a script of custom tests specified for every coding exercise. These custom tests have access to the code students submitted and the output and workspace they created with their code. For every taught language, there is an open-source library that provides a wide range of functions to verify these elements of a student submission. When the functions spot a mistake, they will automatically generate a meaningful feedback message.

The table below lists out all of the utlity packages used to write SCTs. If you're authoring R exercises you write your SCT in R. If you're building Python, SQL or Shell exercises, you write your SCT in Python. The documentation pages for each package list out all of its functions, with examples and best practices.

| Exercise Language | SCT language | GitHub | Build Status | Documentation |
|:------------------|:-------------|:-------|:------------:|:-------------:|
| R | R | [testwhat](https://github.com/datacamp/testwhat) | [![Build Status](https://travis-ci.org/datacamp/testwhat.svg?branch=master)](https://travis-ci.org/datacamp/testwhat) | [link](https://github.com/datacamp/testwhat/wiki) |
| Python | Python | [pythonwhat](https://github.com/datacamp/pythonwhat) | [![Build Status](https://travis-ci.org/datacamp/pythonwhat.svg?branch=master)](https://travis-ci.org/datacamp/pythonwhat) | [link](http://pythonwhat.readthedocs.io/en/latest/) |
| SQL | Python | [sqlwhat](https://github.com/datacamp/sqlwhat) | [![Build Status](https://travis-ci.org/datacamp/sqlwhat.svg?branch=master)](https://travis-ci.org/datacamp/sqlwhat) | [link](http://sqlwhat.readthedocs.io/en/latest/) |
| Shell | Python | [shellwhat](https://github.com/datacamp/shellwhat) | [![Build Status](https://travis-ci.org/datacamp/shellwhat.svg?branch=master)](https://travis-ci.org/datacamp/shellwhat) | [link](https://shellwhat.readthedocs.io) |

#### Example

To understand how SCTs are coded up and how they tie in with the student's experience, consider the source code for this R exercise about variable assignment:

    ## Create a variable

    ```yaml
    type: NormalExercise
    ```

    In this exercise, you'll assign your first variable.

    `@instructions`

    Create a variable `m`, equal to 5.

    `@hint`

    Use `<-` to assign a variable in R.

    `@sample_code`

    ```{r}
    # Create m

    ```

    `@solution`

    ```{r}
    # Create m
    m <- 5
    ```

    `@sct`

    ```{r}
    ex() %>% check_object("m") %>% check_equal()
    success_msg("Well done!")
    ```

- When students submit `a <- 4` when taking this exercise, a feedback box will appear in the learning interface with the message "Did you define the variable `m` without errors?". This message is generated by `check_object()`, that checks if `m` was defined in the workspace.
- If students fix the variable name but not the value assigned and submit `x <- 4`, their submission will fail again: "The contents of the variable `m` aren't correct.". This message was generated by `check_equal()`, that compares the value of `m` in the student workspace with the value of `m` in the solution workspace (a parallel environment in which the solution code was executed). Notice that there was no need to repeat the value `5` in the SCT; `testwhat` inferred it.
-  If students submit the right answer, `m <- 5`, all checks pass, the exercise is marked as complete, and the message "Well done!" is shown, as specified in `success_msg()`.