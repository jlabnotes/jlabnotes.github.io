---
title: Jira JQL - searching People
date: 2023-12-25 09:00:00 +0200
pin: false
categories: [JQL]
tags: [jql-cookbook]
---
## Searching for user names in Jira DC and Jira Cloud  
Searching for users by their usernames is possible only in Jira Data Center and Server but not in Jira Cloud.  
In the Cloud version, when you create a JQL search query for a user in any of the fields Assignee, Reporter or any custom user-picker, Jira will display them as Atlassian Account ID.

**JQL: 4.1**  
`project = DMP AND assignee = currentUser()`  
This query will use the login of the user who executes it and will list all the issues from the specific project. Using the function currentUser() makes the JQL queries easier to maintain because you do not have to create individual queries for each user.

**JQL: 4.2**  
`assignee != currentUser()`  
Display all issues which are NOT assigned to a user who runs this query. This is a very useful function if you want to write a universal query which will show different results depending on the user which runs the query

**JQL: 4.3**  
`assignee not IN (EMPTY, currentUser())`  
Display all issues which are neither unassigned nor assigned to the current user – they are assigned, and to the current user but to somebody else..

**JQL: 4.4**  
`assignee IN membersOf("jira-administrators")`  
Show me all issues where an assignee belongs to a user group jira-administrators. Using the function membersOf makes the query easier to maintain because you do not have to list all the users in one team, and the list is maintained on the group level

**JQL: 4.5**  
`assignee WAS NOT jsmith`  
Jira Data Center and Server only: Show me all issues except those where the assignee WAS or still is user jsmith.

**JQL: 4.6**  
`assignee WAS NOT 5c7074fe36d4d54c411328f9`  
Jira Cloud: Please note that in Jira Cloud the user name will be converted to ID identifier, so the query will have to use this ID identifier: 5c7074fe36d4d54c411328f9

**JQL: 4.7**  
`assignee WAS currentUser() and assignee != currentUser()`  
Jira Data Center and Server only: Display issues where a user executing the query was an assignee but is not any more

**JQL: 4.8**  
`assignee WAS currentUser() DURING (2020-09-01, 2020-09-30)`  
Display issues where the current user was an assignee in September 2020.

**JQL: 4.9**  
`assignee WAS NOT jsmith`  
Show me all issues except those where the assignee WAS or still is user jsmith. Please note that in Jira Cloud the user name will be converted to ID identifier, so the query will look like this: assignee WAS 5c7074da7dae4b6533848198

**JQL: 4.10**  
`NOT assignee = currentUser() AND NOT creator = currentUser()`  
Display all issues not reported by and not assigned to a current user executing this query. The operator NOT works the same as the != operator. Please also note that issue creator is not the same as issue Reporter. Unlike Reporter, this value cannot be modified.

**JQL: 4.11**  
`comment ~ currentuser() AND updatedDate >= endOfDay(-10d) ORDER BY lastViewed DESC`  
Jira Data Center and Server only: Show me all issues where I am mentioned, not older than 10 days and sort them by when I have recently viewed them descending.

**JQL: 4.12**  
`comment ~ 5c7074da7dae4b6533848198 AND updatedDate >= endOfDay(-10d) ORDER BY updatedDate DESC`  
Jira Cloud only. Please note that in Jira Cloud you will have to know the user ID identifier to run queries with specific users.
Show me all issues where I am mentioned (my Jira Cloud ID is after the tilde symbol), not older than 10 days and sort them by updated date descending. Unfortunately, in Jira Cloud in this context the function currentUser does not work"

**JQL: 4.13**  
`creator IN membersOf("developers")`   
Display issues created by the members of a user group developers or jira-administrators

**JQL: 4.14**  
`issue IN updatedBy("jira-admin", "2020/09/01", "2020/09/30")`  
Search for issues created, updated any field or made a comment by a specific user in September 2020. Creating an issue is a form of its updating
