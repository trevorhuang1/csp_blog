---

---

---
toc: true
comments: true
layout: post
title: Week 3
description: Youtube Search Engine
type: hacks
courses: { compsci: {week: 3} }
---


```python
# Run this to install the necessary libraries
#!pip install google-api-python-client

# Import google library
from googleapiclient.discovery import build

# Defines my API key
api_key = 'AIzaSyBqBQADCfvhljqeB_G0pK6PR9bSRN6A-VM'
youtube = build('youtube', 'v3', developerKey=api_key)

# Take user input for search terms
search_terms = input("Enter search terms (comma-separated): ").split(',')

# Iterate through the search terms
for term in search_terms:
    term = term.strip()  # Remove leading/trailing spaces
    # Search for videos
    search_response = youtube.search().list(
        q=term,
        type='video',
        part='id,snippet',
        maxResults=1
    ).execute()

    # Get the first result
    video = search_response['items'][0]

    # Extract video details
    video_id = video['id']['videoId']
    title = video['snippet']['title']
    description = video['snippet']['description']

    # Print video details
    print(f'Title: {title}')
    print(f'Description: {description}')
    print(f'Video URL: https://www.youtube.com/watch?v={video_id}\n')
```

    Enter search terms (comma-separated): ian wu
    Title: (Yiruma) River flows in you - Ian Wu
    Description: A beautiful song arranged by Sungha Jung , hope you like it : ) Follow me on Youtube and My Fanpage ...
    Video URL: https://www.youtube.com/watch?v=bmDmoLE6RuI
    



```python

```
