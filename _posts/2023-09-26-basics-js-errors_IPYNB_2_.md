---
layout: post
title: 1.4 Correcting errors
description: Practice with identifying and correcting code blocks
courses: {'compsci': {'week': 5}}
type: hacks
permalink: /basics/js-debug
---

{% include nav_basics.html %}

[College Board Big Idea 1](https://apclassroom.collegeboard.org/103/home?unit=1)

## Identifying and Correcting Errors (Unit 1.4)

> Become familiar with types of errors and strategies for fixing them

- Review CollegeBoard videos and take notes on blog
- Complete assigned MCQ questions if applicable

# Code Segments

Practice fixing the following code segments!

## Segment 1: Alphabet List

Intended behavior: create a list of characters from the string contained in the variable `alphabet`

### Code:


```python
%%js

var alphabet = "abcdefghijklmnopqrstuvwxyz";
var alphabetList = [];

for (var i = 0; i < 10; i++) {
	alphabetList.push(i);
}

console.log(alphabetList);
```


    <IPython.core.display.Javascript object>


### What I Changed

- First of all, when looking at the console, it becomes obvious that the for loop is actually only pushing the "i" values aka 0-9. Below is the fix. It uses the .length function to figure out how many times the loop has to repeat, and each time it pushes the corresponding number in the array of alphabet into alphabet list.


```python
%%js

var alphabet = "abcdefghijklmnopqrstuvwxyz";
var alphabetList = [];

for (var i = 0; i < alphabet.length; i++) {
    alphabetList.push(alphabet[i]);
}

console.log(alphabetList);
```


    <IPython.core.display.Javascript object>


## Segment 2: Numbered Alphabet

Intended behavior: print the number of a given alphabet letter within the alphabet. For example:
```
"_" is letter number _ in the alphabet
```

Where the underscores (_) are replaced with the letter and the position of that letter within the alphabet (e.g. a=1, b=2, etc.)

### Code:


```python
%%js

// Copy your previous code to built alphabetList here
var alphabet = "abcdefghijklmnopqrstuvwxyz";
var alphabetList = [];

for (i = 0; i < alphabet.length; i++) {
    alphabetList.push(alphabet[i]);
}

let letterNumber = 5;

for (var i = 0; i < alphabetList.length; i++) {
	if (i + 1 == letterNumber) {
		console.log(alphabetList[i] + " is letter number 1 in the alphabet");
	}
}

// Should output:
// "e" is letter number 5 in the alphabet
```


    <IPython.core.display.Javascript object>


### What I Changed

- Added old code to the cell
- The issue was that i was being compared to alphabet list which is an array instead of alphabetlist.length
- i + 1 becaise arrays are zero indexed
- Changed to alphabetList[i] so that it prints the letter instead of the number assigned to it

## Segment 3: Odd Numbers

Intended behavior: print a list of all the odd numbers below 10

### Code:


```python
%%js

let odds = [];
let i = 1;

while (i <= 10) {
  odds.push(i);
  i += 2;
}

console.log(odds);
```


    <IPython.core.display.Javascript object>


### What I Changed

- I had the list start from 1, which is the first odd number

# BELOW NOT EDITED

The intended outcome is printing a number between 1 and 100 once, if it is a multiple of 2 or 5 
- What values are outputted incorrectly. Why?
- Make changes to get the intended outcome.


```python
%%js

var numbers = []
var newNumbers = []
var i = 0

while (i < 100) {
    numbers.push(i)
    i += 1
}
for (var i of numbers) {
    if (numbers[i] % 5 === 0)
        newNumbers.push(numbers[i])
    else if (numbers[i] % 2 === 0)
        newNumbers.push(numbers[i])
}
console.log(newNumbers) 


```


    <IPython.core.display.Javascript object>


### What I changed...
- The original function was printing all of the numbers that were a multiple of 2 AND 5 twice
- I changed the second if statement to an else if statement so that the second if statement won't print a multiple of 2 and 5 twice

# Challenge

This code segment is at a very early stage of implementation.
- What are some ways to (user) error proof this code?
- The code should be able to calculate the cost of the meal of the user

Hint:
- write a “single” test describing an expectation of the program of the program
- test - input burger, expect output of burger price
- run the test, which should fail because the program lacks that feature
- write “just enough” code, the simplest possible, to make the test pass

Then repeat this process until you get program working like you want it to work.


```python
%%js

var menu =  {"burger": 3.99,
         "fries": 1.99,
         "drink": 0.99}
var total = 0

//shows the user the menu and prompts them to select an item
console.log("Menu")
for (var item in menu) {
    console.log(item + "  $" + menu[item].toFixed(2)) //why is toFixed used?
}
//ideally the code should support mutliple items
var item = "burger"

//code should add the price of the menu items selected by the user 
console.log(total)
```

## Hacks
- Fix the errors in the first three segments in this notebook and say what you changed in the code cell under "What I Changed" (Challenge is optional)
