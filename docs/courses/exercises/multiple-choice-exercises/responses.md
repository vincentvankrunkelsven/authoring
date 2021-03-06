# Writing `MultipleChoiceExercise` and `PureMultipleChoiceExercise` Responses

This page provides guidance on writing good multiple choice responses.

## Examples

From [How does the shell compare to a graphical user interface?](https://campus.datacamp.com/courses/introduction-to-shell-for-data-science/manipulating-files-and-directories?ex=1) in "Introduction to Shell for Data Science". Each wrong answer reflects a common misunderstanding.

> What is the relationship between the graphical file explorer that most people use and the command-line shell?
> 
> Possible answers
> - The file explorer lets you view and edit files, while the shell lets you run programs.
> - The file explorer is built on top of the shell.
> - The shell is part of the operating system, while the file explorer is separate.
> - They are both interfaces for issuing commands to the operating system.

From [Review inner join using on](https://campus.datacamp.com/courses/joining-data-in-postgresql/introduction-to-joins?ex=6) in "Joining Data in PostgreSQL". The question is more easily answered if the student runs the code block. Each wrong answer corresponds to a potential misunderstanding about inner joins.

> Why does the following code result in an error?
> 
>     SELECT c.name AS country, l.name AS language
>     FROM countries AS c
>     INNER JOIN languages AS l;
> 
> Possible answers
> - The languages table has more rows than the countries table.
> - There are multiple languages spoken in many countries.
> - INNER JOIN requires a specification of the key field (or fields) in each table.
> - Join queries may not be followed by a semi-colon.


## FAQs

### How many responses should I have?

Four or five.

## Good ideas

### Provide distractors that give insight

The distractors ("wrong answers") should ideally provide insight as to what went wrong. That is, they should be the answer a student expects if they have made a common error or misunderstanding.

### Provide feedback messages that give insight

The feedback message that a student receives should explain why the answer is wrong. Don't just say "Try again", or "Incorrect".

### Make the student do something

Rather than just asking them a question to test their knowledge, you can make the student actively do something in order to answer the question. For example, You can make them write some code to explore a dataset, or make them look at and interpret a plot or diagram.

### Test principles

Similarly, rather than just testing the students' knowledge of facts, it can be good to test the students' understanding of principles.

## Common problems and their solutions

### Having an "all of the above" response

If the students identify two correct statements, they will often be able to guess that "all of the above" is the correct response. Don't use this.

### Having a "none of the above" response

You can't test that the student know the correct response. Don't use this.

### Trivially wrong answers

Having silly or obviously wrong answers simply makes the exercise easier, and reduces the opportunity for learning.

### Different response lengths

Having some answers that contain a lot more or a lot less text than other answers can draw students attention to those answers. Try to keep each answer roughly the same length.
