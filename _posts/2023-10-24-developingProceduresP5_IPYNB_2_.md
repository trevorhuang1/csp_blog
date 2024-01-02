---
toc: True
comments: False
layout: default
title: CB 3.12,3.13 Developing Procedures
type: hacks
courses: {'compsci': {'week': 10}}
description: CB 3.12,3.13 Developing Procedures
---

<h1>- CB 3.12,3.13 Developing Procedures</h1>


What is a procedure?

A procedure is a named group of code that has paramaters and return values. Procedures are known as methods or functions depending on the language.

A procedure executes the statements within it on the parameters to provide a return value.

What are parameters?

Paramaters are input values of a procedure that are specified by arguments.Arguments specify the values of the parameters when a procedure is called.

By creating theses algorithms the readibility of code increases and the complexity decreases. This is becasue a function's name can tell the reader what action it will perform, and by calling it, the code becomes more clean and easy to understand.



<h1>What is a return value?</h1>
<h3>A return value is the value that is returned when a function or a method is called.</h3>
<h3>That return value can be assigned or printed</h3>

<img src = "/passionProject/_notebooks/images.png">

Procedures are used to create algorthims that can perform certain actions or return values. When a procedure returns a value, theis information must be stored in a variable for later use. However some procedures like the MOVE_FORWARD() perform an action, and don't return a value. The image above provides an example of where procedures that don't output a value would be used.


```python
A 60$ item recieves a 20% discount and taxed at 8%.
PROCEDURE applyDiscount(cost, percentDiscounted)
{
    temp ← 100 - percentDiscounted
    temp← temp/ 100
    cost ← cost *temp
    RETURN(cost)
}

price ← applyDiscount(60, 20)
This is how we get the final price with the discount by calling the procedure and assigning it to the price variable.


PROCEDURE applyTax(cost, percentTaxed)
{
    temp ← 100 + percentTaxed
    temp← temp/ 100
    cost ← cost *temp
    RETURN(cost)
}
price ← applyTax(price, 8)
This applys the 8% tax to the price determined after the discount.
```

<h3>Popcorn Hack 1</h3>
Given the applyTax procedure above:
How would you call the procedure to get it to find the price using cost = 50, and percentTaxed = 10, and what value will it return?


```python
#code here
def applyTax(cost, tax):
    taxed = cost * tax/100
    finalCost = cost + taxed
    return finalCost
applyTax(50,10)
```




    55.0



<h1>What Are Functions?</h1>
<ul>
    <li>Collections of code</li>
    <li>Divides large program into smaller chunks</li>
    <li>Better readability</li>
    <li>Less repetitive code</li>
    <li>More efficient code</li>
    <li>Good organization</li>
</ul>



<h1>What Are The Components of a Function?</h1>
<ul>
    <li>The function declaration</li>
    <li>The parameters (input). This is also referred to as an argument when a value is being passed to the actual function.</li>
    <li>The functionality</li>
    <li>The return value (output)</li>
    <li>Calling the function</li>
</ul>


```python
# Defining Functions
#
# def function_name(parameter1, parameter2, etc..):
#     code here...
#
#     return return_value;

# return the value of parameter1 plus parameter2;
def add(parameter1, parameter2): # creates a function that takes in two parameters
    solution = parameter1 + parameter2; # sets solution to the sum of parameter1 and parameter2
    return solution; # return solution
    
print(add(5, 5)); # prints the return value of add(5,5)
```

<h2 style="font-weight:bold">Popcorn Hack 2:</h2>
<h3>1. Make a function that returns the difference of two numbers</h3>


```python
# Code here
num1 = int(input("Enter a number"))
num2 = int(input("Enter a number to subtract from the original"))

def subtract(x, y):
    return x - y

subtract(num1, num2)
```




    3453456



<h1>What is a Class?</h1>
<ul>
    <li>A class is an outline for a set of nested functions and variables.</li>
    <li>There are instance variables</li>
    <li>Functions</li>
    <ul>
        <li>Constructor method (Required)</li>
        <li>To String method</li>
        <li>Getter method</li>
        <li>Setter method</li>
    </ul>
</ul>
<h1>How Does a Class Work?</h1>


```python
# Defining Classes
class person:
    def __init__(self, name, age, ): # constructor
        self.name = name;
        self.age = age;
    
    def getName(self): # method to create get name
        return self.name;
    
    def getAge(self): # method to create get age
        return self.age;
    
    def setName(self, name): # method to create set name
        self.name = name;
        
    def setAge(self, age): # method to create set age
        self.age = age;
        
    def yearOlder(self): # method to increment age by 1
        self.age += 1;
        
    def __str__(self): # method that returns a string when the object is printed
        return (f"My name is {self.name} and I am {self.age} years old.")

Person1 = person("John Doe", 15);
print(Person1)


print(Person1);
```

    My name is John Doe and I am 15 years old.
    My name is John Doe and I am 15 years old.


<h2 style="font-weight:bold">Popcorn Hack 3:</h2>
<h3>1. Create a Car class which has the attributes model, vehicle name, and price</h3>
<h3>2. Create instances of the following cars</h3>
<ul>
    <li>Name: Honda Civic , Model Year: 2018 , Price: $13,000 </li>
    <li>Name: Toyota Prius, Model Year: 2023 , Price: $28,000 </li>
    <li>Name: Chevrolet Impala, Model Year: 2020 , Price: $22,000 </li>
</ul>


```python
class car:
    def __init__(self, model, name, price,):
        self.model = model
        self.name = name
        self.price = price
    
car1 = car("Honda Civic", 2018, 13000)
car2 = car("Toyota Prius", 2023, 28000)
car3 = car("Chevrolet Impala", 2020, 22000)
```

<h1>Homework:</h1>
<h2>Assignment 0: How do you use functions?</h2>
<h3>Create a turtle python function that...</h3>
<ol>
    <li>Takes a single parameter as the number of sides</li>
    <li>Outputs a shape corresponding to the number of sides</li>
    <li>Call the function with the argument being a variable with the user input</li>
</ol>
<h3>Hint: </h3>


```python
# Turtle does not work on school wifi. Copy paste into a replit if you wanna see if I did it right

import turtle

pen = turtle.Turtle()
angle = 0
sides = int(input("How many sides? "))
if sides == 1 or sides == 2:
    print("Please enter a SHAPE")
else:
    angle = 360/sides
    

for i in range(sides):
    pen.forward(30)
    pen.right(angle)
    i += 1

turtle.done()

```

<h2>Assignment 1</h2>
<h3>Create a function that...</h3>
<ol>
    <li>Takes an array as the parameter</li>
    <li>Returns the array of distinct values</li>
    <li>Don't use test arrays</li>
</ol>



```python
arr1 = []
arr2 = []

while True:
    add = input("Add a number. Enter 's' to stop")
    if add == "s":
        break
    arr1.append(int(add))
    if int(add) not in arr2:
        arr2.append(int(add))

print("Numbers inputed: ",arr1)
print("After duplicates removed: ",arr2)
```

    Numbers inputed:  [2, 23, 34, 2, 2, 6, 45, 2, 34, 45, 21, 2, 2, 9]
    After duplicates removed:  [2, 23, 34, 6, 45, 21, 9]


<h2>Assignment 2:</h2>
<h3>Create a student class that...</h3>
<ol>
    <li>Has a constructor that takes three parameters as attributes</li>
    <li>
        <ul>
            <li>email</li>
            <li>name</li>
            <li>grade</li>
        </ul>
    </li>
    <li>Three getter methods to access the name, email, and grade</li>
    <li>Three setter methods to modify the name, email, and grade</li>
    <li>A to string method that returns the three instance variables in this format - "My name is {name}. My email is {email}. My grade is {grade}</li>
    <li>Create an instance of the class that corresponds with you</li>
</ol>



```python
class person:
    def __init__(self, email, name, grade, ): # constructor
        self.email = email
        self.name = name
        self.grade = grade
    
    def getEmail(self): # method to create get email
        return self.email
    
    def getName(self): # method to create get name
        return self.name
    
    def getGrade(self): # method to create get grade
        return self.grade
    
    def setEmail(self, email): # method to create set email
        self.email = email
    
    def setName(self, name): # method to create set name
        self.name = name
        
    def setGrade(self, grade): # method to create set grade
        self.grade = grade
        
    def __str__(self): # method that returns a string when the object is printed
        return (f"My name is {self.name} and I am in {self.grade}th grade. My email is {self.email}")

trevor_huang = person('fake@gmail.com', 'Trevor Huang', 10)
print(trevor_huang)

```

    My name is Trevor Huang and I am in 10th grade. My email is fake@gmail.com

