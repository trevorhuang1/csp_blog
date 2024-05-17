---
comments: True
layout: post
title: Written Response Practice Exam
description: My attempt at previous year's AP exam FRQs
type: hacks
courses: {'compsci': {'week': 28}}
---

- All three of the FRQs require me to upload a file with comments, so I'll leave link to the code which applies to all of the FRQs

## 2023 FRQ 1
### Describe one piece of documentation that would be appropriate to include with or in your program. Describe the intended purpose of this documentation by identifying who would use it and what they would do with it.
- A README/instruction manuals for players who are just starting out would be beneficial to teach them how to send items to each other. This would foster collaboration between users and allow veteran players to help new players and increase the amount of entertainment they get from the game.

### (a) Consider the first iteration statement included in the Procedure section of your Personalized Project Reference. Describe the condition(s) that will cause the body of the iteration statement to execute at least once.
- TgenerateTable(testUser)
- This call with the argument testUser would test to see if the testUser has any friends or items to trade with others since the user id "testUser" is being used as the argument for the currently logged in user. This is crucial to the program functionality because it ensures that only the items, friends, and friend requests of "testUser" are being displayed in the table as shown in the video for "testUser" to then use as a way to engage in sending items or accepting friend requests. Whether or not the precedure works as expected could be easily checked by comparing the data shown in the table compared to the actual data stored in the backend SQLite database. 

### (c) Consider the list identified in the List section of your Personalized Project Reference. Explain how you would need to adjust this part of your program if the list was not included in your code.
- In the list identified in the List section of the personalized project reference, "user = User.query.all()" fetches all of the records from the "User" model in the database and stores it in as a list in the variable user. Each object in the list represents a single row in the "User" model database which is each individual user and the data associated with them. This each user in the list is iterated through to find which object matches the current user. Without this list, every single user would have to be compared to the current user's user id (uid) with an individual if statement which would cause the program to be significantly lengthier and harder to scale with increasing users.

## 2023 FRQ 2
### Explain how you used or could have used feedback, testing, or reflection in the development of your program.
- "Let 'em cook" is a baking game centered around combining items together to create new ones -- similar to the popular game Little Alchemy. I worked on this project with 5 other people and my personal part was the trading feature which encourages collaboration between users and allows more experienced players to help newer players start out by giving them items that they currently possess. Throughout this project, I made sure to practice incremental development by running the code regularly when a change was made so that errors could be caught early on as new chunks of code was added to the working program. Additionally, I benefitted significantly from feedback from both teammates who guided me on how they wanted to project to look and also from live reviews with my teacher to make sure that I was staying on schedule and receiving advice on the code logic and game mechanics.

### (a) Consider the first conditional statement included in the Procedure section of your Personalized Project Reference. Write an equivalent Boolean expression for this conditional statement.
- The first if statement in the procedure section which is crucial to the functionality of the code is the if statement that checks if the current user matches any of the users fetched by the frontend from the backend. An equivalent statemtn would be "curr_uid == user" which would return either true or false.

### (b) Consider the procedure identified in part (i) of the Procedure section of your Personalized Project Reference. Identify a strategy, other than using test cases, that you can use to test the correctness of your procedure. Describe how you would use this strategy.
- 

### (c) Consider the procedure identified in part (i) of the Procedure section of your Personalized Project Reference. Procedures are often used to organize larger problems into subproblems or smaller tasks. Identify the subproblem being solved or task that is being accomplished by your procedure. Explain how the procedure is used to accomplish the overall functionality of your program.
- The procedure shown in the Personalized Project Reference is used to dynamically generate tables based on all the users who currently have an account on the game, the current user's friends, all their items, and all their friend requests. The precedure "generateTable(curr_uid)" is used to generate this table is divided into subproblems within the for loops after the conditional "user.uid == curr_uid" returns true. These for loops add to lists of friends, trade items, and friend requests to populate the rows of the table first which creates the entire table after the procedure has been run. This helps with the overall functionailty of the program by allowing the user to view availible people to send friend requests to, accept their friend requests, and also see which items they can trade to others which would not be possible if they did not have a table to view this information.