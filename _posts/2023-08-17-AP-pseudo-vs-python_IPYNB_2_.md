---
toc: True
comments: True
title: College Board Pseudo Code
description: The College Board testing language is Pseudo Code.  Pseudo mean kind-of language that we will compare to Python.
courses: {'compsci': {'week': 1}}
type: tangibles
---

## Learning College Board Pseudo Code
> College Board uses a kind-of programming language in its Multiple Choice exam. There are thousands of different programming languages have been created, and more are being created every year.  College Board has designed a pseudo code, a non operational programming language, to highlight concepts that it wants every student to learn.

College Board is trying to remain neutral and build Computer Science Principles off of any language, thus the Teacher is left to pick the language(s) according to application and curriculum. 

College Board Pseudo Code [Exam Reference Sheet](https://apcentral.collegeboard.org/media/pdf/ap-computer-science-principles-exam-reference-sheet.pdf)


| College Board | Python |
| ------------- |------- |
| a ← expression | a = expression |
| DISPLAY(expression) | print("expression") |
| INPUT() | hello = input("world") |
| RANDOM(a, b) | random.randint(a, b) |
| a = b | a == b |
| REPEAT n TIMES | for i in range(n) |
| REPEAT UNTIL(condition) | while (false) |
| aList ← value1, value2, value3 | aList = ["value1", "value2", "value3"] |
| list[1] | list[0] |



### Pseudo code IF Code Block
```
a ← 1
b ← 1

IF (a = b) {
   DISPLAY("A equals B")
}
```


```python
# Python code if block to match Pseudo Code
a = 1
b = 1
if (a == b):
    # Python uses indent to establish code block, Teacher use tab key
    print("A equals B")
```

## Hacks
> Key Learnings.  It is very important that you become fluent in " Vocabulary" and researching problems.

- Code a JavaScript cell, this must start with %%js%% in first line of cell. Match the IF condition example in this blog.

- Code a REPEAT n TIMES as described in comparison sheet in Pseudo code, Python, and JavaScript.  Be sure to comment your code.
    -  REPEAT 100 TIMES
    -  Sum all the numpers
    -  PRINT the result

- Reflect on our PSEUDO code and how it helped with your problem solving in these hacks.  

- Maked efinition for: code block, sequence, selections, iteration.  Consider a strategy to remember Pseudo Code, Python and JavaScript for these definitions.


