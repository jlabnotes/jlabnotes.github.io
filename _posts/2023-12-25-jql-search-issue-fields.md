---
title: Jira JQL - searching Issue Fields
date: 2023-12-25 09:00:00 +0200
pin: false
categories: [JQL]
tags: [jql-cookbook,jql]
---
## Issue Fields: Status

**JQL: 3.1**  
`status CHANGED FROM "New" TO "In Progress" BY currentUser()`  
Show all issues transitioned from New to In Progress by the current user

**JQL: 3.2**  
`status CHANGED FROM "New" TO "In Progress" AFTER StartOfWeek()`  
Show all issues transitioned from New to In Progress since Monday at 0.00am. Please note that in most configurations in Jira, the week starts on Sunday not on Monday. It is better to do some testing first if you cannot check it in settings.

**JQL: 3.3**  
`status changed TO "In Progress" BEFORE StartOfDay (-7d) AND status = "In Progress"`  
Search for all issues that were transitioned 7 calendar days ago to status In Progress and is still in this status

**JQL: 3.4**  
`status WAS "To Do" ON (-24h)`  
Search for issues that were in status “To Do” 24 hours ago (although they can have a different status now)

**JQL: 3.5**  
`status = "To Do" and component IN componentsLeadByUser(jsmith)`  
Jira Data Center and Server only: show me all open issues from these projects where the username jsmith is a component lead

**JQL: 3.6**  
`status = New and component IN componentsLeadByUser(5c7074dc017b4a53c68aae8f)`
Jira Cloud: show me all open issues from these projects where the user jsmith is a component lead

**JQL: 3.7**  
`statusCategory = Done AND resolution IN (Done, "Won't Do")`  
Search for issues that are in any of statuses of the Done category (the category is selected is more universal than selecting a specific status) and the resolution type belongs to one of two listed resolution types  

## Issue Fields: Links

**JQL: 3.8**  
`parent = DMP-120`  
Search for all subtasks of a particular issue by the parent key

**JQL: 3.9**  
`parent IN (DMP-85, DMP-80)`  
Search for all subtasks of more than one parent issues

**JQL: 3.10**  
`issueLink IN (DMP-23, DMP-24)`  
Find all issues linked to at least one of the listed issues

**JQL: 3.11**  
`issueLink IN (DMP-23, DMP-24) AND issueLinkType = "relates to"`  
Find all issues linked to at least one of the listed issues but only with a specific link type

**JQL: 3.12**  
`issue IN linkedIssues("DMP-89", "is blocked by")`  
Search for issues linked only by the link type "is blocked by" to issue DMP-89

**JQL: 3.13**
`"Epic Link" IN (DMP-79, DMP-58)`  
Show all stories (or tasks) linked with an Epic by the Epic link relation

**JQL: 3.14**  
`"Epic Link" = "Jupiter One"`  
Find issues that belong to the epic "Jupiter One". You do not have to use the issue key ID in order for this query to work because the Epic Name will be sufficient

**JQL: 3.15**  
`"Epic link" = ANS-31`  
Find issues that are linked with a single Epic, which has the key ANS-31

**JQL: 3.16**  
`issueLinkType = "is blocked by" ORDER BY Rank`  
Find all issues that are blocked by other issues so their progress is not possible and sort them by Rank (so they can be sorted visually on the Kanban or Scrum board later)

## Issue Field: Resolution  

**JQL: 3.17**  
`resolution is not EMPTY ORDER BY priority DESC, assignee ASC`  
Display all unresolved issues sorted by two other fields - priority and assignee. It is good to know that the query `resolution = Unresolved` will give the same results

**JQL: 3.18**  
`resolution is EMPTY AND assignee = currentUser() AND due <= EndOfWeek(1)`  
Your personal to-do list till the end of this week.  
Find all unresolved issues where I am assigned to and which are due by the end of next week (it depends on Jira configuration which day is the last week day)

**JQL: 3.19**  
`resolution CHANGED TO Done BY currentUser() DURING (startOfMonth(-1), endOfMonth(-1))`  
Show to the current user all issues resolved as Done during the previous month. It is a very useful query for the reporting and statistics purposes. If your status consists of two or more words, then you need to put them in quotation marks like this: “To be done”  
The operator DURING sets a past date range for this query. The functions startOf() and endOf() will calculate the proper dates. You could also use here startOfYear() and endOfYear() here

**JQL: 3.20**  
`resolution = Done AND resolutiondate <-5d`  
Show all issues resolved as Done which have been resolved for more than 5 days. When you use the AND operator, all the criteria must be met for the query to return results

**JQL: 3.21**  
`resolution WAS Done BY currentUser() DURING (startOfYear(), endOfYear())`  
The BY operator limits this query to a specific user in the past. In this query you will see issues that at any point in time this year were resolved as Done by a current logged-in user. It will also show these which are now still resolved as Done as well as these which some time in the past were resolved but now are re-opened. If you further limit this query with AND resolution != Done, then this can help you find issues that were reopened.

## Issue Field: Project

**JQL: 3.22**  
`project = DMP AND issuetype IN standardIssueTypes()`  
Search for all standard issue types. These are Epics and Tasks, but not sub-tasks. Use this query if you have more types of sub-tasks and want to exclude them from the results.

**JQL: 3.23**  
`project = DMP AND issuetype IN subTaskIssueTypes()`  
Search for all sub-task issue types in one project with the key DMP

**JQL: 3.24**  
`project IN projectsWhereUserHasPermission("Resolve Issues")`  
This advanced query can be used in Jira Workflow JQL conditions (you will need a plugin for that e.g. Script Runner). When used, a transition will be only visible to those who can resolve issues. You can expand it with further narrowing clauses.

**JQL: 3.25**  
`category = "Agile" OR category = "Classic"`  
Search for issues that belong to projects in either of two categories - "Agile" or "Classic". This makes the query easier to build and maintain if you want to track issues from a few projects at the same time. In this query it is not necessary to put all project names one by one therefore this query is more universal for new projects that may be created in the future. This query will return results if you satisfy any of the given criteria.

**JQL: 3.26**  
`issuetype IN standardIssueTypes() AND issuetype IN subtaskIssueTypes()`  
Select all issues except Epics. The operator AND narrows the search results

## Other frequently used fields

**JQL: 3.27**  
`priority WAS Highest AFTER startOfWeek()`  
Display all issues where the priority was or still is set to “Highest” from the beginning of the week till now

**JQL: 3.28**  
`priority CHANGED BEFORE endOfWeek(-1) AFTER startOfWeek(-1)`  
Search for issues which had priorities changed in the last week

**JQL: 3.29**  
`reporter = currentUser() AND attachments IS EMPTY`  
Display all issues reported by current user where he/she forgot to attach attachments

**JQL: 3.30**  
`issue IN watchedIssues() and assignee != currentUser()`  
Show all issues that the current user is watching and where that user is not an assignee

**JQL: 3.31**  
`watcher = currentUser() AND watchers >= 5`  
Search for issues where the user executing the query is watching and where there are 5 or more watchers

**JQL: 3.32**  
`project = DAM AND level = internal`  
Search for issues in project DAM where the issue security level is set to ‘internal’. It is worth knowing that the field Security level visible on the issue screen is called level in search view columns.

## Other queries

**JQL: 3.33**
`filter = "My Team Filter" and assignee = currentUser()`  
From the results of the filter "My Team Filter", show only the issues assigned to the current user

**JQL: 3.34**
`issueType = Task AND workRatio > 60`  
Select all issues of type Task where over 60% of the original estimate has been logged. This is a very useful query if you want to track budget spending. You can also display the column workRatio in filters

