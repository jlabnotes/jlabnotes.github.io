---
title: Jira workflow properties list
date: 2021-01-02 09:00:00 +0200
categories: [WORKFLOWS]
tags: [workflow-properties]
---

# Disable permissions
## Disable editing

**Use case**

I want to disable edit property in the Resolved status for all users including Administrators

Workflow properties
```
Property key: jira.issue.editable
Property value: false
```
Alternative solution

```
Property key: jira.permission.edit.denied
Property value: (leave empty)
```
>Add this property to the Resolved status or any other final status.
Use this property every time you want to make the issue on this status not editable. Comments and returning transitions will not be affected by this change
{: .prompt-tip }

## Disable worklog  

**Use case**

I want to disable work log on Resolved and Closed statuses

**Workflow properties**

```
Property key: jira.permission.work.denied
Property value: (leave empty)
```

>Add this property to all statuses on Epics, where worklogs normally should not be added
{: .prompt-tip }

## Disable attachments add

**Use case**

I want to disable adding new attachments in all statuses other then In Progress

**Workflow properties**

```
Property key: jira.permission.attach.denied
Property value: (leave empty)
```

If you want to additionally disable deleting only own or all attachments, **use one** of the follwoing properties.

```
Property key: jira.permission.attachdeleteown.denied
Property key: jira.permission.attachdeleteall.denied
```

# Restrict Editing

## Restrict the Edit permission to project role Administrators only

**Use case**

I want to make issues in the Resolved status editable only to Administrators (or another single project role which I want to use)

> For this property to work, you need to check the role ID in project roles browser.
> Your property value may be different because your role ID for Administrator role can be different in your Jira instance
{: .prompt-tip }

**Workflow properties**
```
Property key: jira.permission.edit.projectrole
Property value: 10002
```

## Restrict the Edit permission to project roles

**Use case**

I want to make issues in the Resolved status editable only to Administrators AND Developers.

In this case you need to configure properties for two roles so you need two workflow properties. Suffix 1 or 2 or 3….is used when you want the same property to be added two or more times.

**Workflow properties**

```
Property key (1): jira.permission.edit.projectrole.1
Property value: 10002
Property key (2): jira.permission.edit.projectrole.2
Property value: 10001
```

## Restrict the Edit permission to a user group

**Use case**

I want to make issues in the In Progress status editable only to a Jira group named jira-project-managers in my Jira instance

**Workflow properties**

```
Property key: jira.permission.edit.group
Property value: jira-project-managers
```

>You can use groups from Jira directory or other directories. There are generally hyphens or underscore characters used in the group naming convention.
{: .prompt-tip }

## Restrict the Edit permissions for sub-tasks

**Use case**

I want all sub-task to be editable only to a role Developers, when a Parent task Bug is in the In Progress status

**Workflow properties**

Property key: jira.permission.subtasks.edit.projectrole
Property value: 10102

>For this property to work, you need to check the role ID in project roles
{: .prompt-tip }

# Disable comments

## Disable comments add

**Use case**

I want to disable adding comments in the Resolved status so no change is added to resolved issues

**Workflow properties**

```
Property key: jira.permission.comment.denied
Property value: (leave empty)
```

>This property can be applied to any workflow status. Please note, that when disabled completely, comments will not be available on the transition screen either.
{: .prompt-tip }

## Restrict comments to one project role

**Use case**

I want to enable adding comments in the Resolved status only to a Jira role named Administrators in my Jira instance

**Workflow properties**

```
Property key: jira.permission.comment.projectrole
Property value: 10002
``` 

## Restrict comments to one user group

**Use case**

I want to enable adding comments in the In Progress status only to a Jira group named jira-developers in my Jira instance

**Workflow properties**

```
Property key: jira.permission.comment.group
Property value: jira-project-managers
```
>You can use groups from Jira directory or other directories. There are generally hyphens or underscore characters used in the group naming convention
{: .prompt-tip }


## Disable editing and commenting

**Use case**

I want to make sure that it is not possible to edit and comment closed issues (in status Closed) for anyone

**Workflow properties**
```
Property key (1): jira.issue.editable
Property value: false
```
```
Property key (2): jira.permission.comment.denied
Property value: (leave empty)
```

# Restrict Assignee changes

## Restrict changing Assignee

**Use case**

When a task is in Progress, I do not want anyone to change the Assignee. If someone needs to change the Assignee, they need to go back to the previous status

**Workflow properties**

```
Property key: jjira.permission.assign.denied
Property value: (leave empty)
```

## Restrict permission to change Assignee only to one user role

**Use case**

When a task is in Progress, I want only users in role Administrator to be able to change the Assignee

**Workflow properties**

```
Property key: jira.permission.assign.projectrole
Property value: 10002
```
