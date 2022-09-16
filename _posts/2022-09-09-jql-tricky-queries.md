---
title: Tricky JQL queries for ACP Exam candiates
description: A few less popular JQL queries to test your knowledge
date: 2022-09-16 09:00:00 +0200
pin: false
categories: [JQL]
tags: [acp]
---
When preparing for one of the ACP exams, it is worth reviewing your knowledge by evaluating what you already know. This will boost your confidence and will decrease the risk of panic when you get an 'out-of-the-blue' JQL related question.

**Here are a few examples of tricky JQL queries:**

`due >= "0"` 
You can use 0 as the equivalent to function now(). You can put any value in the quote-marks and it will work just fine. Example: due >= "-1000d"

`duedate < endOfWeek(-1)`  
Although you may think that endOfWeek is always in the future (oh yes, weekend), this may not always be true in Jira. This query will show you all the issues that had their due date before (this is tricky) this week started. If I said "before the end of previous week" this would be too obvious.

`assignee not IN (NULL, currentUser())`  
If you think using NULL is not allowed in JQL queries you are wrong. You can use NULL and EMPTY interchangably.

`assignee IN membersOf ("jira-administrators","jira-software-users")`  
Use groups to make JQL queries more adaptable to rotation of team members. When someone leaves or joins the company, the query will still work for current and new team members.

`status changed to 10001`  
In some cases (eg. in ScriptRunner scripts) it is better to use object id's and not names. Especially in larger Jira instances, due to various reason names of statuses, resolutions or custom fields can be spelled exactly the same. In this example, you are looking for issues which were transitioned from any status to status "Done".

`cf[10011] ~ "preparation"`  
This query will return all issues where a custom field Epic Name contains the word "preparation". Some fields that are by default in Jira are not treated as system fields. Epic Name field is one of them.

`project in projectsWhereUserHasPermission("Assign Issues")`  
`project in projectsWhereUserHasRole("Developers")`  
This query will help you find issues in these projects, where you have specific permission or role in projects. You can also use it to check if you have permission or role in specific projects where you do not have administration rights. Example: project in projectsWhereUserHasRole("Developers") AND project = ABC. In this example, if you see issues this means that you have a role Developers in project ABC.

I hope you found these examples useful and this will bring you one step closer to your ACP Exam success.

If you want to learn 100 more JQL examples, please consider purchasing my e-book, which helps Atlassian ACP Exam candiates and Jira Users to master JQL language.

[You will find more information about JQL here.](https://jlabnotes.com/jql-cookbook/)