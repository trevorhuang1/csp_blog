---
comments: True
layout: post
title: Error Checking
description: A program used to check if another program has any running errors.
type: hacks
courses: {'compsci': {'week': 4}}
---

```python
# Cannot concatenate int and string types, will give error
def function_with_error():
    number = 123
    string = '123'
    print(number + string)

# function will print 123123
def function_without_error():
    string = '123'
    string2 = '123'
    print(string + string2)

def test_function(func):
    print('--------------------------------------------------')
    print('Testing function: ' + func)
    # try tests function, if error occurs will run code in except
    try: 
        eval(func)
    except:
        # print error occured if error occurs
        print('error occured while testing ' + func)
    else:
        print('No errors occured in ' + func + '!')
        print('Output is above.')

test_function('function_with_error()')
test_function('function_without_error()')
```

    --------------------------------------------------
    Testing function: function_with_error()
    error occured while testing function_with_error()
    --------------------------------------------------
    Testing function: function_without_error()
    123123
    No errors occured in function_without_error()!
    Output is above.


This is nice and all, being able to tell when an error occurs, but knowing that an error exists isn't very useful, we would find that out either way from attempting to run it. A nice step would be the print the type of error that occurs. This is done as shown below


```python
# Cannot concatenate int and string types, will give error
def function_with_error():
    number = 123
    string = '123'
    print(number + string)

# function will print 123123
def function_with_error2():
    number = 12
    number2 = 0
    print (number / number2)

def test_function(func):
    print('--------------------------------------------------')
    print('Testing function: ' + func)
    # try tests function, if error occurs will run code in except
    try: 
        eval(func)
    # store exception type in variable error
    except Exception as error:
        # print error occured if error occurs
        print('The following error occured while testing ' + func + ': ')
        print(error)
    else:
        print('No errors occured in ' + func + '!')
        print('Output is above.')

test_function('function_with_error()')
test_function('function_with_error2()')
```

    --------------------------------------------------
    Testing function: function_with_error()
    The following error occured while testing function_with_error(): 
    unsupported operand type(s) for +: 'int' and 'str'
    --------------------------------------------------
    Testing function: function_with_error2()
    The following error occured while testing function_with_error2(): 
    division by zero


Try and catch statements check errors well, but what about if and else statements? I decided to redo Kyle's code but this time with a larger emphasis on if and else statements to show how they work to catch errors. These work fine but I prefer try and except because they are a bit cleaner when catching errors as they require less lines of code.


```python
# Defines the function
def get_valid_number():
    while True:
        user_input = input("Please enter an integer between 1 and 100: ")
            # Checks if the input is a number with isdigit
        if user_input.isdigit():
            number = int(user_input)
            # if between 1 and 100 then return the value
            if 1 <= number <= 100:
                return number
            # checks if too large        
            elif number > 100:
                print("Invalid input. Please enter a number between 1-100")
            # checks if too small
            elif number < 1:
                print("Invalid input. Please enter a number between 1-100")
        # checks if negative
        elif user_input[0] == "-":
            print("Invalid input. Please enter a number between 1-100")
        # otherwise it is not a number
        else:
            print("Please enter an integer")

answer = get_valid_number()
# if the end result is a number, then the code states it is valid
if isinstance(answer, int):
    print(f"You entered a valid number: {answer}")
```

    Please enter an integer between 1 and 100: -2
    Invalid input. Please enter a number between 1-100
    Please enter an integer between 1 and 100: 424
    Invalid input. Please enter a number between 1-100
    Please enter an integer between 1 and 100: 22
    You entered a valid number: 22

