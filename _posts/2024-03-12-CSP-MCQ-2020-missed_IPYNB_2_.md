---
comments: True
layout: post
title: MCQ 2020 Frequently Missed Questions
description: Questions and sample Python code to represent the most frequently missed questions on the 2020 AP Computer Science A Multiple Choice Exam.
type: hacks
courses: {'compsci': {'week': 26}}
---

## 4. Cause of overflow Error (1D, binary math) - Tara Sehdave

In a certain computer program, two positive integers are added together, resulting in an overflow error. Which of the following best explains why the error occurs?

Responses
A
The program attempted to perform an operation that is considered an undecidable problem.

B
The precision of the result is limited due to the constraints of using a floating-point representation.

C
The program can only use a fixed number of bits to represent integers; the computed sum is greater than the maximum representable value.

D
The program cannot represent integers; the integers are converted into decimal approximations, leading to rounding errors.

The correct answer is C because...

- Overflow error occurs in a computer program when adding two positive integers.
- The program uses a fixed number of bits to represent integers.
- The sum of the two integers exceeds the maximum representable value within the fixed number of bits.
- Due to this limitation, the program cannot accurately represent the result of the addition.
- As a result, an overflow error is triggered to indicate that the computed sum is beyond the representable range.


```python
# python overflow example
# as a popcorn hack (binary challenge), describe an overflow in 8 binary digits
# Add 1 to 11111111 (255)
# Subtract 1 from 00000000 (0)
# Try overflow and underflow here: https://nighthawkcoders.github.io/teacher_portfolio/c4.4/2023/09/14/javascript-binary-U2-1.html

import sys

# Maximum float
max_float = sys.float_info.max
print(f"Max float: {max_float}")

# Attempt to overflow float
overflow_float = max_float * 2
print(f"Overflow float to infinity: {overflow_float}")
```

    Max float: 1.7976931348623157e+308
    Overflow float to infinity: inf


## Popcorn Hack 1
- Binary overflow because it is confined to 8 bits but exceeds 255
- Underflow because the binary bits cannot represent negative numbers


```python
# My solution for popcorn hack
# Adding 1 to 11111111 (255) with overflow confined to 8 bits
result = (0b11111111 + 0b1) & 0b11111111
print(bin(result))  # Output: 0b00000000 (overflow)

# Subtracting 1 from 00000000 (0) with underflow confined to 8 bits
result = (0b00000000 - 0b1) & 0b11111111
print(bin(result))  # Output: 0b11111111 (underflow)
```

    0b0
    0b11111111


## 5. Inputs to Logic Circuit (2D, binary logic) - Hanlun Li

The diagram below shows a circuit composed of three logic gates. Each gate takes two inputs and produces a single output. For which of the following input values will the circuit have an output of true ?



The diagram in question shows a circuit composed of three logic gates. Each gate takes two inputs and produces a single output. <br>

For which of the following input values will the circuit have an output of true ? <br>

A) A = true,  B = true,  C = true,  D = false <br>
B) A = true,  B = false, C = false, D = true <br>
C) A = false, B = true,  C = true,  D = true <br>
D) A = false, B = false, C = true,  D = true <br>

A OR B = True, C AND D = True, and since True AND True = True, C is correct. <br>
OR gate only returns true if one of the values is true, and the AND gate returns true if both values are true. 


```python
# represent gates and circuits
# as a popcorn hack (coding challenge), create multiple new circuits and gates
# NOT, NAND, NOR, XOR, XNOR
# Create a hypothetical circuit, such as burglar alarm, decision tree for autonomous car, etc.

# OR gate
def OR_gate(A, B):
    return A or B

# AND gate
def AND_gate(A, B):
    return A and B

# Theoritical circuit representing a Car starting
# A and B could be security checks, such as key being inserted or a fob being present
# C and D could be operational checks, such as a start button being pressed and safety belt being fastened
# The enclosing AND gate ensures car only operates when both security and operational checks are met
def circuit(A, B, C, D):
    return AND_gate(OR_gate(A, B), AND_gate(C, D))

# Print truth table for circuit
print('A', 'B', 'C', 'D', "-->", 'Output')
# nesting of loops for both the True, False combination of A, B, C, D 
# this algorithm is 2 ^ 4 = 16, thus producing all 16 combinations 
# each combination terminates with the output of the circuit
for A in [False, True]:
    for B in [False, True]:
        for C in [False, True]:
            for D in [False, True]:
                print(A, B, C, D, "-->", circuit(A, B, C, D))
```

    A B C D --> Output
    False False False False --> False
    False False False True --> False
    False False True False --> False
    False False True True --> False
    False True False False --> False
    False True False True --> False
    False True True False --> False
    False True True True --> True
    True False False False --> False
    True False False True --> False
    True False True False --> False
    True False True True --> True
    True True False False --> False
    True True False True --> False
    True True True False --> False
    True True True True --> True


## Popcorn Hack 2
- New truth table using NOT and NOR gates
- There are only 8 combinations since the not gate only takes 1 argument
- Scenario
    - Light Switch where A is if there is motion
    - B is if the light is on
    - C is time of day
    - EX: There is motion --> A is True (NOT gate returns false)
        - The light is on --> B is true
        - It is 10 PM --> B is true
        - NOR gate returns true
        - Second NOR gate between false and true returns true
        - The light should remain on


```python
# NOT gate
def NOT_gate(A):
    return not A

# NOR gate
def NOR_gate(A, B):
    return not (A or B)

# Print truth table for circuit
print('A', 'B', 'C', "-->", 'Output')

# Hypothetical situation of turning on/off a light
def circuit(A, B, C):
    return NOR_gate(NOT_gate(A), NOR_gate(B, C))

for A in [False, True]:
    for B in [False, True]:
        for C in [False, True]:
            print(A, B, C, "-->", circuit(A, B, C))
```

    A B C --> Output
    False False False --> False
    False False True --> False
    False True False --> False
    False True True --> False
    True False False --> False
    True False True --> True
    True True False --> True
    True True True --> True


## 11. Color represented by binary Triplet (2D, binary) - Torin Wolff

A color in a computing application is represented by an RGB triplet that describes the amount of red, green, and blue, respectively, used to create the desired color. A selection of colors and their corresponding RGB triplets are shown in the following table. Each value is represented in decimal (base 10).

According to information in the table, what color is represented by the binary RGB triplet (11111111, 11111111, 11110000) ?

#### What is a binary triplet?
A binary triplet is a set of three binary numbers. Binary numbers are numbers that are represented by a series of 1's and 0's. Binary numbers are used in computers because they are easy to represent with electrical signals. A binary triplet is a set of three binary numbers that are used to represent a color. The first number represents the amount of red in the color, the second number represents the amount of green in the color, and the third number represents the amount of blue in the color. The numbers are represented in binary because it is easy to represent with electrical signals. The numbers are represented in a triplet because it is easy to represent with electrical signals.

#### How is a color in binary represented?
A color in binary is represented by a set of three binary numbers. The first number represents the amount of red in the color, the second number represents the amount of green in the color, and the third number represents the amount of blue in the color. The numbers are represented in binary because it is easy to represent with electrical signals. The numbers are represented in a triplet because it is easy to represent with electrical signals. An example of this would be: (01101110, 11111111, 10010110), if you converted this binary triplet to a decimal number it would be 110, 255, 150. This would be a shade of the color green.

#### How do you convert a binary triplet to a decimal number?
To convert a binary string to a decimal number you need to multiply each digit by its place value. For example, if you have the binary string 1010 you would multiply the first digit by 2^3, the second digit by 2^2, the third digit by 2^1, and the fourth digit by 2^0. This would give you the decimal number 10. To convert a binary triplet to a decimal number you need to multiply each digit by its place value. For example, if you have the binary triplet (01101110, 11111111, 10010110) you would multiply the first digit by 2^7, the second digit by 2^6, the third digit by 2^5, the fourth digit by 2^4, the fifth digit by 2^3, the sixth digit by 2^2, the seventh digit by 2^1, and the eighth digit by 2^0. This would give you the decimal number 110, 255, 150.

(0 * 2^7) + (1 * 2^6) + (1 * 2^5) + (0 * 2^4) + (1 * 2^3) + (1 * 2^2) + (1 * 2^1) + (0 * 2^0)

= 0 + 64 + 32 + 0 + 8 + 4 + 2 + 0

= 110

(insert photo)





```python
# Convert binary RGB triplet to decimal
# as a hack (binary challenge), make the rgb standard colors
# as a 2nd hack, make your favorite color pattern 

import matplotlib.pyplot as plt
import matplotlib.patches as patches

# Function to convert binary to decimal
def binary_to_decimal(binary):
    return int(binary, 2)

def plot_colors(rgb_triplets):
    # Create a figure with one subplot per RGB triplet
    fig, axs = plt.subplots(1, len(rgb_triplets), figsize=(2 * len(rgb_triplets), 2))
    
    # Ensure axs is always a list
    axs = axs if len(rgb_triplets) > 1 else [axs]

    for ax, (red_binary, green_binary, blue_binary) in zip(axs, rgb_triplets):
        # Convert to binary strings to decimal
        red_decimal = binary_to_decimal(red_binary)
        green_decimal = binary_to_decimal(green_binary)
        blue_decimal = binary_to_decimal(blue_binary)

        # Normalize number to [0, 1] range, as it is expected by matplotlib 
        red, green, blue = red_decimal/255, green_decimal/255, blue_decimal/255

        # Define a rectangle patch with the binary RGB triplet color and a black border
        rect = patches.Rectangle((0, 0), 1, 1, facecolor=(red, green, blue), edgecolor='black', linewidth=2)
        
        # Add the rectangle to the plot which shows the color 
        ax.add_patch(rect)

        # Remove axis information, we just want to see the color
        ax.axis('off')

        # Print the binary and decimal values
        print("binary:", red_binary, green_binary, blue_binary)    
        print("decimal", red_decimal, green_decimal, blue_decimal)
        print("proportion", red, green, blue)

    # Show the colors
    plt.show()

# Test the function with a list of RGB triplets
rgb_triplet = [('11111111', '11111111', '11110000')] # College Board example
plot_colors(rgb_triplet)

rgb_primary = [('11111111', '00000000', '00000000'), 
                ('11111111', '11111111', '00000000'),
                ('00000000', '00000000', '11111111')]
plot_colors(rgb_primary)
```

    binary: 11111111 11111111 11110000
    decimal 255 255 240
    proportion 1.0 1.0 0.9411764705882353



    
![png](output_10_1.png)
    


    binary: 11111111 00000000 00000000
    decimal 255 0 0
    proportion 1.0 0.0 0.0
    binary: 11111111 11111111 00000000
    decimal 255 255 0
    proportion 1.0 1.0 0.0
    binary: 00000000 00000000 11111111
    decimal 0 0 255
    proportion 0.0 0.0 1.0



    
![png](output_10_3.png)
    


## Popcorn Hack 3


```python
favorite = [('01000000', '11000000', '11110000')] # Favorite Color
plot_colors(favorite)

# Standard Color Examples
standard_colors = [('11111111', '00000000', '11111111'), 
                ('00000000', '00000000', '00000000'),
                ('11111111', '11111111', '11111111'),
                ('00000000', '11111111', '11111111'),]
plot_colors(standard_colors)
```

    binary: 01000000 11000000 11110000
    decimal 64 192 240
    proportion 0.25098039215686274 0.7529411764705882 0.9411764705882353



    
![png](output_12_1.png)
    


    binary: 11111111 00000000 11111111
    decimal 255 0 255
    proportion 1.0 0.0 1.0
    binary: 00000000 00000000 00000000
    decimal 0 0 0
    proportion 0.0 0.0 0.0
    binary: 11111111 11111111 11111111
    decimal 255 255 255
    proportion 1.0 1.0 1.0
    binary: 00000000 11111111 11111111
    decimal 0 255 255
    proportion 0.0 1.0 1.0



    
![png](output_12_3.png)
    


## 50. Reasonable time algorithms (1D, Big O) - Vance Reynolds 

Consider the following algorithms. Each algorithm operates on a list containing n elements, where n is a very large integer.

- An algorithm that accesses each element in the list twice
- An algorithm that accesses each element in the list n times
- An algorithm that accesses only the first 10 elements in the list, regardless of the size of the list


Which of the algorithms run in reasonable time?
Answer D is correct because in order for an algorithm to run in reasonable time, it must take a number of steps less than or equal to a polynomial function.
 
- Algorithm I accesses elements times (twice for each of n elements), which is considered in time. 
- Algorithm II accesses elements (n times for each of n elements), which is in reasonable time. 
- Algorithm III accesses 10 elements, which is in reasonable time.

Simple Explainations:

Unreasonable time: Algorithms with exponential or factorial efficiencies are examples of algorithms that run in an unreasonable amount of time.

Reasonable time: Algorithms with a polynomial efficiency or lower (constant, linear, square, cube, etc.) are said to run in a reasonable amount of time.


```python
# Big O notation example algorithms
# as a popcorn hack (coding challenge), scale list of size by factor of 10 and measure the times
# what do you think about college board's notion of reasonable time for an algorithm?
# as a 2nd hack, create a slow algorithm and measure its time, which are considered slow algorithms... 
#   O(n^3) which is three nested loops 
#   O(2^n) which is a recursive algorithm with two recursive calls

import time

# O(n) Algorithm that accesses each element in the list twice, 2 * n times 
def algorithm_2n(lst):
    for i in lst:
        pass
    for i in lst:
        pass

# O(n^2) Algorithm that accesses each element in the list n times, n * n times
def algorithm_nSquared(lst):
    for i in lst:
        for j in lst:
            pass

# O(1) Algorithm that accesses only the first 10 elements in the list, 10 * 1 is constant 
def algorithm_10times(lst):
    for i in lst[:10]:
        pass

# Create a large list
n = 1000
lst = list(range(n))

# Measure the time taken by algorithm1
start = time.time()
algorithm_2n(lst)
end = time.time()
print(f"Algorithm 2 * N took {(end - start)*1000:.2f} milliseconds")

# Measure the time taken by algorithm2
start = time.time()
algorithm_nSquared(lst)
end = time.time()
print(f"Algorithm N^2 took {(end - start)*1000:.2f} milliseconds")

# Measure the time taken by algorithm3
start = time.time()
algorithm_10times(lst)
end = time.time()
print(f"Algorithm 10 times took {(end - start)*1000:.2f} milliseconds")
```

    Algorithm 2 * N took 0.06 milliseconds
    Algorithm N^2 took 7.62 milliseconds
    Algorithm 10 times took 0.03 milliseconds


## Popcorn Hack 4
- Recursion
    - O(2^n) time complexity because it calls itself within 2 times
- O(n^4)
    - 4 nested loops


```python
def recursion(num):
    if num <= 1:
        return num
    return recursion(num - 1) - recursion(num - 2) 

start = time.time()
recursion(30)
end = time.time()

print(f"Recursion times took {(end - start)*1000:.2f} milliseconds")

def powerOfFour(lst):
    n = len(lst)
    for i in range(n):
        pass
        for j in range(n):
            pass
            for k in range(n):
                pass
                for l in range(n):
                    pass


n = 100
lst = list(range(n))
start = time.time()
powerOfFour(lst)
end = time.time()

print(f"O(n^4) times took {(end - start)*1000:.2f} milliseconds")
```

    Recursion times took 180.93 milliseconds
    O(n^4) times took 922.20 milliseconds



## 56. Compare execution times of tow version (1D analysis) - Kayden Le

An online game collects data about each player’s performance in the game. A program is used to analyze the data to make predictions about how players will perform in a new version of the game.

The procedure GetPrediction (idNum) returns a predicted score for the player with ID number idNum. Assume that all predicted scores are positive. The GetPrediction procedure takes approximately 1 minute to return a result. All other operations happen nearly instantaneously.

Two versions of the program are shown below.

Which of the following best compares the execution times of the two versions of the program?

Version I calls the GetPrediction procedure once for each element of idList, or four times total. Since each call requires 1 minute of execution time, version I requires approximately 4 minutes to execute. Version II calls the GetPrediction procedure twice for each element of idList, and then again in the final display statement. This results in the procedure being called nine times, requiring approximately 9 minutes of execution time.

Both versions aim to achieve the same result, which is to find and display the highest predicted score among the players in idList. However, Version I directly updates the highest score (topScore), while Version II updates the ID of the player with the highest score (topID) and then retrieves the predicted score for that player. Version II essentially avoids calling GetPrediction multiple times for the same ID.

The answer: D - Version II requires approximately 5 more minutes to execute than version I



```python
# Simulate the time taken by GetPrediction, calling an expensive operation twice is slow
# as a popcorn hack (coding challenge)
#  measure the time to calulate fibonacci sequence at small and large numbers
# `this task will require a code layout and a time measurement
#  there are fast ways and slow ways to calculate fibonacci sequence`

'''
The GetPrediction function is a simulation stand-in for a potentially expensive operation.
In a real-world scenario, this could be a call to a;
   - machine learning model
   - a database query
   - fibonacci sequence at a large number
   - or any other algorithm that takes a significant amount of time.
'''
def GetPrediction(idNum):
    # time.sleep(60)  # Commented out to avoid actual delay
    return idNum * 10  # Dummy prediction

# Version I: makes a single call to GetPrediction for each element in idList
def version_I(idList):
    start = time.time()  # Start timer
    topScore = 0
    for idNum in idList:
        predictedScore = GetPrediction(idNum) # calls GetPrediction once
        if predictedScore > topScore: 
            topScore = predictedScore # stores the topScore to avoid calling GetPrediction again
    end = time.time()  # End timer
    print(f"Version I took {end - start + len(idList) * 60:.2f} simulated seconds")  # Add simulated delay

# Version II: makes two calls to GetPrediction for each element in idList
def version_II(idList):
    start = time.time()  # Start timer
    topID = idList[0]
    for idNum in idList:
        if GetPrediction(idNum) > GetPrediction(topID): # calls GetPrediction twice
            topID = idNum # stores the topID, but still calls GetPrediction with topID again
    end = time.time()  # End timer
    print(f"Version II took {end - start + len(idList) * 2 * 60 + 60:.2f} simulated seconds")  # Add simulated delay

# Test the functions
idList = [1, 2, 3, 4] # Small list
# idList = [i for i in range(1, 1000)] # Large list using list comprehension
version_I(idList)
version_II(idList)
```

    Version I took 240.00 simulated seconds
    Version II took 540.00 simulated seconds


## Popcorn Hack 5
- Slow recursion uses recursion to get the answer
- Fast recursion uses memoization
    - Stores the values so it is very quick
    - O(n) run time vs O(2^n) of slow fibonacci
    - <a href="https://www.youtube.com/watch?v=P8Xa2BitN3I">Youtube Video</a>


```python
def slowFibonacci(num):
    if num <= 1:
        return num
    else:
        return slowFibonacci(num-1) + slowFibonacci(num-2)

start = time.time()
smallSlow = slowFibonacci(5)
end = time.time()
print(f"Slow Fibonacci with a small number took {end - start:.2f} seconds")

#start = time.time()
#smallSlow = slowFibonacci(40)
#end = time.time()
#print(f"Slow Fibonacci with a large number took {end - start:.2f} seconds")

def fastFibonacci(n, computed = {0: 0, 1: 1}):
    if n not in computed:
        computed[n] = fastFibonacci(n-1, computed) + fastFibonacci(n-2, computed)
    return computed[n]

start = time.time()
fast = fastFibonacci(1000)
end = time.time()
print(f"Fast Fibonacci with a large number took {end - start:.2f} seconds")
```

    Slow Fibonacci with a small number took 0.00 seconds
    Fast Fibonacci with a large number took 0.01 seconds


## 64. Error with multiplication using repeated addition (4C algorithms and programs) - Abdullah Khanani

The following procedure is intended to return the value of x times y, where x and y are integers. Multiplication is implemented using repeated additions.

For which of the following procedure calls does the procedure NOT return the intended value?

Select two answers.

### Question 64

PROCEDURE Multiply [x,y]
    count <-- 0
    result <-- 0
    REPEAT UNTIL [count ≥ y]
        result <-- result + x
        count <-- count + 1
    RETURN result

### Question

#### For which of the following procedure calls does the procedure NOT return the intended value? Select two answers.

### Options

A. Multiply 2,5
B. Multiply 2,-5
C. Multiply -2,5
D. Multiply -2,-5

### Answered

A and C

### Correct Answer

B and D

### Explanation

For procedures A, the procedure repeatedly adds 2 to result five times, resulting in the intended product 10. Vice versa for C. IF you want to return the result and get a correct answer, multiplying 2,-5 and -2,-5 will give you the wanted result. The following procedure is intended to return the value of x times y, where x and y are integers. Multiplication is implemented using repeated additions. A and C fit these requirements.


```python
# flawed multiply function
# as a popcorn hack (coding challenge), fix the multiply function to work with negative numbers

'''
As you can see, the function fails when y is negative,
because the while loop condition count < y is never true in these cases.
'''

def multiply(x, y):
    count = 0
    result = 0
    while count < y:
        result += x
        count += 1
    return result

# Test cases
print(multiply(2, 5))  # Expected output: 10
print(multiply(2, -5))  # Expected output: -10, Actual output: 0
print(multiply(-2, 5))  # Expected output: -10
print(multiply(-2, -5))  # Expected output: 10, Actual output: 0
```

    10
    0
    -10
    0


## Popcorn Hack 6
- Fixed using abs and multiplying by the sign at the end


```python
def multiply(x, y):
    count = 0 
    result = 0
    while count < abs(y):
        result += x
        count += 1
    return result * y/abs(y)

print(multiply(2, 5))  # Expected output: 10
print(multiply(2, -5))  # Expected output: -10, Actual output: 0
print(multiply(-2, 5))  # Expected output: -10
print(multiply(-2, -5))  # Expected output: 10, Actual output: 0
```

    10.0
    -10.0
    -10.0
    10.0


## 65. Call to concat and substring (4B string operations) - Ameer Hussain

A program contains the following procedures for string manipulation.

Which of the following can be used to store the string "jackalope" in the string variable animal ?

Select two answers.

### Correct Answer C:
animal ← Substring(“jackrabbit”, 1, 4) extracts “jack” from “jackrabbit”. animal ← Concat(animal, “a”) appends “a” to “jack”, resulting in “jacka”. animal ← Concat(animal, Substring(“antelope”, 5, 4)) extracts “lope” from “antelope” and appends it to “jacka”, resulting in “jackalope”.

### Incorrect Answer D:
animal ← Substring(“jackrabbit”, 1, 4) extracts “jack” from “jackrabbit”. animal ← Concat(animal, “a”) appends “a” to “jack”, resulting in “jacka”. animal ← Concat(Substring(“antelope”, 5, 4), animal) is slightly misleading because it extracts “lope” from “antelope” and should prepend it to “jacka”, but this is incorrect because it would result in “lopejacka”. the operations in Answer D would not result in “jackalope”.

animal ← Substring(“antelope”, 5, 4) would assign the substring “lope” from “antelope” to the variable animal. animal ← Concat(“a”, animal) would then prepend “a” to “lope”, resulting in “alope”. animal ← Concat(Substring(“jackrabbit”, 1, 4), animal) would take the substring “jack” from “jackrabbit” and then concatenate it with “alope” resulting in “jackalope”.

The process outlined in Answer B does indeed result in the string “jackalope”, with the first step isolating “lope” from “antelope”, the second step creating the string “alope” by prepending “a” to “lope”, and the final step creating the correct string by prepending “jack” to “alope”.

animal ← Substring(“antelope”, 5, 4) would assign the substring “lope” from “antelope” to the variable animal. animal ← Concat(“a”, animal) would then prepend “a” to “lope”, resulting in “alope”. animal ← Concat(Substring(“jackrabbit”, 1, 4), animal) would take the substring “jack” from “jackrabbit” and then concatenate it with “alope” resulting in “jackalope”.

The process outlined in Answer B does indeed result in the string “jackalope”, with the first step isolating “lope” from “antelope”, the second step creating the string “alope” by prepending “a” to “lope”, and the final step creating the correct string by prepending “jack” to “alope”.


```python
# Incorrect Answer D
# as a popcorn hack (binary challenge), create string and concatenation options for A, B, C
 
animal = "jackrabbit"[0:4]  # Substring("jackrabbit", 1, 4)
animal += "a"  # Concat(animal, "a")
animal = "antelope"[4:8] + animal  # Concat(Substring("antelope", 5, 4), animal)
print(animal)  # Outputs: lopejacka
```

    lopejacka


## Popcorn Hack 7


```python
# A is already done above

# B --> this prints jackalope as intended
animal = "antelope"[4:8]
animal = "a" + animal
animal = "jackrabbit"[0:4] + animal
print(animal)

# C --> this prints jackalope as well
animal = "jackrabbit"[0:4]
animal = animal + "a"
animal = animal + "antelope"[4:8]
print(animal)

```

    jackalope
    jackalope



```python
def binary_search(arr, target):
    low = 0
    high = len(arr) - 1

    while low <= high:
        mid = (low + high) // 2
        if arr[mid] == target:
            return mid
        elif arr[mid] < target:
            low = mid + 1
        else:
            high = mid - 1

    return -1  # Target not found

# Example usage
arr = [2, 4, 6, 8, 10, 12, 14, 16, 18, 20]
target = 12
result = binary_search(arr, target)
if result != -1:
    print(f"Element {target} is found at index {result}")
else:
    print(f"Element {target} is not found in the array")

```

    Element 12 is found at index 5



```python
import nltk
from nltk.sentiment import SentimentIntensityAnalyzer

# Download the vader_lexicon
nltk.download('vader_lexicon')

# Initialize the VADER sentiment intensity analyzer
sia = SentimentIntensityAnalyzer()

# Provide a string to analyze
text = ""

# Get the sentiment scores
sentiment = sia.polarity_scores(text)

print(sentiment)
```

    {'neg': 0.0, 'neu': 1.0, 'pos': 0.0, 'compound': 0.0}


    [nltk_data] Downloading package vader_lexicon to
    [nltk_data]     /home/trevor/nltk_data...
    [nltk_data]   Package vader_lexicon is already up-to-date!

