---
comments: True
layout: post
title: Data Structures Writeup
description: Individual review regarding CPT project & machine learning project
type: tangibles
courses: {'compsci': {'week': 28}}
---

## Collections
- Python Model Code and SQLite Database
- The database table has name, uid, their encrypted password, items they have, DOB, favorite food, role, points, friends, and current friend requests
![image](https://github.com/trevorhuang1/csp_blog/assets/118785933/8e29e824-ae74-4b6f-a5ff-a781307bdfdb)
- There are some default users which are created in the users model. They get default items, a set uid & username, and data in other columns
![image](https://github.com/trevorhuang1/csp_blog/assets/118785933/1218a30e-a595-4464-96c4-d587bd38e7ca)

## Lists and Dictionaries
- Use of lists and dictionaries in the api code
- Get request where python list of all users are being pulled and returned as json
![image](https://github.com/trevorhuang1/csp_blog/assets/118785933/419fdd13-e644-40bd-ba83-05c1e274641b)

- Two distinct examples of dictionaries
- Use of .uid and .role keys to access the user Flay's dictionary
![image](https://github.com/trevorhuang1/csp_blog/assets/118785933/b1230c3c-88f4-41c7-85d2-fe062595a8ce)

## API and JSON
- API code for all CRUD operations.
![image](https://github.com/trevorhuang1/csp_blog/assets/118785933/b7c1bdba-952f-49a3-a839-e6c2a10af466)
- Series of if statements, loops, and returns to make sure that the POST request sent for login is valid. It returns specific errors based on how the request sent did not satisfy the login requirements
![image](https://github.com/trevorhuang1/csp_blog/assets/118785933/abd9c496-a02f-424a-9dfd-02f46d00eaed)
- Postman URL and body for the POST request
![image](https://github.com/trevorhuang1/csp_blog/assets/118785933/6aed471e-1ed3-47d4-bf07-089609ece932)
- Postman URL and body for the GET request
![image](https://github.com/trevorhuang1/csp_blog/assets/118785933/04dbcf12-55b9-4cee-8376-80a80a02b06c)
- Above screenshots have the 200 success already
- 400 error after missing password for authentication POST request
![image](https://github.com/trevorhuang1/csp_blog/assets/118785933/1fa01095-71e4-432a-b8ce-5e5ed826b9c3)
- 400 error after trying to edit a user who does not exist
![image](https://github.com/trevorhuang1/csp_blog/assets/118785933/40e66ed5-b530-4a08-bd71-86f52ef8d4b5)

## Frontend
- Body of the POST request being done during authentication
![Image](https://github.com/nighthawkcoders/teacher_portfolio/assets/118785933/1e9692e4-db44-4dee-97b0-97c6f6f3741d)
- JSON object being returned from the GET request in the leaderboard
![image](https://github.com/trevorhuang1/csp_blog/assets/118785933/5b5fb10c-6e12-46ed-9328-42a38162e478)
- Body of the PUT request being sent
![image](https://github.com/trevorhuang1/csp_blog/assets/118785933/56afb234-0c74-4ea0-ad11-f4bb37ceeb32)
- After the GET request, the JSON data being returned is sorted into tables with a for loop
![image](https://github.com/trevorhuang1/csp_blog/assets/118785933/8ef50997-bee0-4636-8b49-5cdee528c062)
- Redirect to main page once if there are no errors and the login is properly authenticate
![Image](https://github.com/nighthawkcoders/teacher_portfolio/assets/118785933/ce0ffcd8-c234-461b-ab0b-259758d2cba7)
- Below are all the different redirects based on the error received. For example, a 404 page redirects to its own page, 401 has its own, etc
![Image](https://github.com/nighthawkcoders/teacher_portfolio/assets/118785933/5b6ebeed-4cd7-45c3-ae69-34633090a41b)