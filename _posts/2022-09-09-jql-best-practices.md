---
title: Jira JQL Best Practices for ACP Exam
description: This is a small description to the first post
date: 2022-09-01
pin: false
categories: [CORE]
tags: [jql,article]
---
**I guess many of us, Atlassian Certified Professionals, will agree that some Atlassian Jira JQL questions which we had in our ACP exams were tricky. These questions can be easier to answer, if you follow the Atlassian JQL Best Practices, which we often forget or simply do not know.**

When preparing for one of the Jira related ACP exams, for example ACP-100 or ACP-120, you should expect a few questions relating to JQL. In ACP-100 preparation topics you can find - `Topic 1: Advanced User Features; 1.1: Given a business requirement, create, translate, critique, and optimize JQL queries.`

Although you may work with JQL on a daily basis, some questions are really tricky and require more time to analyze. Do not underestimate these questions. Sometimes, even if you answer them correctly, you are not always 100% sure about that.

If you want an ACP Exam-hack from me, memorize this JQL Golden Best Practice:
>_Ask yourself:_  
>Is this JQL query easy to maintain?  
>Will anybody have to modify it when some external conditions or data change?  
>If no - that is ok, if yes - optimize it.  
{: .prompt-tip }

It does not mean that it is always possible to optimize a JQL query, because not every query needs to be shared (in shared filters or dashboards). But on the ACP Exam, expect to select only this query which does not need to be updated once created.

**Here are a few examples to illustrate it:**

**(1) Do not use individual user names, if you want to share the filter with others**

`JQL: reporter in membersOf("dev-ops-members")` - when someone is added or removed from this group, this JQL will continue to work just fine, no need to update it

`JQL: assignee = currentUser()` - if you want to share a dashboard which should work the same way for everyone, use the group or user related functions and not individual values

**(2) Do not list all the task or sub-task issue types in one query, if you do not want to select only a few of them**

`JQL: project = ABC and standardIssueTypes()` - this will select all task type issues, but not sub-tasks. Tricky question: will this also select Epics? Check it out yourself.

`JQL: project = ABC and subTaskIssueTypes()` - this will select all sub-task type issues, but not tasks and epics

**(3) In your Jira, if you create many new projects reqularly, configure project categories and use them in your JQL queries**

`JQL: category = “agile” and status = Open` - this will list all issues in status Open from all projects, current and future, associated with the category “agile”  

I hope you found these examples useful and this will bring you one step closer to your ACP Exam success.

If you want to be 100 steps closer, please consider purchasing my e-book, which aimed at Atlassian ACP Exam candiates and Jira Users.

[You will find more information here.](https://jlabnotes.com/jql-cookbook/)