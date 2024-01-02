---

---

---
toc: true
comments: true
layout: post
title: Week 3
description: Math Quiz
type: hacks
courses: { compsci: {week: 3} }
---


```python
#!pip install emoji
from emoji import emojize
import random

# Define a dictionary with emojis as keys and movies as values
emojis_movies = {
    "🦁👑": "The Lion King",
    "🌊🐟": "Finding Nemo",
    "🧙‍♂️📚": "Harry Potter",
    "🍫🏭": "Willy Wonka and the Chocolate Factory",
    "🟢👽": "Toy Story",
    "🦸‍♂️🦇": "Batman",
}

def select_random_emoji():
    emoji = random.choice(list(emojis_movies.keys()))
    return emoji

def play_game():
    emoji = select_random_emoji()
    print("Guess the movie represented by these emojis:")
    print(emoji)
    guess = input("Your guess: ")

    if guess == emojis_movies[emoji]:
        print("Congratulations! You guessed it right.")
    else:
        print(f"Sorry, the correct answer was {emojis_movies[emoji]}.")
    
    return guess

# Add a while loop to repeat the game
while True:
    guess = play_game()
    play_again = input("Do you want to play again? (yes/no): ")
    if play_again.lower() != 'yes':
        break
```

    Guess the movie represented by these emojis:
    🧙‍♂️📚
    Your guess: Harry Potter
    Congratulations! You guessed it right.
    Do you want to play again? (yes/no): yes
    Guess the movie represented by these emojis:
    🧙‍♂️📚
    Your guess: Hrryn potter
    Sorry, the correct answer was Harry Potter.



```python

```
