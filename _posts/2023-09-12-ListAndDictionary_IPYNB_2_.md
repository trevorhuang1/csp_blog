---
toc: True
comments: True
layout: post
title: List and Dictionary
description: List and dictionary hack
type: hacks
courses: {'compsci': {'week': 4}}
---

```python
# Sample of Python Variables

# variable of type string
print("What is the variable name/key?", "value?", "type?", "primitive or collection, why?")
name = "John Doe"
print("name", name, type(name))

print()


# variable of type integer
print("What is the variable name/key?", "value?", "type?", "primitive or collection, why?")
age = 18
print("age", age, type(age))

print()

# variable of type float
print("What is the variable name/key?", "value?", "type?", "primitive or collection, why?")
score = 90.0
print("score", score, type(score))

print()

# variable of type list (many values in one variable)
print("What is variable name/key?", "value?", "type?", "primitive or collection?")
print("What is different about the list output?")
langs = ["Python", "JavaScript", "Java"]
print("langs", langs, type(langs), "length", len(langs))
print("- langs[0]", langs[0], type(langs[0]))

print()

# variable of type dictionary (a group of keys and values)
print("What is the variable name/key?", "value?", "type?", "primitive or collection, why?")
print("What is different about the dictionary output?")
person = {
    "name": name,
    "age": age,
    "score": score,
    "langs": langs
}
print("person", person, type(person), "length", len(person))
print('- person["name"]', person["name"], type(person["name"]))

```

    What is the variable name/key? value? type? primitive or collection, why?
    name John Doe <class 'str'>
    
    What is the variable name/key? value? type? primitive or collection, why?
    age 18 <class 'int'>
    
    What is the variable name/key? value? type? primitive or collection, why?
    score 90.0 <class 'float'>
    
    What is variable name/key? value? type? primitive or collection?
    What is different about the list output?
    langs ['Python', 'JavaScript', 'Java'] <class 'list'> length 3
    - langs[0] Python <class 'str'>
    
    What is the variable name/key? value? type? primitive or collection, why?
    What is different about the dictionary output?
    person {'name': 'John Doe', 'age': 18, 'score': 90.0, 'langs': ['Python', 'JavaScript', 'Java']} <class 'dict'> length 4
    - person["name"] John Doe <class 'str'>


### List and Dictionary purpose
Our society is being built on information.  <mark>List and Dictionaries are used to collect information</mark>.  Mostly, when information is collected it is formed into patterns.  As that pattern is established you will be able collect many instances of that pattern.
- List is used to collect many instances of a pattern
- Dictionary is used to organize data patterns.
- Iteration is often used to process through lists.

To start exploring more deeply into List, Dictionary and Iteration this example will explore constructing a List of people and cars.
- As we learned above, a List is a data type: class 'list'
- A <mark>'list' data type has the method '.append(expression)'</mark> that allows you to add to the list.  A class usually has extra method to support working with its objects/instances.
- In the example below,  the expression is appended to the 'list' is the data type: class 'dict'
- At the end, you see a fairly complicated data structure.  This is a <mark>list of dictionaries</mark>, or a collection of many similar data patterns.  The output looks similar to JavaScript Object Notation (JSON), Jekyll/GitHub pages yml files, FastPages Front Matter. As discussed we will see this key/value patter often, you will be required to understand this data structure and understand the parts.  Just believe it is peasy ;) and it will become so.


```python
# Define an empty List called InfoDb
InfoDb = []

# InfoDB is a data structure with expected Keys and Values

# Append to List a Dictionary of key/values related to a person and cars
InfoDb.append({
    "FirstName": "John",
    "LastName": "Mortensen",
    "DOB": "October 21",
    "Residence": "San Diego",
    "Email": "jmortensen@powayusd.com",
    "Owns_Cars": ["2015-Fusion", "2011-Ranger", "2003-Excursion", "1997-F350", "1969-Cadillac"]
})

# Append to List a 2nd Dictionary of key/values
InfoDb.append({
    "FirstName": "Sunny",
    "LastName": "Naidu",
    "DOB": "August 2",
    "Residence": "Temecula",
    "Email": "snaidu@powayusd.com",
    "Owns_Cars": ["4Runner"]
})

# Append to List a 2nd Dictionary of key/values
InfoDb.append({
    "FirstName": "Shane",
    "LastName": "Lopez",
    "DOB": "February 27",
    "Residence": "San Diego",
    "Email": "???@powayusd.com",
    "Owns_Cars": ["2021-Insight"]
})

# Print the data structure
print(InfoDb)
```

    [{'FirstName': 'John', 'LastName': 'Mortensen', 'DOB': 'October 21', 'Residence': 'San Diego', 'Email': 'jmortensen@powayusd.com', 'Owns_Cars': ['2015-Fusion', '2011-Ranger', '2003-Excursion', '1997-F350', '1969-Cadillac']}, {'FirstName': 'Sunny', 'LastName': 'Naidu', 'DOB': 'August 2', 'Residence': 'Temecula', 'Email': 'snaidu@powayusd.com', 'Owns_Cars': ['4Runner']}, {'FirstName': 'Shane', 'LastName': 'Lopez', 'DOB': 'February 27', 'Residence': 'San Diego', 'Email': '???@powayusd.com', 'Owns_Cars': ['2021-Insight']}]


### Formatted output of List/Dictionary - for loop
Managing data in Lists and Dictionaries is for the convenience of passing the data across the internet, to applications, or preparing it to be stored into a database.  It is a great way to exchange data between programs and programmers.  Exchange of data between programs includes the data type the method/function and the format of the data type.  These concepts are key to learning how to write functions, receive, and return data.  This process is often referred to as an <mark>Application Programming Interface (API)</mark>. 

Next, we will take the stored data and output it within our notebook.  There are multiple steps to this process...
- <mark>Preparing a function to format the data</mark>, the print_data() function receives a parameter called "d_rec" short for dictionary record.  It then references different keys within [] square brackets.   
- <mark>Preparing a function to iterate through the list</mark>, the for_loop() function uses an enhanced for loop that pull record by record out of InfoDb until the list is empty.  Each time through the loop it call print_data(record), which passes the dictionary record to that function.
- Finally, you need to <mark>activate your function</mark> with the call to the defined function for_loop().  Functions are defined, not activated until they are called.  By placing for_loop() at the left margin the function is activated.


```python
# This jupyter cell has dependencies on one or more cells above

# print function: given a dictionary of InfoDb content
def print_data(d_rec):
    print(d_rec["FirstName"], d_rec["LastName"])  # using comma puts space between values
    print("\t", "Residence:", d_rec["Residence"]) # \t is a tab indent
    print("\t", "Birth Day:", d_rec["DOB"])
    print("\t", "Cars: ", end="")  # end="" make sure no return occurs
    print(", ".join(d_rec["Owns_Cars"]))  # join allows printing a string list with separator
    print()


# for loop algorithm iterates on length of InfoDb
def for_loop():
    print("For loop output\n")
    for record in InfoDb:
        print_data(record)

for_loop()
```

    For loop output
    
    John Mortensen
    	 Residence: San Diego
    	 Birth Day: October 21
    	 Cars: 2015-Fusion, 2011-Ranger, 2003-Excursion, 1997-F350, 1969-Cadillac
    
    Sunny Naidu
    	 Residence: Temecula
    	 Birth Day: August 2
    	 Cars: 4Runner
    
    Shane Lopez
    	 Residence: San Diego
    	 Birth Day: February 27
    	 Cars: 2021-Insight
    


### Alternate methods for iteration - while loop
In coding, there are usually many ways to achieve the same result.  Defined are functions illustrating using index to reference records in a list, these methods are called a "while" loop and "recursion".
- The while_loop() function contains a while loop, "while i < len(InfoDb):".  This counts through the elements in the list start at zero, and passes the record to print_data()


```python
# This jupyter cell has dependencies on one or more cells above

# while loop algorithm contains an initial n and an index incrementing statement (n += 1)
def while_loop():
    print("While loop output\n")
    i = 0
    while i < len(InfoDb):
        record = InfoDb[i]
        print_data(record)
        i += 1
    return

while_loop()
```

    While loop output
    
    John Mortensen
    	 Residence: San Diego
    	 Birth Day: October 21
    	 Cars: 2015-Fusion, 2011-Ranger, 2003-Excursion, 1997-F350, 1969-Cadillac
    
    Sunny Naidu
    	 Residence: Temecula
    	 Birth Day: August 2
    	 Cars: 4Runner
    
    Shane Lopez
    	 Residence: San Diego
    	 Birth Day: February 27
    	 Cars: 2021-Insight
    


### Calling a function repeatedly - recursion
This final technique achieves looping by calling itself repeatedly.
- recursive_loop(i) function is primed with the value 0 on its activation with "recursive_loop(0)"
- the last statement indented inside the if statement "recursive_loop(i + 1)" activates another call to the recursive_loop(i) function, each time i is increasing
- ultimately the "if i < len(InfoDb):" will evaluate to false and the program ends


```python
# This jupyter cell has dependencies on one or more cells above

# recursion algorithm loops incrementing on each call (n + 1) until exit condition is met
def recursive_loop(i):
    if i < len(InfoDb):
        record = InfoDb[i]
        print_data(record)
        recursive_loop(i + 1)
    return
    
print("Recursive loop output\n")
recursive_loop(0)
```

    Recursive loop output
    
    John Mortensen
    	 Residence: San Diego
    	 Birth Day: October 21
    	 Cars: 2015-Fusion, 2011-Ranger, 2003-Excursion, 1997-F350, 1969-Cadillac
    
    Sunny Naidu
    	 Residence: Temecula
    	 Birth Day: August 2
    	 Cars: 4Runner
    
    Shane Lopez
    	 Residence: San Diego
    	 Birth Day: February 27
    	 Cars: 2021-Insight
    


## Hacks
- Add a few records to the InfoDb
- Try to do a for loop with an index
- Pair Share code somethings creative or unique, with loops and data. Hints...
    - Would it be possible to output data in a reverse order?
    - Are there other methods that can be performed on lists?
    - Could you create new or add to dictionary data set?  Could you do it with input?
    - Make a quiz that stores in a List of Dictionaries.
