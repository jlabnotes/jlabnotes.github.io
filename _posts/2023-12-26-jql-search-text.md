---
title: Jira JQL - searching Text
date: 2023-12-26 09:00:00 +0200
pin: false
categories: [JQL]
tags: [jql-cookbook]
---
## About searching dates

Searching for text seems to be the most unpredictable type of search in Jira. There are many questions on Atlassian Community from users which complained about wrong results despite the well written queries.  
I know from answers given to these questions that a lot of depends on indexing the database, configuration of character encoding (like Unicode Standard), language used and so on. So, in case some of your queries do not return expected results, do not be surprised (too much).  

Generally, you can search for text stored in text type fields like Summary, Description, Comments, custom fields and third-party custom fields. However, you may encounter some problems with searching through text fields in Jira Cloud. It is best to start writing JQL queries in Jira Cloud in the Simple Mode first.

More about search syntax for text fields:
[Atlassian Support - search syntax for text fields](https://support.atlassian.com/jira-software-cloud/docs/search-syntax-for-text-fields/)

## Queries

**JQL: 6.1**  
`text ~ "project approved "`  
Display all issues containing both words in any single text field, for example: a title, description or comments.

**JQL: 6.2**  
`description ~ "we have a problem with"`  
Show me issues where the description contains the term "we have a problem"

**JQL: 6.3**  
`comment ~ "approved" AND comment ~ "confirmed"`  
Display issues where there are two words in the same comment

**JQL: 6.4**  
`"Change Comment" ~ "approved" OR "Change Comment" ~ "rejected"`  
Jira Data Center and Server: Show me issues where the custom field Change Comment contains words approved or rejected

**JQL: 6.5**  
`"Change Comment" ~ "approved OR rejected" AND assignee = currentUser()`  
Jira Data Center and Server: An example of a compound query with OR operator. Show me issues where the custom field Change Comment contains words approved or rejected to which the current user is assigned. The operators must be in CAPITAL letters.

**JQL: 6.6**  
`"Change Comment[Short text]" ~ "approved" OR "Change Comment[Short text]" ~ "confirmed"`  
Jira Cloud: Show me issues where the custom field Change Comment contains words approved or rejected. The segment [Short text] is added automatically when you select the custom field of this type.

**JQL: 6.7**  
`"Keyword[Short text]" ~ "approved AND confirmed"`  
Jira Cloud: Show me issues where the custom field Keyword contains both words approved AND rejected.  The operator in the quotation marks must be in CAPITAL letters.

**JQL: 6.8**  
`comment ~ "error 4*"`  
Display all issues where one of the comments contains the term that begins with the text error 4. This will return issues with comments like error 4, error 45, error 4850
