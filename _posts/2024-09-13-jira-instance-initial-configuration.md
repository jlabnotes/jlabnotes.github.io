---
title: Jira system initial configuration
date: 2020-09-13 09:00:00 +0200
categories: [SYSTEM]
tags: [jira-configuration]
img_path: /assets/images/jsic/
---
After new Jira instance installation, it is necessary to update the default values for date formatting and first day of the week. It is needed to have properly displayed dates in fields like Due Date or in Sprint Planning.  

# Jira System Advanced settings  
Go to Jira Administration / General configuration / Advanced settings  

![properties-setup](jsic01.png)  

Set the properties as follows:  
`jira.date.picker.java.format = dd/MM/yyyy`  
`jira.date.picker.javascript.format = %d/%m/%Y`  
`jira.date.time.picker.java.format = dd/MM/yyyy HH:mm`  
`jira.date.time.picker.javascript.format = %d/%m/%Y %H:%M`  
More about date formats are explained here:  
[https://confluence.atlassian.com/jira/changing-the-due-date-input-format-192536.html](https://confluence.atlassian.com/jira/changing-the-due-date-input-format-192536.html)

# Jira System Advanced settings  
Go to Jira Administration / Look and feel  
In the Date/Time Formats section at the very bottom, make the following changes. All the changes are saved automatically.  

![look-and-feel-setup](jsic02.png)  

Set the properties as follows:  
`Time Format -> HH:mm`  
`Day Format -> EEEE HH:mm`  
`Complete Date/Time Format -> dd/MM/yyyy HH:mm`  
`Day/Month/Year Format -> dd/MM/yyyy`  
`Use ISO8601 standard in Date Picker -> Set Yes`

# Advanced settings exception in Jira Cloud  
`jira.date.picker.*` and `jira.date.time.picker.*` aren't supported in the issue view.  
The issue view formats your dates and times based on your profile settings page, selected language.  
In practice this means that if you do not like the US format, eg: Sep 13, 2024 then go to your Atlassian Account, Account preferences, and change the format to UK.  

<mark>**Please Note:**</mark> You cannot have English language setup and the German (or any other country) date format any more. If you want to have English interface then you need to have either US or UK format.

More about advanced settings in the Jira Cloud administration documentation:  
[https://support.atlassian.com/jira-cloud-administration/docs/configure-advanced-settings/](https://support.atlassian.com/jira-cloud-administration/docs/configure-advanced-settings/)  