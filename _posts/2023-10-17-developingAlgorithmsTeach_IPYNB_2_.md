---
toc: True
comments: False
layout: post
title: CB 3.9. 3.15 Developing Algoritms
description: College Board Big Idea 3, Idea 9, Developing Algorithms
courses: {'compsci': {'week': 9}}
type: hacks
---

Lets start off with the basics. 
What is an algorithm? 

- An algorithm is a procedure or formula used for solving a problem. It has a sequence of events, inputs, and outputs. 


What are algorithms used for? 

- Algorithms are used in many different aspect of life. For example a form of routine is an algorithm as it is a series of specified events. 


Why are algorithms important? 

- It solves a problem in a way that it can be applied to any similar problem. It allows the computer to solve the problem on its own w/o any form of human interference. 


```python
# Psuedo Code 1
DISPLAY ("What is the temperature outside in F?")
temp <- INPUT()
IF (temp >= 90)
{
    DISPLAY("its too hot outide")
}
ELSE 
{
    IF (temp >= 65){
        DISPLAY ("sure I will play outside")
    }
    ELSE 
    {
        DISPLAY ("its too cold outside")
    }
}

# Psuedo Code 2
DISPLAY ("What is the temperature outside in F?")
temp <- INPUT()
IF (temp >= 90)
{
    DISPLAY("its too hot outide")
}
IF (temp >= 65)
{
        DISPLAY ("sure I will play outside")
}
IF (temp < 65)
{
        DISPLAY ("its too cold outside")
}
```

What is the difference between the two pieces of code in the cell above?


```python
# Code 1
print("What is the temperature outside in F?")
temp = int(input())

if temp >= 90: 
    print("its too hot outide")
else:  
    if temp >= 65:
        print("sure I will play outside")
    else: 
        print("its too cold outside")
```

    What is the temperature outside in F?
    sure I will play outside



```python
# Code 2
print("What is the temperature outside in F?")
temp = int(input())

if temp >= 90: 
    print("its too hot outide")
if temp >= 65:
    print("sure I will play outside")
if temp < 65:
    print("its too cold outside")
```

    What is the temperature outside in F?
    its too hot outide
    sure I will play outside


What happens if we plug 56 for the temp? What happens if we plug 95 in? 

If we plug 56 in, then it will display the text "its too cold outside." It first checks the first input, if temp is greater than or equal to 90. Which it isn't so it moves on to the next if. If temp is greater than or equal to 65, which it isn't so it checks the last if/else statement and displays the text its too cold outside. 

If we plug 95 in we get two different results. Code one displays "its too hot outide" but code two displays "its too hot outide" and "sure I will play outside." Why is this?  

### Popcorn Hack #1 
Adjust Pseudo Code #2 so that it has the same output as Code #1 for all inputs. 


```python
# Insert your code here: 
print("What is the temperature outside in F?")
temp = int(input())

if temp >= 90: 
    print("its too hot outide")
elif temp >= 65:
    print("sure I will play outside")
elif temp < 65:
    print("its too cold outside")
```

    What is the temperature outside in F?
    its too hot outide


# Conditionals vs Booleans 

Quick reminder: 
- Conditionals: checks if a condition is true or false using statements like if, elif, and else if. 
- Booleans: Data type that conditionals use, only two: true and false

We have given an algorithm that uses conditionals and two boolean statements that should have the same output as the conditional. Which boolean statement works and which one doesn't? 

### Conditional: 


```python
# Psuedo Code
IF (isHoliday)
{
    driveWork<- False
}
ELSE
{
    IF (iswWeekday)
    {
        driveWork <_ True
    }
    ELSE
    {
        driveWork <- False
    }
}
```

### Boolean


```python
# Option 1: 
driveWork <- ( (isHoliday) AND (isWeekday))

# Option 2: 
driveWork <- ( (NOT (isHoliday)) AND (isWeekday))
```

### Answer

| <img src="https://i.ibb.co/hCtMMRH/Screenshot-2023-10-15-at-6-21-20-PM.png" width = 600px height = auto > |

Option 2 is the correct answer

### Popcorn Hack #2
Using the commands listed below, move the robot (gray triangle) through the white squares to the gray square wihtout touching the black squares in the least amount of lines as possible. 

Commands allowed: 
MOVE_FORWARD()
- moves the robot one sqaure in the direction it is facing 
ROTATE_LEFT()
- rotates the robot 90 degrees counterclockwise relative to itself 
ROTATE_RIGHT()
- rotates the robot 90 degrees clockwise relative to itself 
CAN_MOVE()
- checks if the robot can move forward in true or false (true: it can move forward. false: it can't move forward)

| <img src="https://i.ibb.co/3TzmV2b/Screen-Shot-2023-10-16-at-7-45-01-PM.png" width = 600px height = auto > |


```python
# Insert your code here: 
WHILE CAN_MOVE() IS True {
    REPEAT UNTIL GRAY SQUARE: 
        MOVE_FORWARD()
        ROTATE_RIGHT()
        MOVE_FORWARD()
        ROTATE_LEFT()
}
```


      File "/tmp/ipykernel_1209/3132200247.py", line 2
        WHILE CAN_MOVE() == True {
              ^
    SyntaxError: invalid syntax



### Optional Popcorn Hack
Change your code to an algorithm that works for any given course. 

Hint: use if, elif, else, and CAN_MOVE() 


```python
# Insert your code here: 
```

# Combining Selection and/or Iteration

Create an algorithm that uses selection and/or iteration to determine the cost of one item. 
THe display at the stores says the follorwing: 
- Green tagged items: 25% off 
- Red tagged items: 60% off
- Tax on all items is 10% 


```python
# Psuedo Code
DISPLAY ("What is the cost of the item?")
cost <- INPUT()
DIPLAY ("Is the tag green or red (type "True" if it is green, type "False" for red)")
tag <- BOOL(INPUT())
IF (tag == True) # Check if it is green tag (refer to lines above)
{
    cost <- 0.75 * cost
}
IF (tag == False) # Check if it is green tag (refer to lines above)
{
    cost <- 0.40 * cost
}
cost <- 1.10 * cost 
```


```python
print("What is the cost of the item?")
cost = int(input())
print("Is the tag green or red (type "True" if it is green, type "False" for red)")
tag = bool(input())

if tag == True: # Check if it is green tag (refer to lines above)
    cost = 0.75 * cost
if tag == False: # Check if it is green tag (refer to lines above)
    cost = 0.40 * cost
cost = 1.10 * cost # accounting for tax
```

# Famous Collatz Conjecture

1. Start with any positive integer 
2. IF that number is even, divide by 2
3. If that number is odd, multiply by 3 and add 1
4. Repeat steps 2 and 3 until you reach the number 1 

6 -> 3 -> 10 -> 5 -> 16 -> 8 -> 4 -> 2 -> 1

Collatz proposed that this sequence of numbers would always terminate at 1. The problem of whether this is true or not for all positive integers is still unsolved today. 

Lets create an algorithm that will start with any positive integer "n" and display the full sequence of numbers that result from this conjecture. 


```python
# Psuedo Code 
DISPLAY ("choose a value for n")
n <- INPUT() 
DISPLAY (n)
REPEAT UNTIL (n = 1)
{
    IF (n MOD 2 = 0)
    {
        n <- n/2
    }
    ELSE 
    {
        n <- 3 * n + 1
    }
DISPLAY (n)
}
```


```python
# Code 
print("choose a value for n")
n = int(input())
print(n)
while n != 1: 
    if n % 2 == 0: 
        n = n/2
    else: 
        n = (n*3)+1
    print(n)
```

    choose a value for n
    889
    2668
    1334.0
    667.0
    2002.0
    1001.0
    3004.0
    1502.0
    751.0
    2254.0
    1127.0
    3382.0
    1691.0
    5074.0
    2537.0
    7612.0
    3806.0
    1903.0
    5710.0
    2855.0
    8566.0
    4283.0
    12850.0
    6425.0
    19276.0
    9638.0
    4819.0
    14458.0
    7229.0
    21688.0
    10844.0
    5422.0
    2711.0
    8134.0
    4067.0
    12202.0
    6101.0
    18304.0
    9152.0
    4576.0
    2288.0
    1144.0
    572.0
    286.0
    143.0
    430.0
    215.0
    646.0
    323.0
    970.0
    485.0
    1456.0
    728.0
    364.0
    182.0
    91.0
    274.0
    137.0
    412.0
    206.0
    103.0
    310.0
    155.0
    466.0
    233.0
    700.0
    350.0
    175.0
    526.0
    263.0
    790.0
    395.0
    1186.0
    593.0
    1780.0
    890.0
    445.0
    1336.0
    668.0
    334.0
    167.0
    502.0
    251.0
    754.0
    377.0
    1132.0
    566.0
    283.0
    850.0
    425.0
    1276.0
    638.0
    319.0
    958.0
    479.0
    1438.0
    719.0
    2158.0
    1079.0
    3238.0
    1619.0
    4858.0
    2429.0
    7288.0
    3644.0
    1822.0
    911.0
    2734.0
    1367.0
    4102.0
    2051.0
    6154.0
    3077.0
    9232.0
    4616.0
    2308.0
    1154.0
    577.0
    1732.0
    866.0
    433.0
    1300.0
    650.0
    325.0
    976.0
    488.0
    244.0
    122.0
    61.0
    184.0
    92.0
    46.0
    23.0
    70.0
    35.0
    106.0
    53.0
    160.0
    80.0
    40.0
    20.0
    10.0
    5.0
    16.0
    8.0
    4.0
    2.0
    1.0


### Popcorn hack #3

We are given an algorhtim (below) for a robot to move from the current square to the grey square, completing the course (below). However it doesn't work. Why does the given algorithm not work? 

Using the commands listed below, fix the algorithm

Commands allowed: 
MOVE_FORWARD()
- moves the robot one sqaure in the direction it is facing 
ROTATE_LEFT()
- rotates the robot 90 degrees counterclockwise relative to itself 
ROTATE_RIGHT()
- rotates the robot 90 degrees clockwise relative to itself 
CAN_MOVE()
- checks if the robot can move forward in true or false (true: it can move forward. false: it can't move forward)

#### Course: 

| <img src="https://i.ibb.co/cgz67XJ/Screen-Shot-2023-10-16-at-8-05-24-PM.png" width = 600px height = auto > |

#### Given Algorithm 


```python
REPEAT UNTIL (goalReached)
{
    IF (CAN_MOVE(FORWARD))
    {
        MOVE_FORWARD
    }
    ELSE
    {
        IF CAN_MOVE(RIGHT)
        {
            ROTATE_RIGHT
            MOVE_FORWARD
        }
    }
}
```

#### Put your answer to the question "Why does the given algorithm not work?" here: 
- Because if it hits a corner and can't move 



```python
# Insert your updated algorithm here: 
REPEAT UNTIL (goalReached)
{
    IF (CAN_MOVE(FORWARD))
    {
        MOVE_FORWARD
    }
    ELSE
    {
        IF CAN_MOVE(RIGHT)
        {
            ROTATE_RIGHT
            MOVE_FORWARD
        }
        ELSE IF CAN_MOVE(LEFT)
        {
            ROTATE_LEFT
            MOVE_FORWARD
        }
        ELSE 
        {
            ROTATE_RIGHT
            ROTATE_RIGHT
        }
    }
}
```


      File "/tmp/ipykernel_1209/3318149462.py", line 2
        REPEAT UNTIL (goalReached)
               ^
    SyntaxError: invalid syntax



# Homework

- Create an algorithm that uses selection and/or iteration that will represent one player's turn in a game. 

- During a turn, each player gets 4 attempts/chances to get the greates number possible. 

- During each attempt the player will use a random number generator to select a random number 1-10. 

- After the player has had 4 chances, their score is the greatest number they receieved from the random number generator, and their turn is over. 

Use the following flowchart to assist you: 

| <img src="https://i.ibb.co/ZBFgwn2/Screen-Shot-2023-10-15-at-7-40-22-PM.png" width = 600px height = auto > 


```python
from random import randint
attempts = 1
myAttempts = 1
number = 0
score = 0
myScore = 0
myNumber = 0

while attempts != 5:
    print("Your Turn: ")
    print("----------------------------------")
    print("Attempt #: ", attempts)
    randomNum = randint(1,10)
    if randomNum > number:
        number = randomNum
        print("Score: ", number)
        attempts += 1
    else:
        print("Score ", number)
        attempts += 1

if attempts == 5:
    print("\n")

while myAttempts != 5:
    print("My Turn: ")
    print("----------------------------------")
    print("Attempt #: ", myAttempts)
    randomNum = randint(1,10)
    if randomNum > myNumber:
        myNumber = randomNum
        print("Score: ", myNumber)
        myAttempts += 1
    else:
        print("Score ", myNumber)
        myAttempts += 1

myScore = myNumber
score = number

if myAttempts == 5:
    print("\n")
    if myScore > score:
        print("I win")
    elif myScore == score:
        print("Tie")
    else:
        print("You won")
```

    Your Turn: 
    ----------------------------------
    Attempt #:  1
    Score:  4
    Your Turn: 
    ----------------------------------
    Attempt #:  2
    Score:  8
    Your Turn: 
    ----------------------------------
    Attempt #:  3
    Score:  9
    Your Turn: 
    ----------------------------------
    Attempt #:  4
    Score  9
    
    
    My Turn: 
    ----------------------------------
    Attempt #:  1
    Score:  1
    My Turn: 
    ----------------------------------
    Attempt #:  2
    Score:  8
    My Turn: 
    ----------------------------------
    Attempt #:  3
    Score  8
    My Turn: 
    ----------------------------------
    Attempt #:  4
    Score  8
    
    
    You won

