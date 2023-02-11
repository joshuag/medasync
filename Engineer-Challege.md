At Medasync, we recognize that your time is valuable, and we appreciate you investing that time with us. With that in mind, we've designed this exercise to be done in your spare time and it is untimed. Work on the project when you can and return it to us when you are finished.

We're looking for a project that represents how you would work on code in real life, including tests. Please choose a language that you're comfortable with so as to best demonstrate your programming ability.

Package your code as a tarball, zip, or a gitbundle and send it to us when you have finished.

# Problem Statement

Medasync processes streams of data and analyzes them to help our customers understand things they might be missing. You're going to write a something to process an input file that contains patients and actions. You can accept this file via stdin or as a filename given as an argument on the command line. 

Each line of the input will begin with a type marker, either "Patient" or "Action".

"Patient" will register a patient in the application, and will look like the following:

```
Patient John
```

"Action" will add an action to a patient, and will have an action type and action time. The list of available actions are "Intake", "Discharge", "Treatment"

"Intake" and "Discharge" have a patient and date and time as their only parameters. All times will be in Zulu time. For example:

```
Action Intake John 2023-01-06T09:45:00Z
Action Discharge John 2023-01-15T15:58:00Z
```

"Treatment" has a patient, date and time, and a four digit treatment code. For example:

```
Action Treatment John 2023-01-09T09:45:00Z F5GZ
```

We want to track patients, the duration of their stay in hours and minutes, and how many different treatments they received.

## Assumptions

A correct input will always have a patient before any actions taken on that patient, but may have patients and actions at any place in the file.

Every patient should have both an Intake and Discharge, but Intakes and Discharges can come in any order

Every patient should have at least one treatment.

Discharge should always be after Intake.

Example Input:

```
Patient John
Action Intake John 2023-01-06T09:45:00Z
Action Discharge John 2023-01-15T15:58:00Z
Action Treatment John 2023-01-09T11:35:00Z F5GZ
Patient Anne
Action Treatment John 2023-01-07T07:11:00Z GG34
Action Treatment John 2023-01-08T06:24:00Z BZ42
Action Intake Anne 2023-01-04T01:22:00Z
Action Treatment John 2023-01-10T16:36:00Z R0F1
Action Treatment Anne 2023-01-05T22:23:00Z R0F1
Action Discharge Anne 2023-01-09T04:56:00Z
Patient Polly
Action Intake Polly 2023-01-09T12:00:00Z
Action Treatment Polly 2023-01-09T13:00:00Z GG34
Action Treatment Polly 2023-01-09T13:00:00Z R0F1
Action Discharge Polly 2023-01-10T12:00:00Z
```

Expected Output:

```
Patient John stayed for 222.0 hours and 13.0 minutes and received 4 treatments
Patient Anne stayed for 123.0 hours and 34.0 minutes and received 1 treatments
Patient Polly stayed for 24.0 hours and 0.0 minutes and received 2 treatments
```

# Evaluation Criteria

There are a lot of different ways to tackle technical interviewing - and even more ways to solve problems. The problem above could even be solved in the space of a function if you really wanted. However, we're looking to understand how you model problems and how you thinking about testing and running your code, so it's important that you build with enough complexity to demonstrate your skill in those areas.

So to show your stuff, this needs a little bit more complexity than the problem calls for, but don't go nuts - you don't need to build an enormously complex piece of software.

We want to understand how you approach problems, so make sure to detail your thinking in your README. You can model data however you like, but make sure to explain why you chose what you did.

We'll be evaluating solutions on:

- How well they deal with varying input
- How internally consistent they are
- Their testing
- Use of the language in which they are written
- The design explanation in the README
