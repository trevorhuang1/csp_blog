---
toc: True
comments: True
layout: post
title: CB 3.7,3.8 - Iteration in Python
description: Lesson for iteration in Python, using College Board lessons 3.7 & 3.8.
type: hacks
author: Advik Garg, Srijan Atti, Akhil Singamneni, Aashray Rajagopalan
courses: {'compsci': {'week': 8}}
---

# Introduction
In this lesson, we will explore the various ways to create loops in Python. Loops are essential for repetitive tasks and are a fundamental concept in programming. We will cover different types of loops, advanced loop techniques, and how to work with lists and dictionaries using loops.

## For Loops
- Used to iterate over a sequence (such as a list, tuple, string, or range) 
- Executes a block of code for each item in the sequence


```python
# APCSP Pseudo-Code: Iterating Over a List of Fruits

fruits ← ["apple", "banana", "cherry"]

FOR EACH fruit IN fruits:
    DISPLAY fruit
END FOR



```


```python
# Example 1: Simple for loop
fruits = ["apple", "banana", "cherry"]
for fruit in fruits:
    print(fruit)
```

    apple
    banana
    cherry


## While Loops
- Used to execute a block of code as long as a condition is true


```python
# APCSP Pseudo-Code: Using a While Loop to Count and Display Numbers


i ← 1


WHILE i ≤ 5:
    DISPLAY i
    i ← i + 1
END WHILE
```


```python
# Example 2: Simple while loop
i = 1
while i <= 5:
    print(i)
    i += 1
```

    1
    2
    3
    4
    5


## Looping with Lists and Dictionaries
- Used to iterate through the elements of lists and dictionaries


```python
# APCSP Pseudo-Code: Loop Through a List

numbers ← [1, 2, 3, 4]
FOR EACH num IN numbers:
    DISPLAY num
END FOR

# APCSP Pseudo-Code: Loop Through a Dictionary
person ← {"name": "aashray", "age": 15, "city": "San Diego"}
FOR EACH key, value IN person:
    DISPLAY key, ":", value
END FOR

```


```python
# Example 3: Loop through a list
numbers = [1, 2, 3, 4]
for num in numbers:
    print(num)

# Example 4: Loop through a dictionary
person = {"name": "aashray", "age": 15, "city": "San Diego"}
for key, value in person.items():
    print(key, ":", value)

```

    1
    2
    3
    4
    name : aashray
    age : 15
    city : San Diego


# Popcorn Hack 1

- Use a loop to get X amount of inputs. Then use a loop to find the type of each value.

- Extra Challenge: If an input is a number, make the corresponding value in the dictionary a number.


```python
dictionary = {}
inputs = int(input("How many values do you want to enter?"))

for i in range(inputs):
    user_input = input("What would you like to add?")
    try:
        user_input = eval(user_input)
        print(type(user_input))
    except ValueError:
        print("string")
```

    <class 'int'>
    <class 'int'>


## Looping with Index Variable
You can use the `range` function to create a loop with an index variable.


```python
# APCSP Pseudo-Code: Loop Through a List Using Index

lst ← [4, 6, 7, 2]
FOR i IN RANGE(LENGTH(lst)):
    DISPLAY "Index: " + STRING(i)
    DISPLAY "Element: " + STRING(GET_ELEMENT(lst, i))
END FOR
```


```python
# Example 5: Loop with an index variable

lst = [4, 6, 7, 2]

for i in range(len(lst)): # Loop for the number of elements in the list
    print('Index: ' + str(i)) # Print the index
    print('Element: ' + str(lst[i])) # Print the element
```

    Index: 0
    Element: 4
    Index: 1
    Element: 6
    Index: 2
    Element: 7
    Index: 3
    Element: 2


## Nested If Statements
You can nest conditional statements inside a `for` loop to execute different code based on conditions.


```python
# APCSP Pseudo-Code: For Loop with Nested If Statements

numbers ← [1, 2, 3, 4, 5]
FOR EACH num IN numbers:
    IF num MOD 2 EQUALS 0:
        DISPLAY num, "is even"
    ELSE:
        DISPLAY num, "is odd"
    END IF
END FOR

```


```python
# Example 6: For loop with nested if statements
numbers = [1, 2, 3, 4, 5]
for num in numbers:
    if num % 2 == 0:
        print(num, "is even")
    else:
        print(num, "is odd")
```

    1 is odd
    2 is even
    3 is odd
    4 is even
    5 is odd


# Popcorn Hack 2

- Use the input() function to append a range of integers from a list

- Use a nested if statement to only print numbers in the list that are evenly divisble by 3


```python
nums = [1,3,4,2,32,4,3,35,64,34,45,4,33,39,12,42]
divisible = []

#Code goes here

start = int(input("Enter your starting value: "))
end = int(input("Enter your end value: "))

for i in range(start-1, end+1):
    num = nums[i]
    if num % 3 == 0:
        print(num,"is divisible by 3")
```

    3 is divisible by 3
    3 is divisible by 3
    45 is divisible by 3


## Try/Except
- Using a `try` and `except` block inside a loop can handle errors gracefully.
  
- Very useful for production code, even in frontend webapps
    - Ex: Giving an error page instead of dumping critical information on the webpage


```python
# APCSP Pseudo-Code: Handling Errors in a For Loop

numbers ← [1, 2, "three", 4, 0, "five"]
FOR EACH item IN numbers:
    TRY:
        DISPLAY 10 / item
    CATCH ZeroDivisionError:
        DISPLAY "Division by zero"
    CATCH TypeError:
        DISPLAY "Type error"
    END TRY
END FOR

```


```python
numbers = [1, 2, "three", 4, 0, "five"]

for item in numbers:
    try:
        print(10 / item)
    except ZeroDivisionError: #Type of error: Dividing by Zero
        print("Division by zero")
    except TypeError: #Type of error: Dividing by something that isn't a number
        print("Type error")
```

    10.0
    5.0
    Type error
    2.5
    Division by zero
    Type error


# Popcorn Hack 3
- Create a for loop that uses a try and except statement for an AttributeError
- Use integers and a list to create scenarios where the loop will either print something expected or print an error message
- *CHALLENGE:* Try using the `math` module for this error


```python
import math

numbers = [-4, 2, 3]

# Code goes here
for value in numbers:
    try:
        math.squareroot(value)
    except AttributeError:
        print("Attribute Error")
```

    Attribute Error
    Attribute Error
    Attribute Error


## Continue and Break
- `Continue` statement skips the current iteration
- `Break` statement exits the loop prematurely


```python
# APCSP Pseudo-Code: For Loop with Continue and Break

numbers ← [1, 2, 3, 4, 5]
FOR EACH num IN numbers:
 
    IF num EQUALS 3:
        CONTINUE
    IF num EQUALS 5:
        BREAK 
    DISPLAY num
END FOR

```


```python
# Example 8: For loop with continue and break
numbers = [1, 2, 3, 4, 5]
for num in numbers:
    if num == 3:
        continue  # Skip the number 3
    if num == 5:
        break  # Exit the loop when 5 is encountered
    print(num)
```

    1
    2
    4


# Nested For Loops
- You can also put for loops within for loops
- Allows for looping an exponential amount of times


```python
# APCSP Pseudo-Code: Nested Loops for Group Names

groups ← [["advik", "aashray"], ["akhil", "srijan"]]

FOR EACH pair IN groups:
    FOR EACH person IN pair:
        DISPLAY person + " is cool"
    END FOR
    DISPLAY pair[0] + " and " + pair[1] + " love to code code code"
END FOR

```


```python
groups = [['advik', 'aashray'], ['akhil', 'srijan']]

for pair in groups:
    for person in pair:
        print(person + ' is cool')
    print(pair[0] + ' and ' + pair[1] + ' love to code code code')
```

    advik is cool
    aashray is cool
    advik and aashray love to code code code
    akhil is cool
    srijan is cool
    akhil and srijan love to code code code


# (OPTIONAL) Popcorn Hack 4
- Create a nested for loop that iterates over a dictionary that has:
    - A name for each key
    - A list for each value containing stuff like age, grade, etc.
- Break/continue if certain conditions are met
- Have fun! If you want to, relate it to a theme!


```python
people = {}

# Code here
```

## Iteration via Recursion
- A technique where a function calls itself
- Can be used to recreate loops until a certain condition is met


```python
# APCSP Pseudo-Code: Recursion for Factorial Calculation

FUNCTION factorial(n):
    IF n EQUALS 0:
        RETURN 1
    ELSE IF n LESS THAN 0:
        RETURN "undefined"
    ELSE IF TYPEOF(n) EQUALS "float":
        RETURN "not solvable without gamma function"
    ELSE:
        RETURN n TIMES factorial(n - 1)
    END IF
END FUNCTION

result ← CALL factorial(5)
DISPLAY "Factorial of 5 is", result

```


```python
# Example 9: Recursion for factorial calculation
def factorial(n):
    if n == 0: #Conditions to stop the recursion
        return 1 # 0! is 1
    elif n < 0:
        return "undefined" # Undefined for negative numbers 
    elif isinstance(n, float):
        return "not solvable without gamma function" # Only accept integers
    else:
        return n * factorial(n - 1) #Function calling itself

result = factorial(5)
print("Factorial of 5 is", result)
```

    Factorial of 5 is 120


# Homework

- Add student names w/ grades to a dictionary until the user doesn't want more students
    - Prompt for user input for all of these


- Use a nested if/else statement in a for loop 
    - Get the highest score in the dictionary
    - Add all students who passed into a new list (add student names, not their scores)



- Bonus: Use a try/except for any scores that aren't integers 


```python
students = {}
passed = []
highScore = 0
#Code goes here

while True:
    student = input("Enter the student's name (quit to stop): ")
    if student == "quit":
        break
    try:
        grade = int(input(f"Input the student's score: "))
        students[student] = grade
    except ValueError:
        print("Invalid input. Please enter an integer for the grade.")
    
    if grade >= 60:
        passed.append(student)
    print(student + ": " + str(grade))
    if grade > highScore:
        highScore = grade

print("Students who passed: ")
for person in passed:
    print(person)

print("Highest score in the class: ")
print(highScore)
```

    ian: 99
    kyle: 100
    trevor: 33
    Invalid input. Please enter an integer for the grade.
    trevor: 33
    Students who passed: 
    ian
    kyle
    Highest score in the class: 
    100

