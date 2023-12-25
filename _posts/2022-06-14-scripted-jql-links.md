---
title: Scripted JQL - Linked Issues
date: 2022-06-14 09:00:00 +0200
pin: true
categories: [JQL]
tags: [scripted-jql]
---

## General Linking - _hasLinkType()_

Find issues that have ANY linked issues  
`issueFunction in hasLinks()`  

Find issues that have a specific link (they are linked with an inward or outward link)  
`issueFunction in hasLinks("is duplicated by")`  

This is a generic JQL query which does the same thing only for one ticket.   
`issue in linkedIssues(ABC-123,"is duplicated by")`    
Find issues that are linked to a particular issue via a particular type of link 

## General Linking - _hasLinkType()_

If you want to use the _Link Name_, use the function hasLinkType()  
Find all issues which use a specific Link Name eg.'Duplicate'
'Duplicate' is the _Name_ of the link and not its _outward/inward link description_.  

Review Issue Linking names in Jira Administration.  
`issueFunction in hasLinkType(Duplicate)`  

Find all issues which use a specific Link Name with more than one word - 'Parent Child Link'.  
`issueFunction in hasLinkType("Parent Child Link")`  

If you want to use the _outward/inward link description_, then use function hasLinks().    

Below are two examples which have equivalent result:   
`issueFunction in hasLinkType("Duplicate")`  
`issueFunction in hasLinks("duplicates") OR issueFunction in hasLinks("is duplicated by")`

Find issues with more than 2 'blocks' outward links  
`issueFunction in hasLinks("blocks", "+2")`

## Selecting specific issues which are linked - _linkedIssuesOf()_

**Template**  
`issueFunction in linkedIssuesOf(Subquery, link_type)`

**Examples**  
Find issues linked by any link type, which are in status 'In Progress'.  
`issueFunction in linkedIssuesOf("status='In Progress'")`  

Find issues linked by an outward link 'clones' and these issues are in status 'To Do'.  
`issueFunction in linkedIssuesOf("status='To Do'", "clones")`

## Selecting specific issues linked with Epics

Find all issues linked by any type of regular link and including Epics Links and Subtask links for a specific subquery relating to tasks.  
As a result you will get issues matched by the subquery, including linked Epics and Sub-tasks.  
`issueFunction in linkedIssuesOfAll("Key = DOR-15300")`  
`issueFunction in linkedIssuesOfAll("project=IDP")`  

You can save the query as named filter and use its name.  
`issueFunction in linkedIssuesOf("filter = 'DRMA: All Open Tasks'")`

Find linked issues with whatever link to this specific issue SBM-600.  
`issueFunction in linkedIssuesOf("SBM-600")`  

Find linked issues with link type 'clones' to specific issue.  
`issueFunction in linkedIssuesOf("SBM-7026", clones)`

## Recursive Linking

### One Level below  
Recursively - return all issues that are linked both directly and indirectly to the results of the initial query  

**Template**  
Find all issues issues that are linked both directly and indirectly to the results of the initial query - top level. 
`issueFunction in linkedIssuesOfRecursive (Subquery)`

**Example**  
Find all issues linked the result of the initial query ("key=JIRA-1") that link back to the issues in the query, including blocks links, duplicates, clones, and more.  
`issueFunction in linkedIssuesOfRecursive ("key = JIRA-1")`  

**Example**  
Find all issues linked directly with the Change Bundle  
`issueFunction in linkedIssuesOfRecursive("issue =SBM-7043")`

### All levels below   
Find all issues including subtasks and epic links that are linked directly and indirectly to the results of the initial query.  
Example  
Find all linked issue to this Change Bundle
`issueFunction in linkedIssuesOfAllRecursive("issue =SBM-7043")`  
Result: will show Epics and tasks linked with these Epics, with no link type specified

## Epic Subqueries  

Find all issues linked with a specific set of issues. The names of links are not important. It will find linked issues to issues matched by the subquery.  

**Example**  
Find all issues linked with an issue Epic.  
`issueFunction in linkedIssuesOf("issuetype = Epic")`  

Show me issues linked with Epic, using the link name 'Change Bundle' having specific Component  
`issueFunction in linkedIssuesOf("issuetype = Epic", "Change Bundle") and Component = ZERT_VE`

**Template**  
Find Epics with stories meeting the subquery criteria.  
`issueFunction in epicsOf (Subquery)`  

**Example**  
Find Epics for stories selected in the query.   
`issueFunction in epicsOf("project = ABC AND issuetype=Task")`  

Find Epics with unresolved stories in project Mobile
`issueFunction in epicsOf ("resolution = empty and project = Mobile")`  

**Template**  
Find stories in Epics meeting the subquery criteria.  
`issueFunction in issuesInEpics (Subquery)`  

**Example**  
`issueFunction in issuesInEpics ("project=ABC and status = 'In Progress'")`  
Find all issues/stories which have Epics in status 'In Progress' in project ABC

`issueFunction in issuesInEpics("resolution is not empty")`  
Find all issues/stories in resolved Epics

## Sub-task Subqueries  
**Template**  
Show me all issues with sub-tasks  
`issueFunction in hasSubtasks()`

**Examples**  
Show me sub-tasks of issues specified by a subquery.  
In this example: all sub-tasks of all issues from project ABC  
`issueFunction in subtasksOf("project = ABC")`  

Show me sub-tasks in status "Done" of parent issues with resolution Empty  
`issueFunction in subtasksOf("resolution IS EMPTY") AND status = Done`

Show me subtasks of the following filter results  
`issuefunction in subtasksOf("filter = 'Stories in Epic'")`

Show me subtasks found by a subquery  
`issueFunction in subtasksOf("project = IDP AND issuetype=Incident")`

## Parent issues finding  
Stories and sub-tasks in an Epic:  
`parentEpic = Demo-123`  
As a result you will get Issues AND Sub-tasks in epic Demo-123  

Get the parents of subtasks found by a subquery  
`issueFunction in parentsOf("project=IDP and issuetype=Incident")`

Show me parents of sub-tasks from project ABC which are in status Open
`issueFunction in parentsOf("project = ABC AND status = Open")`  

Show me parent issues of unresolved sub-tasks where I am an assignee  
`issueFunction in parentsOf("Resolution IS EMPTY and Assignee = currentUser()")`

## JQL function for Portfolio
Get a list of sub-tasks for a specific parent.  
`issue in childIssuesOf("DOR-12962")`  
As a result I will see all children issues  

Get a list of ALL parents for a specific subtask.  
`issue in parentIssuesOf("DOR-18800")`  
As a result I will see all parents - issue and epic

## Advanced: Linked Parents-Children finding  
Find all issues linked with a specific set of issues and also linked with a specific link type.  
Link Name: Change Bundle  
Outward description: _change sheets_  
Inward description: _bundled in_  
In this example I want to see all issues linked to "Change Sheet" using inward link type 'bundled in'.  
Source: Change Sheet, Destination: linked issues by link name 'bundled in'  

I will get a list o parents of selected Change Sheets.  
`issueFunction in linkedIssuesOf("issuetype = 'Change Sheet'", 'bundled in')`  
As a result I will see all Change Bundles (parents)  

Another extended version with sub-query  
`issueFunction in linkedIssuesOf("project = DOR and type = EPIC and 'Control Unit' is EMPTY", 'Change Bundle')`  
This will show you all Change Bundles for linked issues (Epics in this example) which do not have any value in custom field Control Unit.  

In the opposite direction, a list of children - change sheets linked with any Change Bundles.  
`issueFunction in linkedIssuesOf("issuetype = 'Change Bundle'", 'change sheets')`



**Sources:** 
   1. <https://www.adaptavist.com/blog/top-10-most-commonly-used-jira-query-language-functions>
   2. <https://blog.valiantys.com/en/expert-tips/jql/>
   3. <https://confluence.atlassian.com/jiraportfolioserver0211/searching-for-issues-using-portfolio-details-945537693.html>