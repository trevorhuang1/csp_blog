---
comments: True
layout: post
title: Final Project Plans
description: The plans for our algorithm
type: hacks
courses: {'compsci': {'week': 30}}
---

## Overall Project Plans
For the final night at the museum project, we plan to create an algorithm that sorts anime series by popularity, ratings, number of episodes, genre, and how recently it was released. This will be done by initially parsing the web for a list of anime, then appending it to an array. Then, the array of anime titles will be iterated through, then using a google trends api it will check how many times each anime was searched for in the past year to determine their relevancy/popularity. The value for how many times each anime was searched for will be set as a dictionary value, then, using a sorting function, the dictionary will be ordered from most searches to least searches. Furthermore, for rating popularity, utilizing beautiful soup, a web parser, we can parse an anime site to search for ratings, then utilizing a dictionary we can sort by highest rating. This process can be repeated for genre, and the date of release to filter the results out. Or, there can be an array full of arrays to store the values for each anime. 

## Work Distribution:
- Matthew:
    - Webscraping to get the top 100 japanese shows
- Aashray Reddy:
    - Backend model
    - Frontend work after the model is finished
- Aashray Rajagopalan:
    - Frontend work
    - Help Kyle with the quicksort algorithm
- Kyle:
    - Quicksort algorithm
        - Sort by relevancy, rating, and website user ratings
- Trevor:
    - Frontend api
    - With with Aashray Reddy on the backend model


> Example:

anime_data = [
    ['Title', 'Release Date', 'Genre', 'Rating'],
    ['Attack on Titan', '2013-04-07', 'Action, Fantasy', 8.9],
    ['Death Note', '2006-10-04', 'Mystery, Thriller', 9.0],
    ['My Hero Academia', '2016-04-03', 'Action, Comedy', 8.4],
    ['Demon Slayer', '2019-04-06', 'Action, Fantasy', 8.7],
    ['One Punch Man', '2015-10-05', 'Action, Comedy', 8.8]
]
This is what the database rows and columns would probably look like.

## Requirements
Loops (Algorithmic)
Show specific example of building a List using List Comprehension. Show examples of processing a list using conventional and for each methods.

Sorting / Searching (Algorithmic)
Show examples of sorting and searching using the backend of your project.. FYI, SQLAlchemy allows filtered selections and sorting. Additionally, you have sorting options discussed in tech talk.
- As a group, we discussed using either quicksort or merge sort. The TV shows are already sorted by ratings, however we need to sort by release date and website fan ratings as well.

<iframe width="560" height="315" src="https://www.youtube.com/embed/WprjBK0p6rw" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

[Watch the QuickSort Visual Explanation](https://www.youtube.com/watch?v=WprjBK0p6rw)


Big(O)
Illustrate Space and Time complexity used in your Sorting / Searching algorithm.
- We did some research into time complexity and both merge sort and quicksort have O(log(n)) time complexity on average, but quicksort has a O(n^2) time complexity in the worst case scenerio
- However looking into the space complexity, quicksort has O(log(n)) complexity for auxillary space and O(n) for non in place
- Merge sort has a consistent O(n) space time complexity
- Since we are planning to go up to 500 tv shows, we decided that quicksort would be best because of its space complexity

2D Iteration
Show examples of code that use 2D iteration. This can be anywhere in your code where you are using rows and columns.
```
anime_data = [
    ['Title', 'Release Date', 'Genre', 'Rating'],
    ['Attack on Titan', '2013-04-07', 'Action, Fantasy', 8.9],
    ['Death Note', '2006-10-04', 'Mystery, Thriller', 9.0],
    ['My Hero Academia', '2016-04-03', 'Action, Comedy', 8.4],
    ['Demon Slayer', '2019-04-06', 'Action, Fantasy', 8.7],
    ['One Punch Man', '2015-10-05', 'Action, Comedy', 8.8]
]
```

Deployment (Full Stack)
A complete deployment illustration multiple people using and updating your Full Stack Web Application simultaneously.
- The user will also be able to have their own ratings on each show and can sort it by those ratings. If the user wants to update their ratings, a PUT request will be sent to the SQL backend and their ratings will be updated.

<script src="https://utteranc.es/client.js"
        repo="{{ site.github_username }}/{{ site.github_repo | default: site.baseurl | remove: "/" }}"
        issue-term="title"
        label="blogpost-comment"
        theme="github-light"
        crossorigin="anonymous"
        async>
</script>