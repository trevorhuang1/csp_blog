---
title: Final Individual Review
comments: true
description: Trevor's final individual review for CPT.
type: tangibles
layout: post
courses: { compsci: {week: 24} }
---

# Project overview
Let 'em Cook! is our own twist on a childhood favorite game of Little Alchemy. Instead of combining elements, we combine foods! We also have a leaderboard and trading features between users as well as a shop

# My feature
My feature is the trading feature between users. When a user wants to trade with another, they must first send them a friend request and wait for the other user to accept before sending items to each other. This is done through the sqlite.db which contains every user's list of friends and friend requests

# College Board Requirements:
- Instructions for input from one of the following: the user (including user actions that trigger events), a device, an online data stream, a file
- Use of at least one list (or other collection type) to represent a collection of data that is stored and used to manage program complexity and help fulfill the program’s purpose
- At least one procedure that contributes to the program's intended purpose, where you have defined the procedure's name, the return type (if necessary), and one or more parameters
- An algorithm that includes sequencing, selection, and iteration that is in the body of the selected procedure
- Calls to your student-developed procedure
- Instructions for output (tactile, audible, visual, or textual) based on input and program functionality

## Instructions for input from one of the following: the user (including user actions that trigger events), a device, an online data stream, a file
My part allows you to send a recipe to a friend using a form and then a button to send/accept friend requests
![Image](https://files.catbox.moe/4iqmus.png)

## Use of at least one list (or other collection type) to represent a collection of data that is stored and used to manage program complexity and help fulfill the program’s purpose
Lists of a user's friends in the sqlite.db allow for sending of items between friends
![Image](https://files.catbox.moe/qtr0zw.png)

## At least one procedure that contributes to the program's intended purpose, where you have defined the procedure's name, the return type (if necessary), and one or more parameters
parameter(self), returns if error, name(delete)
![Image](https://files.catbox.moe/1dzgby.png)

## An algorithm that includes sequencing, selection, and iteration that is in the body of the selected procedure
The algorithmn first confirms the user did not send to themself before adding the friend request (sequencing), it selects the correct user based on the sender in the body (selection) after iterating throughout all of the users
![Image](https://files.catbox.moe/75z56w.png)

## Calls to your student-developed procedure
Frontend fetch request to backend calls to the delete function
![Image](https://files.catbox.moe/3v9efb.png)

## Instructions for output
Code to generate the data tables
![Image](https://files.catbox.moe/u9wmdy.png)

## Key commits:
- <a href="https://github.com/trevorhuang1/lmc-frontend/commit/b768a1cf9b960d3ec8fb0aa223dfbf7b7bc59ee5">Database fetch request</a> This code helps create the tables by fetch request (GET) by iterating through the user's list of friends, items, and all of the users and then appending to the correct lists to be explained
- <a href="https://github.com/trevorhuang1/lmc-backend/commit/9baf6ce9288412a0147ffb00ce55e3f67f6cd8ea">Code logic for accepting friend request</a> This backend code handles what happens when the frontend sends a DELETE request when clicking the button to accept friend request.
- <a href="https://github.com/trevorhuang1/lmc-frontend/pulls?q=is%3Apr+is%3Aclosed+author%3Atrevorhuang1">Link to frontend pull requests</a>
- <a href="https://github.com/trevorhuang1/lmc-backend/pulls?q=is%3Apr+is%3Aclosed+author%3Atrevorhuang1+">Link to backend pull requests</a>

<script src="https://utteranc.es/client.js"
        repo="trevorhuang1/csp_blog"
        issue-term="pathname"
        theme="github-light"
        crossorigin="anonymous"
        async>
</script>