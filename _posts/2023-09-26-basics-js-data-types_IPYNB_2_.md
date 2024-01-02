---
title: Javascript Data Types/Lists
hide: True
description: A Tech Talk on javascript data types and how to use with lists
type: hacks
permalink: /basics/datatypes
author: Rohan Juneja
---

{% include nav_basics.html %}

# string datatype
- We discussed that strings store text
- It is useful to know a few functions that can be used on string manipulation (see example below)
- We can see the type of data using `typeof` operator


```python
%%js

// assign variable
var name = "Trevor";
var hello = "Hello World";
console.log("variable: hello");
console.log(hello);
console.log(name);

// seeing the type of this data
console.log("variable: hello check typeof")
console.log(typeof hello)

// add strings together
console.log("string concatenation: hello + Rohan!")
console.log(hello + " Rohan!")
```


    <IPython.core.display.Javascript object>


## .substring()


```python
%%js
var hello = "Hello World";

// getting a certain component of this text
// (here the _ is a standin for the space character)
// H  e  l  l  o  _  W  o  r  l  d
// 0  1  2  3  4  5  6  7  8  9  10
// if we want the hello component, we want characters 0-4, so we use the following function
// (note how we use 0 and 5 as arguments, the last character is NOT INCLUSIVE)
console.log("substring: hello 0, 5")
console.log(hello.substring(0, 5) + hello.substring(4,11))
```


    <IPython.core.display.Javascript object>


## .toUpperCase() and .toLowerCase()


```python
%%js
var hello = "Hello World";

// useful functions to make string lowercase or uppercase
console.log("string convert to upper case: hello toUpperCase")
console.log(hello.toUpperCase())
console.log("string convert to lower case: hello toLowerCase")
console.log(hello.toLowerCase())
```


    <IPython.core.display.Javascript object>


## .includes()


```python
%%js
var hello = "Hello World";
var name = "Trevor Huang";

// useful function to check if one string is contained in another
console.log("string includes: hello includes Rohan")
console.log(hello.includes("Rohan"))
console.log("string includes: hello includes Hello")
console.log(hello.includes("Hello"))
console.log(hello.includes("Trevor"))
```


    <IPython.core.display.Javascript object>


# number datatype
- we discussed that numbers store numbers
- here are some useful ideas in javascript to deal with numbers


```python
%%js
console.log("Numbers info")

// assign numbers to varialbes
console.log("variable: num1")
var num1 = 9
console.log(num1)
console.log("variable: num2")
var num2 = 6
console.log(num2)


// simple operations with numbers
console.log("Operations")
console.log("subtract: num1 - num2")
console.log(num1 - num2)
console.log("add: num1 + num2")
console.log(num1 + num2)
console.log("divide: num1 / num2")
console.log(num1 / num2)
console.log("multiply: num1 * num2")
console.log(num1 * num2)
console.log("remainder (modulo): num1 % num2")
console.log(num1 % num2)
```


    <IPython.core.display.Javascript object>


# number formatting


```python
%%js
console.log("variable: num1")
var num1 = 9
console.log(num1)
console.log("variable: num2")
var num2 = 7
console.log(num2)

// converting numbers to text
console.log("number convert string: num1")
console.log(num1.toString())

// rounding a number
console.log("round(num1 / num2)")
console.log(Math.round(num1 / num2))

// rounding a number to decimal palces
console.log("set decimals to 2 places (num1 / num2)")
console.log((num1 / num2).toFixed(2))
console.log((num1/num2).toFixed(3))
```


    <IPython.core.display.Javascript object>


# Array datatype
- an array is just a list of other datatypes
- put all the items in square brackets
- some useful methods below


```python
%%js
console.log("Array: assigning a list of strings")
var str1 = "1st string"
var arr_data = [str1, "2nd string", "3rd string"]
var abc = ["a", "b", "c"]
// seeing what is in the array
console.log(arr_data)
console.log(abc)
// getting one thing from an array
// "A string" "Other Data" "more data"
//    0           1            2
console.log("Array: referencing a cell #1")
console.log([ arr_data[1] ])  // zero based counting: 1 is 2nd cell

```


    <IPython.core.display.Javascript object>


# array manipulation


```python
%%js
console.log("Array: assigning a list of strings")
var str1 = "1st string"
var arr_data = [str1, "b", "c"]
// seeing what is in the array
console.log(arr_data)

// adding something new to the array
console.log("Array: adding to list")
arr_data.push("4th string")
console.log(arr_data)

// removing the first element of array
console.log("Array: removing from front of list")
arr_data.shift()
console.log(arr_data)

// removing the last element of array
console.log("Array: removing from end of list")
arr_data.pop()
console.log(arr_data)

arr_data[2] = "new third string"
console.log(arr_data)
```


    <IPython.core.display.Javascript object>


# Object datatype

- store records as key-value pairs
- are defined by enclosing data in curly braces `{}`
- allow access and modification using dot `.` or square bracket `[]` notation


```python
%%js
console.log("Object: assigning key-value objects")
var obj = {
    name: "Trevor",
    age: 15,
    school: "DNHS",
    sport: "XC"
};

// The following is stored in the object called "obj"
// {
//     name: "Safin",
//     age: 13
// }
//
// The key "name" is associated with the string value "Safin"
// The key "age" is associated with the number value 13
// Notice that keys are of the type "string"

// print obj to the console
console.log(obj);
console.log(obj.name);
// -> { name: 'Safin', age: 13 }
// Notice that single quotes ' and double quotes " can be used interchangeably
```


    <IPython.core.display.Javascript object>


# object access


```python
%%js
console.log("Object: assigning key-value objects")
var obj = {
    name: "Trevor",
    age: 15,
    school: "DNHS",
    sport: "XC"
};

// The following is stored in the object called "obj"
// {
//     name: "Safin",
//     age: 13
// }
//
// The key "name" is associated with the string value "Safin"
// The key "age" is associated with the number value 13
// Notice that keys are of the type "string"

// print obj to the console
console.log(obj);
// -> { name: 'Safin', age: 13 }
// Notice that single quotes ' and double quotes " can be used interchangeably

// To access certain values within an object, also known as an object's fields,
// you can use the name of the object suffixed with a dot and the name of the field
// or using the square bracket notation shown below
console.log("Object: using key name to access the name value (key notation)")
console.log(obj["name"]);
console.log("Object: using key name to access the name value (dot notation)")
console.log(obj.name);
// -> Safin

// Fields of an object can be manipulated similar to variables
console.log("Object: mutating the key name from Safin to John")
obj.name = "John"
obj.sport = "track"
console.log(obj);
console.log(obj.name);

// -> John

// A key-value pair can be added to the object
console.log("Object: mutating the key name from Safin to John")
obj["ghid"] = "jm1021"
console.log(obj);
// Observe new key
```


    <IPython.core.display.Javascript object>


# Hacks


```python
%%js

//Object about me
var trevor = {
    name: "Trevor Huang",
    age: 15,
    birthday: "April 23rd",
    schedule: ["Period 1: AP Chemistry", "Period 3: Honors Humanities", "Period 4: AP Chinese", "Period 5: AP CSP"],
    hobbies: ["Running", "Video games"],
    favHoliday: "Halloween",
    favNumber: 8
};

//Prints my object
console.log("My original Object:")
//code from chatgpt
console.log(JSON.stringify(trevor, null, 2));

//updates schedule again
console.log("\nUh oh, looks like I'm missing my period 2 class and some hobbies. This is the updated object: ");
//Adds my missing period 2 and some more hobbies
trevor.schedule.splice(1, 0, "Period 2: Calculus AB");
//Adds hanging out with friends to list of hobbies
trevor.hobbies.push("Hanging out with friends");
trevor.hobbies.push("Playing with my cat");
console.log(JSON.stringify(trevor, null, 2));

//Some mathematical operations
var ageInFiveYears = trevor.age + 5;
var halfAge = trevor.age / 2;
var numberAndAge = trevor.age * trevor.favNumber;

//contextualising
console.log("In five years, I will be " + ageInFiveYears + " years old");
console.log("Half of my age is " + halfAge + " years");
console.log("My current age multiplied by my favorite number is " + numberAndAge);

//using type of
var typeOfAge = typeof trevor.age;
var typeOfHobbies = typeof trevor.hobbies;
var typeOfHoliday = typeof trevor.favHoliday;

console.log("\nType of age: " + typeOfAge);
console.log("Type of hobbies: " + typeOfHobbies);
console.log("Type of favorite holiday: " + typeOfHoliday);
```


    <IPython.core.display.Javascript object>

