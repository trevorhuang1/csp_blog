---

---

---
toc: true
comments: true
layout: post
title: Week 3
description: Math QUiz
type: hacks
courses: { compsci: {week: 3} }
---


```python
from random import randint
def Operation(A, B, op):
    ans = 0
    if (op == 0): ans = A+B
    if (op == 1): ans = A-B
    if (op == 2): ans = A*B
    if (op == 3): ans = A//B
    if (op == 4): ans = A**B
    if (op == 5): ans = A%B
    if (op == 6): ans = A&B
    if (op == 7): ans = A|B
    if (op == 8): ans = A^B
    return ans
rsp = None
numOfQuestions = 0
# How many questions in the test?
while True:
    rsp = input("Ready for a test? How many questions do you want to answer?\n> ")
    if (rsp.isnumeric and int(rsp) > 0):
        numOfQuestions = int(rsp)
        rsp = None
        break
key = {0: "+",
        1: "-",
        2: "*",
        3: "//",
        4: "^",
        5: "%",
        6: "AND",
        7: "OR",
        8: "XOR",
        9: "?"}
# Loop through questions
numCorrect = 0
for i in range(1, numOfQuestions+1):
    op = 0
    A = randint(1, 10)
    B = randint(1, 10)
    if (1 <= i <= 5):
        op = randint(0, 3)
    elif (6 <= i <= 10):
        op = randint(0, 5)
    elif (11 <= i <= 15):
        op = randint(0, 8)
    else:
        op = 9
    rsp = input(f"Question {i}. What is {A} {key[op]} {B}?\n> ")
    if ((not rsp.strip("-").isnumeric()) or op == 9):
        print("Wrong! Not valid")
        continue
    ans = Operation(A, B, op)
    if (ans != int(rsp)):
        print(f"Wrong! The correct answer is {ans}.")
    else:
        print(f"Correct! The correct answer is {ans}")
        numCorrect += 1
print(f"You got {numCorrect}/{numOfQuestions} or %{numCorrect/numOfQuestions * 100}")
```


    ---------------------------------------------------------------------------

    ValueError                                Traceback (most recent call last)

    /tmp/ipykernel_2904/3279772151.py in <module>
         17 while True:
         18     rsp = input("Ready for a test? How many questions do you want to answer?\n> ")
    ---> 19     if (rsp.isnumeric and int(rsp) > 0):
         20         numOfQuestions = int(rsp)
         21         rsp = None


    ValueError: invalid literal for int() with base 10: ''

