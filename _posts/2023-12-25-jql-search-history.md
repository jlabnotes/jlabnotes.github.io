---
title: Jira JQL - searching Issue History
date: 2023-12-25 09:00:00 +0200
pin: false
categories: [JQL]
tags: [jql-cookbook]
---
There is a list of parameters that are available for operators involving time and history of changes. Below is the list of these parameters and you will see them in practical examples in chapters that follow.

- ON, BEFORE, AFTER – to be used with a specific date
- DURING – to be used with a date range from the past e.g. DURING(2020-09-01, 2020-09-20)
- BY – to be used with a username to limit results to a specific user in the past
- value CHANGED FROM TO – to check how the value of assignee or status changed in issue history
 CHANGED BY – to check if an issue was changed by a specific user
The table below summarises operators and how they work.  

**JQL Operator "WAS"**  

| Parameter | Explanation | 
|-----------|:-----------|
| Operator | WAS <br> WAS NOT<br> WAS IN<br> WAS NOT IN |  
| Explanation | Finds issues that currently have<br> or previously had values |  
| Used only in fields | Assignee, Fix Version, Priority,<br> Reporter, Status, Resolution |  
| Accepts these parameters | AFTER "date"<br> BEFORE "date"<br> BY "username" - set by what user<br> DURING ("date1","date2")<br> ON "date" |  

**JQL Operator "CHANGED"**  

| Parameter | Explanation |  
|-----------|:-----------|  
| Operator | CHANGED |  
| Explanation |  Finds issues where a value changed |  
| Used only in fields | Assignee, Fix Version, Priority,<br> Reporter, Status, Resolution |  
| Accepts these parameters | AFTER "date"<br> BEFORE "date" <br> BY "username" - set by what user <br> DURING ("date1","date2") <br> ON "date" <br> FROM "old_value" TO "new_value" |  

