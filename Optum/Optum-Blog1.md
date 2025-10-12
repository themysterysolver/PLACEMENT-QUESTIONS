# Optum

- **Year:** 2025
- **Type:** Placement  
- **Role:** Full stack developer
---

## Online Assessment Overview  

- The test was conducted in the `codeSignal` the same platform used by **`VISA`**.
- The test duration was `70mins`,unlike the other DSA question in OA this was different.If u are reading this blog for DSA q,then you can skip it out.Since it's going to be about web dev.
- We logged into to the codesignal then we completed the basic procdure then we were asked to do choose any one among the given tech stacks,
  - Django + Angular
  - Java spring boot + MyBatis
  - Express + React + sequelize
  - C# ASP.NET + React

- Now came the fun part,we were given 4 requirements/features to implement.
- They gave us the initial DB structre,readme,schemas,(frontend)react app,backend logic. It was a well designed file structre for front-end and back-end.
- Now we have to implemeent the above features in the tech stack choosen above.
- The IDE was very user friendly,it was similar to `VS code`. They had terminal to run commands.
- They also had an `AI bot` whihc the game changer here. They told us we can use how muchever we want to use this bot to achieve the end goal. It's name is `COSMO`,it 
was a really strong AI assitance.
- Topics and things you should know,
  - basics of react,nodesjs and app structre
  - How to work on terminal and bash
  - curl,tree,npm,sudo commands
  - How to CRUD,how it works.
  - How to debug!

---

## Question 1: *Implement the features!*  
**Description:**  

### Context

- This assessment consists of a single question with multiple tiers of requirements. It will be graded every time you click submit, and your highest scoring attempt will become your final score saved in your assessment report.
You will get points for a partial solution, so make sure to submit your code even if you don't finish everything.
Last but not least, this is an Al co-piloted assessment and Cosmo (found in the left-hand-side menu) is here to help you get things done faster. You are expected to make use of your Al co-pilot as much as you need to.

### Introduction

- You are given a fully functional application called Conduit, a simple blogging website that's similar to sites like medium.com. The application follows a modern web stack, with an Express.js backend using Sequelize ORM providing a RESTful API and a React frontend consuming this API. This application allows users to:
- Sign up and log in using authentication
- Create, edit, and delete articles with support for markdown formatting
- Comment on anicies and engage in discussions
- Follow other users to see then amcies in a personalized feed
- Favorite articles to save the for
- Filter articles by tags to discover trending topics.
- We've populated the database with 2 users and 7 articles which are owned by the Author user

```
authorexample.com 1234
teallengexample.com-121234
```

#### Requirements

- You will be implementing four progressive features, each building on the previous one:

### 📌Tier 1: Add Read-only API Endpoint for Article View Count

- Implement a simple counter that tracks how many times each article has been viewed.

<br>

**Acceptance Criteria**
- Add a viewCount integer attribute to the Article model with default value of 0.
- Create an API route called /articles/:slug/viewed to increment the counter when an article is viewed
- The viewCount field should be returned with Article data
- Backend only: No Ul changes required for this tier

### 📌Tier 2: Display Article View Count in UI

- Build on Tier 1 functionality by showing the view count to users.

<br>

**Acceptance Criteria**
- Every time an article is viewed, call the API created when working on Tier 1 requirements to update the value by 1
Add a simple icon and display the viewCount value (e.g..
42 views" below the article title.
- Frontend only. No backend changes required for this tier.

### 📌Tier 3: Add Article Categories
- Implement a Article categories separate from tags

<br>

**Acceptance Criteria**

- Create a new Category model with attributes for name and description.
- Define an association between Article and Category models.
- Seed the Category table with some categories (Travel, Animals, etc)
- Create an API endpoints to list all cafegories.
- Update the article creation/edit form in the Ul to fetch the categories and include a category dropdown.

### 📌Tier 4: Implement Article Recommendations

- Create a simple recommendation endpoint based on categories, tags, and viewCount Display recommendations with the full Article view

<br>

**Acceptance Criteria**

- Create a new API endpoint that retums 3-5 recommended articles based on
  -  Articles in the same category
  - Articles sharing the most tags with the current article
  - Sort the list by most viewed (via viewCount)
- Add a 'Recommended Reading" section to the bottom of the article page in the UI
- Display the recommended articles with their tities and author names.

---

### Thought Process  

- First I read the problem statement and doing this without an aissitance would be impossible.So I did the below thing,
  - I am aware of a command called `tree` , I used this to `COSMO` for better directory understanding and the files it should change.
  - I then prompted the entire requirements and asked it to give logics and code for each tier in parts.
  - For backend I tested it using `curl`.
  - Unfortunately localhost wasn't working so I wasn't able to check my `UI` part. (my friends faced the same issue)

> PS: Always have the server running,use multiple terminals,if u chnage anything on DB restart it.


---



// Your solution here
> ***ANYONE CAN CONRIBUTE! LET'S BUILD A COMMUNITY!!***
