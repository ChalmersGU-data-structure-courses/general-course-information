# Written examination

Upcoming exam dates:
- 2025 June 5, 14–18
- 2025 August 21, 14–18
- 2025 end of October (date not decided yet)

## Topics

There is a [long list of topics](exam-topics.md) you should know for the exam.

## Allowed aids

You are allowed to bring ***one double sided A4 sheet of hand written notes*** to the exam.
It can contain anything you want, though a summary of the course material is a popular choice.

The sheet ***must be handed in with the exam***, but only for the purpose of determining if it adheres to the rules (and to make grading more entertaining, the sheets are sometimes quite the works of art).
You can get the sheet back afterwards if you need it for a re-exam or want to frame it and hang it on your wall.

## Format

There are 6 basic questions and 3 advanced questions.
* Each basic question is graded either correct or incorrect.
* Each advanced questions is awarded up to two points.

We do not give fractional points.

## Grading

Your grade (U/3/4/5) is calculated according to the following very complicated formula:

```python
def grade(
    basic,    # number of basic questions answered correctly
    advanced, # advanced points obtained
):
    if basic < 5:
        return 'U'  # sorry, try again next time
    else:
        return 3 + advanced // 2
```

Or, formulated differently:

- To pass the exam, you must pass 5 of the 6 basic questions.
- To get grade 4, you must also be awarded at least 2 points for the advanced questions.
- To get grade 5, you must also be awarded at least 4 points for the advanced questions.

(If your course uses the G/VG grading scale, then you need 3 advanced points to get a VG.)

## Past exams

We have a repository of [past exams](https://github.com/ChalmersGU-data-structure-courses/past-exams) that you can use to practice.
Note that the format of our exams has changed over the years.

Once the exam is over, solutions to the exam will be uploaded here.
