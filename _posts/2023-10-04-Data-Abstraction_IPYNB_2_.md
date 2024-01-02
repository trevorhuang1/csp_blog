---
layout: post
toc: True
title: Data Abstraction
description: Popcorn hacks during the data abstraction lesson as well as the homework
type: hacks
comments: True
courses: {'compsci': {'week': 7}}
---

## Popcorn Hack 1


```python
name = "Trevor Huang"
print(name)
```

    Trevor Huang


## Popcorn Hack 2


```python
name = "Trevor Huang"
age = 15
likesCats = True

print(name)
print(age)
print(likesCats)
```

    Trevor Huang
    15
    True


## Popcorn Hack 3


```python
person1 = "Ian Wu"
person2 = "Jason Guan"
idol = "Kyle Liang"

person2 = person1
idol = person2
print(idol)
```

    Ian Wu


## Popcorn Hack 4


```python
list = ["Robotics", "XC", "Brawl Stars", "Engineering", "Ian Wu"]
print(list[1])
```

    XC


## Popcorn Hack 5


```python
import json
menu = ["French Fries", "Burgers", "Milkshake", "Soft drink"]
json_obj = json.dumps(menu)
print(json_obj)
```

    ["French Fries", "Burgers", "Milkshake", "Soft drink"]


# Homework


```python
# Making 2 Dictionaries
people = {
    "Trevor": 15,
    "Toby": 17,
    "Ian": 15,
    "Tarun": 14,
    "Maria Branyas": 116
}

negative = {
    "Bobby": -232,
    "Tristan": -1,
    "Mark": -12
}

def oldest_person(people):
    # Setting up the variables
    oldest = 0
    oldest_ppl = ""
    for person, age in people.items():
        ## IF the person's age is greater than all of the previous ages, then replace oldest with their age
        if age > oldest:
            oldest = age
            oldest_ppl = person
        ## if the person's age is less than 0, then tell the person negative ages don't exist. I needed to use an elif statement because an else statement would run between toby and ian and count them as negative because toby > ian
        elif age < 0:
            return "You can't have negative ages..."
    return str(oldest_ppl) + " is the oldest person at " + str(oldest) + " years old"

# Code so that I can print both at the same time
result1 = oldest_person(people)
result2 = oldest_person(negative)

print(result1)
print(result2)
```

    Maria Branyas is the oldest person at 116 years old
    You can't have negative ages...

