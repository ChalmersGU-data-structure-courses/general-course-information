# Written examination

There is a [long list of topics](exam-topics.md) you should know for the exam.

## Allowed aids

You are allowed to bring ***one double sided A4 sheet of hand written notes*** to the exam.
It can contain anything you want, though a summary of the course material is a popular choice.

The sheet ***must be handed in with the exam***, but only for the purpose of determining if it adheres to the rules (and to make grading more entertaining, the sheets are sometimes quite the works of art).
You can get the sheet back afterwards if you need it for a re-exam or want to frame it and hang it on your wall.

## Grading

There are 6 basic questions and 3 advanced questions.
The basic questions are graded either correct or incorrect, while the advanced questions are awarded 0, 1 or 2 points each.

We use the following very complicated formula to calculate your final grade, where `basic` and `advanced` are integers ≤6:

```python
def grade(basic, advanced):
    if basic < 5:
        return None  # Sorry, try again next time
    else:
        return 3 + advanced // 2
```

Or, formulated differently:

- To pass the exam, you must pass 5 of the 6 basic questions.
- To get grade 4, you must also be awarded at least 2 points for the advanced questions.
- To get grade 5, you must also be awarded at least 4 points for the advanced questions.

(If your course uses the G/VG grading scale, then you need 3 advanced points to get a VG.)
