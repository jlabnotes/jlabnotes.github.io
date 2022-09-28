---
title: Jira workflow properties - how to use them?
date: 2020-12-31 09:00:00 +0200
categories: [WORKFLOWS]
tags: [workflow-properties]
img_path: /assets/images/jwps/
---
Advanced workflow properties in Jira are very useful every time you need to introduce some restrictions on certain statuses or workflow transitions of a workflow. In this article I have collected my favorite permission-based properties that I use most often in advanced Jira configurations.

# Types of Jira workflow properties
You can utilize advanced workflow properties in the following scenarios:

**Status workflow properties**

 - <mark>Permission based properties</mark> - when you want to restrict a user to perform some action only on a specific status. This article focuses on these properties
 - <mark>Transition workflow properties</mark>
   - Change transition buttons order. 
   - Hide resolution values when resolving issues

# How to use permission-based workflow properties?

The format of workflow properties is

`jira.permission.[subtasks.]{permission}.{user}.{suffix}`

where:

`jira.permission` is a standard prefix

`[subtasks.]` if specified, indicates that the permission applies to the subtasks of issues in this step

`{permission}` is a short name specified in Permissions class (e.g. attach, resolve, close, delete, link, comment)

`{user}` is a description who will be affected by the permission property - user, group, assignee, reporter, lead, userCF, projectrole)

`{suffix}` is a number when you need to create the same property for more than one user/group/role

>**Important**:  
Workflow permissions are used only to locally restrict permissions that are set in the permission scheme. You can not grant permissions in this way.
For example, in your permission scheme, if you have the ‘Add comments’ permission granted to only one project role, let us say ‘Developers’, you cannot then add this permission to other roles like ‘Managers’ using workflow properties.  
If the role ‘Managers’ is excluded on the permission scheme level, then adding them in the workflow property will not work.
{: .prompt-tip }

# How to add workflow properties on status?

![workflow properties](jwps01.png)

To edit the status property, edit the workflow and:

1. Select the status where you want to add some additional properties
2. Click on properties link

![workflow properties](jwps02.png)

To add the status property, edit the following fields:

1. **Property key** – a special series of property keys as described in examples below. It controls a particular type of permission and (optionally) a user or a group
2. **Property Value** – put the value if it exists in the property
Please note, that you cannot edit once added property. To change a property you need to delete it and add a new property again.  

To delete a status property click on the link delete

![workflow properties](jwps03.png)

# How to check the global project role ID in your Jira instance?

Some workflow properties require the ID number of global project roles. Below I explain how to check this ID, so you can use it in the workflow permission property value.  

Go to <kbd>Jira Administration / System / Project roles</kbd> and click on any of the actions

![workflow properties](jwps04.png)

See the role ID in the address bar

![workflow properties](jwps05.png)



# More information

[More information and tutorials on https://jlabnotes.com](https://jlabnotes.com/)
