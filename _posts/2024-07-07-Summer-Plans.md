---
comments: True
layout: post
title: Summer Project plans
description: Here are the plans for the summer project I plan to do
type: plans
courses: {'compsci': {'week': 30}}
---

## Project Idea
In my tutoring organization, 1Must, most tutors usually have the same kids every Saturday session. However, many tutors miss meetings due to scheduling conflicts, so there needs to be a better way for other tutors to pick off where they left off. My idea is to create an application which allows for notes on specific kids and tracking of school progress. This would not only create a better system but also open up opportunities for sponsors sinec there would be concrete evidence that we help kids improve in school.

## Features:
- User authentication: different logins for students, tutors, and developers
    - Use jwt token to accomplish this
- Student profiles: this would be the responsibilities of the tutors to fill out academic history, learning preferences, and areas of improvement. Possibly add photos and personal notes to help tutors remember each student
    - Database work. This could be done with individual columns for each topic I discussed above
- Session notes: highlight what was covered after each session including the name of unit that student was on before they finished for the day
- Progress tracking: record grades, test scores, and other academic metrics to monitor improvement. Hopefully add graphs and other visuals for this
    - This is a more difficult aspect because we can't directly access their grades and it's not fair to force them to reveal them if they don't want to. Perhaps something like unit tests similar to Khan Academy could also show academic growth.
- Communication: in app messaging for tutors and students. This would allow for updates/annoucements from the organization
    - Not everyone has access to iMessages which makes commication poor sometimes. I think this could be a possible solution, although it would require a lot of testing.
- Homework help center (would have to talk to organizer): outside of school students can leave questions about homework in a discussion board style for tutors to give answers to when they have time
- Chatbot (low priority, long term): a chatbot for students to use outside of 1Must hours where they can use it for easy homework help
    - I would have to explore NLP which I'm not familiar with at this moment, which is why this is lowest priority.

## Long-term Vision:
- Create a mobile version of this web applcication for easier access and convenience
- Expand the application and maybe offer it to other tutoring organizations
[Canva](https://www.canva.com/design/DAGKZf48sU0/9Fy5iuFcVwwl8Fu_y9adMw/edit)