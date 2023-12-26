---
title: Jira JQL - searching Dates introduction
date: 2023-12-26 09:00:00 +0200
pin: false
categories: [JQL]
tags: [jql-cookbook]
img_path: /assets/images/jsdts/
---
## Units of time
These queries will help you find issues based on dates or dates range.
There are the following units of time in JQL with corresponding letters which you need to use in queries:
- y – Years
- M – Months (note: this one is a capital letter)
- w – Weeks
- d – Days
- h – hours
- m – minutes  

## Timeline
In order to understand queries involving dates and time, you need to visualise yourself a timeline, where now is the current moment in time and which in Jira is represented as now().

![time periods](jsdts01.png)  

There are four periods of time that you can ask about in Jira (see the picture above). They are divided by the operators which are easy to remember:
1. **Operator “<”** –  translates as “before” or “earlier than”.
For example <-1d means before/earlier than one day in the past from this moment.
2. **Operator “>”** – translates as “after”. 
For example, >-1d means after one day in the past till now (and in the future if it is possible for a specific field). 

In fields _Created_, _Updated_, _Resolved_, the dates refer to the past. The past can be divided into two periods of time:
1. **past within a specific period of time** – this can be determined with an operator greater than “>” or, if you want to include this specific moment of time, you use the operator greater than equal “>=” (what happened after a specific moment in the past)
2. **past with an unspecified period of time** – if you want to include all the past dates before now or before a point of time in the past, you just use the operator less than “<”.  

This will all be clearer to you when you see a few examples.  
In the same way we can divide the future. Queries about the future work only with the field “due” or the alias “duedate”. However, please note that the duedate can also be in the past (e.g. task was due)

## Specifying time
Another important thing to remember is that if you do not specify a time while searching for a specific date (and normally we do not do it), Jira will assume that you want to start searching from midnight on that date e.g. 2020-09-20 00:00.  

>  If you are interested in issues up to 23:59 on 2020-09-19 or previous days, use the query: < 2020-09-20.
{: .prompt-info }

You should know that exact times are also stored in Jira along with dates, and they can be checked in the issues filter view.   

![time in filter](jsdts02.png)  

Often when you create many issues in a very short period of time and want to sort them by date, they will be sorted not so much by the date but by the time they were created in Jira.
