---
comments: True
layout: post
title: Simulations - Student Teach
description: Student Lesson
type: hacks
courses: {'compsci': {'week': 10}}
---

## Simulations 


> A simulation is the use of a computer software to represent the dynamic responses of one system by the behaviour of another system modeled after it. A simulation uses a mathematical descriptions, or models, of a real system in the form of a computer program.

![simulation](https://www.simscale.com/wp-content/uploads/2022/11/dron-quadcopter-simulation.png)

## College Board Essential Knowledge

> Simulation are absractions of more complex objects or phenomena for a specific purpose 

- Mimic Real World Events
- Allows investigation of phenomenons without contraints of the Real World
- Helps you draw accurate inferences

> Simulations utilize varying sets of values to reflect the changings states of a phenomenon

- simulations can simplfly things for functionality
- Simulations can contain bias from real world elements, that were chosen to be included or excluded

> Simulations work best when the real world experemnts are too impractical or time consuming. For example, simulating how different cars behave when they crash, would be much better than crashng actual cars in the real world, which would be expensive and dangerous.

<a href="https://ibb.co/f4jKcBY"><img src="https://i.ibb.co/NZck4Q6/simulations-vs-experiments.png" alt="simulations-vs-experiments" border="0"></a>


## Rolling the Dice

<a href="https://ibb.co/PGBhfPD"><img src="https://i.ibb.co/XxmsvKY/craps-rolling-seven-7.jpg" alt="craps-rolling-seven-7" border="0"></a>

> Simulating something like a dice roll in real life would require accounting for things like: weight, flaws in design, thrust, and gravity.
- KEEP IT SIMPLE! just use a random-number generator! Ignore minor causes of variablility

## Random

- "Random" is a built-in python function that allow the user to draw a random value from a set range.
- A Random Number Generator (RNG) is a common simulation that selects a random value from an array.
- The following code cell utilizes "random" to select a number from 1 to 100.


```python
#imports random module so we can use it in our code
import random

#sets variable random_number as a random number between 1 and 100
random_number = random.randint(1, 100)

#Printing out your random Number
print(random_number)
```

    42


## More complex usage of "random"; Coin Toss Simulation


```python
import random
def flip_coin():
    return random.choice(["Heads", "Tails"])
def coin_flip_simulation(num_flips):
    heads_count = 0
    tails_count = 0
    for _ in range(num_flips):
        result = flip_coin()
        if result == "Heads":
            heads_count += 1
        else:
            tails_count += 1
    return heads_count, tails_count
if __name__ == "__main__":
    num_flips = 1000  #This is the number of coin flips you want to simulate
    heads, tails = coin_flip_simulation(num_flips)
    print("Number of Heads: "+ str(heads))
    print("Number of Tails: " + str(tails))
    print("Heads Probability: "+ str({heads / num_flips}))
    print("Tails Probability: "+ str({tails / num_flips}))
```

    Number of Heads: 492
    Number of Tails: 508
    Heads Probability: {0.492}
    Tails Probability: {0.508}


## Popcorn Hack #1

Utilize "random" to create a basic simulation of a rolling TWO dice. Print the sum of both dice rolls. Remember to practice good syntax when naming your variables. 


```python
import random

#Code, Code, Code
dice1 = random.randint(1, 6)
dice2 = random.randint(1, 6)
print("You rolled",dice1,"and",dice2)
print("Your score is:",(dice1+dice2))
```

    You rolled 6 and 6
    Your score is: 12


## Algorithms
>Simulations often utilize algorithms and equations to perform tasks because simulations don't always have the same output
- the output of a simulation depends on the input

>An algorithm is a finite sequence of instructions used to solve problems or perform computations. 
- commonly used alongside functions


## Example Algorithm in a function


```python
#Defining Function
def algorithm(input):
    
    #Manipulating input and preparing it for the output.  
    output = input+2
    
    #Return the output
    return output

#Call the Function to start the algorithm
algorithm(5)
    
```




    7



## Mathematics
- Math can also prove to be very useful in certain types of situations.
- Commonly used along with Algorithms when simulating various things

![math](https://pythontutorialhome.files.wordpress.com/2019/05/image-2.png)


## Popcorn Hack #2

Simulate how long an object will fall for using an algorithm, with user-inputed variables for height dropped. Use the following formula as a reference.

![gravity ](https://hepweb.ucsd.edu/ph110b/110b_notes/img272.png)

- t = time (output)
- h = height dropped from (input)
- g = constant (given)


```python
import math

# Constant, Acceleration due to gravity (m/s^2)
G = 9.81 

def simulation(height_dropped):
    # Code Code Code
    m = 2*height_dropped
    t = math.sqrt(m/G)
    print("The object fell for",t,"seconds")
    
simulation(5)
```

    The object fell for 1.0096375546923044 seconds


# Using Loops in Simulations

> For loops can also be used in simulations
- They can simulate events that repeat but don't always have the same output



```python
# Example For Loop

#Creating For Loop to repeat 4 times
for i in range(4):
    
    #Action that happens inside for loop
    print("This is run number: " + str(i))
    
```

    This is run number: 0
    This is run number: 1
    This is run number: 2
    This is run number: 3


## Popcorn Hack #3

You are gambling addic. 

Each session you roll 2 dice.

If your dice roll is greater than or equal to 9 you win the session.

If you win over 5 sessions, you win the jackpot.

Simulate your odds to predict if you will hit the jackpot (how many rounds did you win?) using a for loop and random.



```python
import random

#Code, Code, Code
wins = 0

for i in range(100):
    dice1 = random.randint(1, 6)
    dice2 = random.randint(1, 6)
    total = dice1 + dice2
    if total >= 9:
        print("You won!")
        wins += 1
    else:
        print("You lost!")
    if wins == 5:
        break

if wins == 5:
    print("You won the jackpot!")
    print(f"You won {wins} out of {i} sessions")
```

    You lost!
    You lost!
    You lost!
    You won!
    You won!
    You lost!
    You lost!
    You lost!
    You lost!
    You lost!
    You won!
    You lost!
    You lost!
    You lost!
    You lost!
    You lost!
    You lost!
    You won!
    You lost!
    You won!
    You won the jackpot!
    You won 5 out of 19 sessions


## BONUS POPCORN HACK
> Welcome to Flight Simulator! Your goal is to complete a Python program that simulates a flight We've set up some initial values for altitude, speed, and fuel. Your task is to update these values to make the flight more realistic.

- Your mission:

1. Use random changes to simulate altitude, speed, and fuel changes.
2. Keep the flight going until it reaches 10,000 feet or runs out of fuel.
3. Make sure altitude, speed, and fuel remain realistic.


```python
import random

# Initial parameters
altitude = 0
speed = 0
fuel = 100

print("Welcome to Flight Simulator!")

# Code Code Code
while True:
    altitude += 100
    speed += 15
    fuel -= 2
    
    if altitude == 10000:
        print(f"We just hit 10,000 feet!")
        print(f"The current speed in miles per hour is {speed}")
        print(f"The amount of fuel left is {fuel}%")
        break
    if fuel == 0:
        print(f"We ran out of fuel. Good luck LOL")
        print(f"The current speed in miles per hour is {speed}")
        print(f"The altitude is {altitude}")
        break
```

    Welcome to Flight Simulator!
    We ran out of fuel. Good luck LOL
    The current speed in miles per hour is 750
    The altitude is 5000


## QUIZ TIME

- Quick true or false quiz, whoever answers this correctly(raise your hand) gets a piece of gum or a dinero. 
<hr>

> T or F    
- A simulation will always have the same result.
> T or F    
- A simulation investigates a phenomenom without real-world constraints of time, money, or safety.
> T or F    
- A simulation has results which are more accurate than an experiment,
> T or F    
- A simulation can model real-worl events that are not practical for experiments


```python
#code
False
True
False
True
```

## Homework hack 1


```python
import random

def simulate_game():
    money = 100
    wins = 0

    for i in range(100):
        roll = random.randint(1, 6) + random.randint(1, 6)
        print(f"You rolled {roll}")
        if roll <= 3:
            money -= 70
            print(f"You lost $70. You have {money} left")
        elif 3 < roll < 6:
            money -= 40
            print(f"You lost $40. You have {money} left")
        elif 6 <= roll < 9:
            money += 20
            wins += 1
            print(f"You won $20! You have {money} left")
        elif roll >= 9:
            wins += 1
            print(f"You won $50! You have {money} left")
        if wins == 5:
            money += 100
            print(f"Jackpot! You won $100! You have {money} left")
            wins = 0
            

simulate_game()
```

    You rolled 6
    You won $20! You have 120 left
    You rolled 6
    You won $20! You have 140 left
    You rolled 7
    You won $20! You have 160 left
    You rolled 10
    You won $50! You have 160 left
    You rolled 8
    You won $20! You have 180 left
    Jackpot! You won $100! You have 280 left
    You rolled 12
    You won $50! You have 280 left
    You rolled 7
    You won $20! You have 300 left
    You rolled 6
    You won $20! You have 320 left
    You rolled 8
    You won $20! You have 340 left
    You rolled 9
    You won $50! You have 340 left
    Jackpot! You won $100! You have 440 left
    You rolled 4
    You lost $40. You have 400 left
    You rolled 4
    You lost $40. You have 360 left
    You rolled 4
    You lost $40. You have 320 left
    You rolled 7
    You won $20! You have 340 left
    You rolled 3
    You lost $70. You have 270 left
    You rolled 7
    You won $20! You have 290 left
    You rolled 8
    You won $20! You have 310 left
    You rolled 11
    You won $50! You have 310 left
    You rolled 8
    You won $20! You have 330 left
    Jackpot! You won $100! You have 430 left
    You rolled 12
    You won $50! You have 430 left
    You rolled 5
    You lost $40. You have 390 left
    You rolled 2
    You lost $70. You have 320 left
    You rolled 7
    You won $20! You have 340 left
    You rolled 6
    You won $20! You have 360 left
    You rolled 9
    You won $50! You have 360 left
    You rolled 5
    You lost $40. You have 320 left
    You rolled 10
    You won $50! You have 320 left
    Jackpot! You won $100! You have 420 left
    You rolled 6
    You won $20! You have 440 left
    You rolled 7
    You won $20! You have 460 left
    You rolled 8
    You won $20! You have 480 left
    You rolled 2
    You lost $70. You have 410 left
    You rolled 5
    You lost $40. You have 370 left
    You rolled 6
    You won $20! You have 390 left
    You rolled 3
    You lost $70. You have 320 left
    You rolled 7
    You won $20! You have 340 left
    Jackpot! You won $100! You have 440 left
    You rolled 3
    You lost $70. You have 370 left
    You rolled 8
    You won $20! You have 390 left
    You rolled 5
    You lost $40. You have 350 left
    You rolled 7
    You won $20! You have 370 left
    You rolled 7
    You won $20! You have 390 left
    You rolled 5
    You lost $40. You have 350 left
    You rolled 12
    You won $50! You have 350 left
    You rolled 5
    You lost $40. You have 310 left
    You rolled 7
    You won $20! You have 330 left
    Jackpot! You won $100! You have 430 left
    You rolled 8
    You won $20! You have 450 left
    You rolled 7
    You won $20! You have 470 left
    You rolled 5
    You lost $40. You have 430 left
    You rolled 11
    You won $50! You have 430 left
    You rolled 4
    You lost $40. You have 390 left
    You rolled 6
    You won $20! You have 410 left
    You rolled 9
    You won $50! You have 410 left
    Jackpot! You won $100! You have 510 left
    You rolled 4
    You lost $40. You have 470 left
    You rolled 5
    You lost $40. You have 430 left
    You rolled 8
    You won $20! You have 450 left
    You rolled 3
    You lost $70. You have 380 left
    You rolled 6
    You won $20! You have 400 left
    You rolled 11
    You won $50! You have 400 left
    You rolled 8
    You won $20! You have 420 left
    You rolled 10
    You won $50! You have 420 left
    Jackpot! You won $100! You have 520 left
    You rolled 9
    You won $50! You have 520 left
    You rolled 7
    You won $20! You have 540 left
    You rolled 9
    You won $50! You have 540 left
    You rolled 9
    You won $50! You have 540 left
    You rolled 9
    You won $50! You have 540 left
    Jackpot! You won $100! You have 640 left
    You rolled 3
    You lost $70. You have 570 left
    You rolled 9
    You won $50! You have 570 left
    You rolled 11
    You won $50! You have 570 left
    You rolled 3
    You lost $70. You have 500 left
    You rolled 9
    You won $50! You have 500 left
    You rolled 9
    You won $50! You have 500 left
    You rolled 8
    You won $20! You have 520 left
    Jackpot! You won $100! You have 620 left
    You rolled 5
    You lost $40. You have 580 left
    You rolled 7
    You won $20! You have 600 left
    You rolled 10
    You won $50! You have 600 left
    You rolled 7
    You won $20! You have 620 left
    You rolled 5
    You lost $40. You have 580 left
    You rolled 6
    You won $20! You have 600 left
    You rolled 6
    You won $20! You have 620 left
    Jackpot! You won $100! You have 720 left
    You rolled 4
    You lost $40. You have 680 left
    You rolled 8
    You won $20! You have 700 left
    You rolled 3
    You lost $70. You have 630 left
    You rolled 4
    You lost $40. You have 590 left
    You rolled 5
    You lost $40. You have 550 left
    You rolled 11
    You won $50! You have 550 left
    You rolled 10
    You won $50! You have 550 left
    You rolled 4
    You lost $40. You have 510 left
    You rolled 7
    You won $20! You have 530 left
    You rolled 10
    You won $50! You have 530 left
    Jackpot! You won $100! You have 630 left
    You rolled 6
    You won $20! You have 650 left
    You rolled 5
    You lost $40. You have 610 left
    You rolled 4
    You lost $40. You have 570 left
    You rolled 11
    You won $50! You have 570 left
    You rolled 12
    You won $50! You have 570 left
    You rolled 8
    You won $20! You have 590 left
    You rolled 10
    You won $50! You have 590 left
    Jackpot! You won $100! You have 690 left
    You rolled 9
    You won $50! You have 690 left
    You rolled 8
    You won $20! You have 710 left
    You rolled 7
    You won $20! You have 730 left
    You rolled 11
    You won $50! You have 730 left
    You rolled 6
    You won $20! You have 750 left
    Jackpot! You won $100! You have 850 left


## Homework hack 2


```python
# Initial parameters
speed = 6  # Initial speed
acceleration = 2  # Acceleration rate in m/s^2
deceleration = 1  # Deceleration rate in m/s^2
max_speed = 60  # Maximum speed in m/s
distance = 0  # Initial distance
time = 0  # Initial time

#Code Code Code
def simulation(speed, acceleration, deceleration, max_speed, distance, time):
    while distance < 1000 and speed >= 5:
        time += 1
        if time <= 10:
            speed += acceleration
            distance += speed
            
            print(f"Time:",time)
            print(f"Speed:",speed)
            print(f"Distance:",distance)
        else:
            speed -= deceleration
            distance += speed
            
            print(f"Time:",time)
            print(f"Speed:",speed)
            print(f"Distance:",distance)
        if distance >= 1000:
            break
            
simulation(speed, acceleration, deceleration, max_speed, distance, time)
```

    Time: 1
    Speed: 8
    Distance: 8
    Time: 2
    Speed: 10
    Distance: 18
    Time: 3
    Speed: 12
    Distance: 30
    Time: 4
    Speed: 14
    Distance: 44
    Time: 5
    Speed: 16
    Distance: 60
    Time: 6
    Speed: 18
    Distance: 78
    Time: 7
    Speed: 20
    Distance: 98
    Time: 8
    Speed: 22
    Distance: 120
    Time: 9
    Speed: 24
    Distance: 144
    Time: 10
    Speed: 26
    Distance: 170
    Time: 11
    Speed: 25
    Distance: 195
    Time: 12
    Speed: 24
    Distance: 219
    Time: 13
    Speed: 23
    Distance: 242
    Time: 14
    Speed: 22
    Distance: 264
    Time: 15
    Speed: 21
    Distance: 285
    Time: 16
    Speed: 20
    Distance: 305
    Time: 17
    Speed: 19
    Distance: 324
    Time: 18
    Speed: 18
    Distance: 342
    Time: 19
    Speed: 17
    Distance: 359
    Time: 20
    Speed: 16
    Distance: 375
    Time: 21
    Speed: 15
    Distance: 390
    Time: 22
    Speed: 14
    Distance: 404
    Time: 23
    Speed: 13
    Distance: 417
    Time: 24
    Speed: 12
    Distance: 429
    Time: 25
    Speed: 11
    Distance: 440
    Time: 26
    Speed: 10
    Distance: 450
    Time: 27
    Speed: 9
    Distance: 459
    Time: 28
    Speed: 8
    Distance: 467
    Time: 29
    Speed: 7
    Distance: 474
    Time: 30
    Speed: 6
    Distance: 480
    Time: 31
    Speed: 5
    Distance: 485
    Time: 32
    Speed: 4
    Distance: 489

