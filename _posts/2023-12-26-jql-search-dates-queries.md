---
title: Jira JQL - searching Dates queries
date: 2023-12-26 09:00:00 +0200
pin: false
categories: [JQL]
tags: [jql-cookbook,jql]
---
## Due dates

**JQL: 5.1**  
`due > 7d`  
Show me issues due more than (after) 7 days from now in the future

**JQL: 5.2**  
`due <= 3d`  
Show me issues due within exactly the next 3 days from now (after now and before +3d from now)

**JQL: 5.3**  
`due >= "0" AND due <= 5d`  
Show me issues that are not overdue now and are due in the next 5 days from now. NB. “0” is just another way to set the current time, just like function now()

**JQL: 5.4**  
`due >= 7d AND due <= 10d`  
Issues due within the next 7d to 10d

**JQL: 5.5**  
`due <= -1w`  
Show me all issues that were due more than 1 week ago. This can easily be narrowed down with status type for example AND status = Open, to get overdue issues

**JQL: 5.6**  
`due < endOfYear(3M)`  
Find issues due by the end of March next year. This one is really interesting because it takes into account calendar months. You do not have to write the "+" character additionally.

**JQL: 5.7**  
`due >= startOfDay() AND due <= 7d`  
Display issues that are due in the next 7 days from midnight today (that is when the start of day begins)

**JQL: 5.8**  
`due < endOfDay()`  
Show me issues that are due by today any time before 23h59. This will include all issues from the past as well. The endOfDay() function will calculate the data in parentheses taking into account the date today.

**JQL: 5.9**  
`due < endOfDay(1)`  
Select issues that are due by tomorrow any time before 23h59. This will include issues from the past as well. Jira knows that you want to ask about tomorrow because you gave number 1 in parentheses. You do not have to write additionally the "+" or the "d" characters.

**JQL: 5.10**  
`due >= 2020-09-15 AND due < 2020-09-25`  
Today is the 20th of September. Show me issues that are, were or will be due between two specific dates. The past or the future depends on when this query is run. In this example all times on 2020-09-24 are included. It may be confusing because 25 of September is used. When you use the parameter “less than” only the previous day up to 23h59 will be taken into account. Make sure that you use the correct date format configured in your Jira.

**JQL: 5.11**  
`due >= startOfWeek(1w) AND due <= endOfWeek(2w)`  
Display issues due between Sunday next week and Saturday the following week (depends on the first day settings in Jira)

**JQL: 5.12**  
`duedate < now() and resolution = Unresolved`  
Find issues that now overdue but still are not resolved ( due < "0" will also search for overdue issues, because the duedate field name is an alias of due)

## Created and Updated

**JQL: 5.13**  
`updated < 2020-09-18`  
Show me all issues that were updated on 17 September 2020 or earlier (it is not a mistake, yes 17 September). This query will work because 18 September starts at 00:00 (midnight) so this will return issues updated until 23:59:59 on 17 September

**JQL: 5.14**  
`updated >= 2020-09-20 AND updated < 2020-09-21`  
Show me issues updated exactly on 20 September 2020. Normally you do not specify a time when searching for an exact date, therefore Jira will assume midnight on the date you provide. When you type the query like this, you will search all issues across all 23 hours and 59 seconds for that date up to but not including (<) 12:00 midnight the following day (21 Sept)

**JQL: 5.15**  
`updated >= -2w AND updated <= -1w`  
Display issues updated more than 1 week ago but not more than 2 weeks ago (within a specific period of time in the past)

**JQL: 5.16**  
`updatedDate > startOfDay(-1) AND updatedDate < endOfDay(-1)`  
Show me all issues that were updated during the whole 24 hours (1 calendar day) yesterday. 'updatedDate' is an alias name of the 'updated' field

**JQL: 5.17**  
`updated >=-5d AND resolution = unresolved`  
Display issue that have been updated within the past 5 days and are unresolved

**JQL: 5.18**  
`status = "In Progress" and NOT updated >= startOfDay(-2w)`  
Show me all issues that are in status ‘In Progress’ and have not been updated for over 2 weeks. They may require your attention.

**JQL: 5.19**  
`created >= -2d and resolved < startOfDay(-1d)`  
Show me issues created within the last two days i.e. 48 hours from current time and resolved before the start of yesterday. If it is 15h00 in the afternoon, Jira will go back exactly 48 hours from now and not from the start of day.

**JQL: 5.20**  
`created >=startOfDay(-5)ORDER BY Updated`  
Display issues created within the last 5 days from midnight (12 a.m.) today, sorted by the Updated date. It is important to note the current moment in time is not a reference point. That is why using startOf…and endOf… functions is more specific than using the current moment of time as the relative date reference.

**JQL: 5.21**  
`createdDate >= startOfWeek (-1)`  
Display issues created since last week. The function startOfWeek returns the data result so Jira will calculate on what date was the start of last week (and it depends on the first calendar date configuration in your instance)

**JQL: 5.22**  
`createdDate >= 2020-09-20`  
Search for issues created on and after 20 September 2020. When you specify a date Jira assumes midnight on the date you provide.

**JQL: 5.23**  
`created > "2020-09-28 21:12"`  
Search for issues created later than on 28 September 2020 at 21:12

**JQL: 5.24**  
`(created > lastLogin() OR created > currentLogin()) AND creator = currentUser()`
Show me the issues that I created during my last session or during this session. Note that Creator is not the same as Reporter because the value in field Reporter can be changed. The operator OR widens the search results

**JQL: 5.25**  
`created < currentLogin AND creator = currentUser()`  
Search for issues created before the current login session of the user executing this query

## Issue history

**JQL: 5.26**  
`issue IN issueHistory() AND assignee = currentUser()`  
Find issues which I have recently viewed, that are assigned to me

**JQL: 5.27**  
`issue IN issueHistory() AND assignee = currentUser()`  
A very useful query for a personal dashboard. Show me up to 50 issues that I have viewed recently.

**JQL: 5.28**  
`status CHANGED FROM "In QA Review" TO "QA Rejected" BY jsmith DURING (StartOfWeek(-1), EndOfWeek(-1))`  
Show me issues that were transitioned to indicated status by a user jsmith during the last week. Please note that in Jira startOfWeek() starts Sunday 00:00:00 endOfweek() is Saturday 23:59:59 where a week has default settings. However, if you want the current week to be Mon-Sun, use "startOfWeek(1d), endOfWeek(1d)".  Similarly, if you want the previous week to be Mon-Sun, use "(startOfWeek(-6d), endOfWeek(-6d))"

**JQL: 5.29**  
`!(status CHANGED AFTER '-1w')`  
Knowing how to use negation is very useful in JQL. Here is an example on how to display only these issues where the status did not change in the last week.

**JQL: 5.30**  
`status CHANGED AFTER startOfMonth()`  
Search for issues whose status changed after the first calendar day of the current month. Should be useful when you want to check if some resolved issues from the last month did not change their status this month. If you use it as a filter to which you subscribe, you can create in this way an alerting notification mechanism.

**JQL: 5.31**  
`status CHANGED TO ("In Progress",Done) DURING (-24h, Now())`  
Search issues that were transitioned to Done or Closed within the last 24 hours

**JQL: 5.32**  
`status WAS "In Progress" DURING (startOfWeek(), endOfWeek())`  
Search for issues that were in Progress any time last week.

**JQL: 5.33**  
`status WAS "In Progress" DURING (2020-09-01, 2020-09-30)`  
Search for issues that were in Progress any time between the specified dates (make sure that you use your configured format of dates in your Jira instance).

**JQL: 5.34**  
`status WAS IN (Done, Approved) ORDER BY updatedDate ASC`  
Search for issues that were or are in one of selected status and order results by the date they were updated ascending

**JQL: 5.35**  
`status WAS Closed BY currentUser() DURING (startOfWeek(-1), endOfWeek())`  
Search for issues that were transitioned to Closed by the user executing this query within the last two weeks from first day of the week last week to the last day of this week

**JQL: 5.36**  
`resolution WAS NOT Duplicate BEFORE 2020-09-01`  
Display issues that were not resolved as Duplicate before 1st September 2020 (so on 31 August or earlier).

**JQL: 5.37**  
`statusCategory = "In Progress" AND duedate >= startOfMonth(1) AND duedate <= endOfMonth(1)`  
Search for all issues that are in the status category “In Progress” (with any status name) that will be due next calendar month. If you change the parameter to -1 then you can search the same for issue that WERE due last calendar month.

**JQL: 5.38**  
`status CHANGED TO "In Progress" BEFORE StartOfDay (-7d) AND status = "In Progress"`  
Search for all issues that were transitioned more than 7 calendar days ago to status in Progress and still are in this status.

**JQL: 5.39**  
`status WAS Done AFTER startOfWeek()`  
Show me all the issues where the status WAS or IS Done since the start of this week. In most configurations in Jira, the week starts on Sunday not on Monday. There is some confusion about it, so it is better to do some testing first.

**JQL: 5.40**  
`resolved >= -2w AND resolved <= -1w`  
Show me all issues resolved within 2 and 1 weeks ago

**JQL: 5.41**  
`resolved <= - 1d`  
Display issues resolved more than 1 day ago

**JQL: 5.42**  
`resolution WAS Done BY currentUser()`  
Show me issues that at any point in time were resolved as Done by a current user. It will also show these which are now still resolved as Done as well as these which some time in the past were resolved

**JQL: 5.43**  
`priority WAS High BEFORE 2020-09-25`  
Display issues that had the field value Priority set as High on 2020-09-24 and earlier

**JQL: 5.44**  
`issue IN issueHistory() and creator = currentUser()`  
Display up to 50 issues that I looked at recently (stored in my issue browsing history) which I created

## Versions and Sprints
**Version**  
grouping of issues in a specific release

`fixversion = version-name`  
`fixversion in (version1, version2)`  
`fixversion is not empty`  
`fixversion in unreleasedVersions()`  
`fixversion = earliestUnreleasedVersion()`  
`fixversion = latestReleasedVersion()`  
`affectedVersion = version-name`

**Sprint**  
time-boxed iteration of rapid work  

`sprint in futureSprints()`  
`sprint = sprint-ID`  
`sprint = sprint-name`  
`sprint in (sprint1, sprint2, sprint3)`  
`sprint is empty`  
