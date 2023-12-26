---
title: Tricky JQL questions for ACP Exam candiates
description: 10 simulated queistions for the ACP exams
date: 2022-12-26 09:00:00 +0200
pin: false
categories: [JQL]
tags: [acp,jql]
---
## Introduction  
Below you will find 10 rather difficult examples of how the Atlassian Certified Professional Exam questions may look like. Below the questions there are answers with detailed explanations.
Please note: These questions are only simulations and are not taken from any real ACP exam papers.

## Questions

### Question 1
User John contacted you about a problem with his Teamwork dashboard. His login in Jira is ‘john.doe’. On this dashboard John can see a gadget ‘Filter Results’ based on the following JQL query:  
`project = TRE and resolution = Done`  

John reports to you that he cannot see any issues in the gadget but all his team members, when they use the same dashboard, can see 5 tasks.

_What is the cause of this problem?_  
**A.** John has no access to the gadget and one of his team members should share the entire dashboard with John so the gadget will be visible  
**B.** John should copy the dashboard, save his private version, and then update the query to see the issues:
`project = TRE and resolution = Done and assignee = john.doe`  
**C.**	John does not have the ‘Browse Projects’ permission in project TRE  
**D.** 	John should request help from Jira Administrator who should enable the dashboard for him  
 
### Question 2
Inspect the JQL query shown below:  
`project = DBRA AND updatedDate > startOfDay(-1) 
AND updatedDate < endOfDay(-1) OR updated < endOfDay()`  

_What will be the outcome of this query?_  
**A.** The outcome will be an error. There is no `updatedDate` field in Jira  
**B.** The outcome will be all issues from project DBRA that were updated today  
**C.** The outcome will be all issues from project DBRA updated yesterday (the last 24 hours)  
**D.** The outcome will be all issues in this Jira instance

### Question 3
Jenny wanted to create the simplest possible JQL query which she can use to list all the tasks that she needs to do by Friday every week. She would like to share this query with other team members belonging to group Developers (jira-team-developers) so they can use it for their tasks list as well.  

_Which JQL query satisfies her requirements?_  
**A.**	`status = "To Do" AND assignee = "jenny.smith" AND due <= EndOfWeek()`  
**B.**	`assignee = currentUser() AND resolution is NULL AND due <= EndOfWeek()`  
**C.**	`statusCategory = "To Do" AND assignee = "jenny.smith" AND due <= EndOfWeek(1w)`  
**D.**	`statusCategory = "To Do" AND assignee = currentUser AND assignee in membersOf ("jira-team-developers" AND due <= EndOfWeek()`

###	Question 4
A user requested you to help her in creating a filter for her team’s dashboard, to be used in one of dashboard’s gadgets. Her team is participating in a few projects categorized as software – the Jira project keys as follows (ABA, ABB, ABC, ABD, ABF, BDA).  
This user would like to see all issues that were rejected by the Quality Assurance Team last week and which did not change its status since then. This JQL needs to be as simple as possible.  

_Which JQL query would you recommend to this user?_
**A.**	`project IN (ABA, ABB, ABC, ABD, ABF, BDA) AND status = Rejected BEFORE EndOfWeek(-1)`  
**B.**	`project IN (ABA, ABB, ABC, ABD, ABF, BDA) AND status CHANGED TO Rejected DURING (startOfWeek(-1), endOfWeek(-1)) AND status = Rejected`  
**C.**	`category = "software" AND status CHANGED TO Rejected DURING (startOfWeek(-1), endOfWeek(-1)) AND status = Rejected`  
**D.**	`category = "software" AND status CHANGED TO Rejected DURING (startOfWeek(-1), endOfWeek(-1))`  

### Question 5
A user Mel Smith (username: mel.smith) works in one Jira project called “TEMPS”.
Mel needs a JQL saved filter which should help her team members in their work. She wants to list issues that meet the requirements which are listed below:  
1.	Issues were assigned to a viewing user but now are assigned to somebody else
2.	Issues that were created by a user executing the query

_Which JQL query will satisfy Mel’s requirements?_  
**A.**	`assignee WAS currentUser() AND assignee != currentUser() AND created = currentUser() AND project = TEMPS`  
**B.**	`assignee NOT IN currentUser() AND assignee != currentUser() AND creator = mel.smith`  
**C.**	`assignee != currentUser() AND assignee WAS currentUser() AND creator IS NOT currentUser()`  
**D.**	`project = TEMPS AND assignee WAS currentUser() AND assignee != currentUser() AND creator = currentUser()`  

### Question 6
Betty created a JQL query which she shares with her team located in London and Chicago:  
`project = DBA AND type = Story AND created >= startOfDay() AND status = resolved`  

_What can you say about his JQL query?_
**A.** This query is overcomplicated and should be simplified  
**B.** This query will give different results depending on user profile settings  
**C.** This query contains the keyword ‘type’ which is a reserved operator in Jira.  
**D.** Status names should be in quotation marks  

### Question 7
In your Jira instance, there is a custom field, type label, called ‘Variables’.  
A user has requested from you a new JQL query with the following requirement: “I would like to see all unassigned issues from a filter "TEMPUS" which my team is using, where the 'Variables' field value equals: Ready. Unfortunately, due to bad Jira administration practices, there is another custom field called Variables and you need to avoid selecting the wrong custom field.”  

_Which JQL query will return the needed results:_  
**A.**	`filterName = TEMPUS AND status = Unassigned AND Variables = Ready`  
**B.**	`filter = TEMPUS AND status = Unassigned AND cf[10240] = Ready`  
**C.**	`filterName = "TEMPUS" AND assignee IS NULL AND "Variables" = Ready`  
**D.**	`filter = "TEMPUS" AND assignee IS EMPTY AND cf[10240] = Ready`  
**E.**	`filter = TEMPUS AND assignee = Unassigned AND cf[10240] = Ready`  

### Question 8
Two project managers with their user id: “jwollar” and “ewartes” want to be notified once every week about issues they are watching in Jira, where their name is mentioned in comments. They only want to know about the issues where they have access to these issues. 

_How will you satisfy this requirement?_  

**A.**	Use JQL:  
`watcher = currentUser() AND comment ~ currentUser()`  
and create a shared filter to which each project manager can subscribe to  
**B.**	Use JQL:  
`projects in projectsWhereUserHasPermission("Browse Projects") AND watcher in (jwollar, ewartes)`  
**C.**	Use JQL:  
`project in projectsWhereUserHasPermission("Browse Issues") AND watcher ~ currentUser() AND comment ~ currentUser()`  
and create a shared filter to which each project manager can subscribe to  
**D.**	Use JQL:  
`project in projectsWhereUserHasPermission("Browse Issues") AND watcher = currentUser() AND currentUser() IN comments`   
and create a shared filter to which each project manager can subscribe to  

### Question 9
Rebeca is a software developer who works in Jira Software. She wants to create a private filter where she will see all her overdue issues, which she cannot complete because they are blocked by others. 

_Select the JQL query which satisfies this requirement._  
**A.**	`projectCategory = "software" AND due < startOfDay() AND status = Blocked`  
**B.**	`due < startOfDay() AND resolution = Unresolved AND issueLinkType = "is blocked by"`  
**C.**	`category = "software" AND due < startOfDay() AND resolution = Unresolved`  
**D.**	`category = software AND due < startOfDay() AND issueLinkType = "is blocked by"`  

### Question 10
Out of 5 JQL queries below, only one is correct. Identify this query.  
**A.**	`duedate < endOfMonth("+1q")`  
**B.**	`assignee in membersOf("dev-group","ops-group")`  
**C.**	`issue in issueHistory() AND issuetype IN standardIssueTypes()`  
**D.**	`project = WORK AND project = TEST`  
**E.**	`summary = "Task for Jenny"`  


## Answers

### Answer (1):
A is not correct. Sharing the dashboard with John is not needed. He has access to the dashboard but cannot see the tasks.  
B is not correct. Creating the dashboard with this JQL will not help  
C is correct. Browse permission is needed to see tasks from a project in Jira.  
D is not correct. There is no such thing in Jira as enabling the dashboard.

### Answer (2):
A is not correct – ‘updatedDate’ is an alias name for field ‘updated’. This query will not produce and error  
B is not correct  
C is not correct. This would have been correct without the second part of the query, after the OR operator  
D is correct. The query part after the operator OR is responsible for listing all Jira issues. In this case the first part of the query joined by the operators ‘AND’ does not influence the JQL outcome.  

### Answer (3):
A is not correct. The results will be limited only to one status name and one user. There can be many other statuses in other workflows and other team members will not see their issues.  
B is correct. This is the most simple and universal JQL to get a list of tasks that are due by the end of current Week. You can use NULL and EMPTY interchangeably.  
C is not correct. StatusCategory will not show the tasks that are already in progress. Also, the function EndOfWeek(1w) shows the Saturday next week. Apart from that, limiting the assignee to one person does not satisfy the requirements   
D is not correct. ‘MembersOf’ is not needed and the ‘currentUser’ does not have the needed brackets

### Answer (4):
A is not correct. You cannot use the predicate BEFORE in this way  
B is not correct. The JQL query will work and will give the desired results. However, it is not as simple as possible and is not flexible. If a new project is added to category ‘software’, this query will not list the issues from this new project  
C is correct. It uses the project field ‘category’ and is therefore simplified and adaptive.  
D is not correct. This query will show all issues that changed to status Rejected but may not be in this status anymore. The requirement says about issues which still remain in the ‘Rejected’ status.

### Answer (5):
A is not correct. The field “created” is about the time dimension and not users  
B is not correct. Operators NOT IN cannot be used to limit users in field assignee  
C is not correct. Operators NOT IN cannot be used to limit users in field creator  
D is correct. Every time you know that it will not limit your results, you should put the project name(s) in the JQL query

### Answer (6):
A is incorrect. This query cannot be further simplified because every segment relates to a different dimension of data  
B is correct. Calendar functions like endOfDay() always consider the time zone of the viewing user. Time zone is an individual user setting configured in the user profile. In this case there is a time zone difference between offices in London and Chicago so query results may differ.  
C is incorrect. Keyword ‘type’ is an alias to keyword ‘issuetype’ and can be used interchangeably.  
D is incorrect. Status names containing only one word do not have to be in quotation marks

### Answer (7)
A is incorrect. The field name “filterName”  does not exist  
B is incorrect. You cannot use statement: status = Unassigned to find unassigned issues (i.e. issues with no assignee)  
C is incorrect. You cannot use the Custom Field name, if there are more than one fields with that name in the Jira instance.  
D is correct. Quotation marks in the filter name are optional if there is only one word used  
E is incorrect. You  cannot use the equals:= operator to find the unassigned issues

### Answer (8)
A is correct. You do not need to check the ‘Browse Projects’ permission because filter results always show only issues to which a user has access. Project permissions and Issue security may limit the number of issues that are listed in filters  
B is incorrect. You cannot use the field ‘Watcher’ with the operator IN.   
C is incorrect. You cannot use the field Watcher with the operator CONTAINS:~. Permission ‘Browse Issues’ does not exist in Jira.  
D is incorrect. You do not need to check the ‘Browse Projects’ permission because filter results always show only issues to which user has access. You cannot use the function currentUser() with the operator IN. Field ‘comments’ does not exist in Jira.

### Answer (9)
A is incorrect. This query will produce an error – there is no field projectCategory in Jira  
B is correct. This query contains the minimum necessary elements to see Rebeca’s blocked and uncomplete (unresolved) issues which are overdue on the day when the query is being run.  
C is incorrect. Using the field ‘category’ is not necessary and may limit the query results. Also, issue type linking is missing.  
D is incorrect. This  query will show all overdue issues which are unresolved and resolved.

### Answer (10)
A is incorrect. The calendar function endOfMonth() does not support the parameter ‘q’  
B is incorrect. The user related function membersOf() supports only one parameter. To include two groups, you should write two clauses and combine them with a keyword ‘OR’  
C is correct. These are valid functions but less frequently used  
D is incorrect. An issue cannot belong to two projects at the same time. The keyword ‘AND’ is incorrect.  
E is incorrect. You cannot use the operator  -> equals:= in this query but you should rather use the operator -> contains:~  
