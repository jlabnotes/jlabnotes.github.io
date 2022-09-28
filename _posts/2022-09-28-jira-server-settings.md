---
title: Jira Server/DC Date/Time Settings
date: 2022-09-28 09:00:00 +0200
categories: [SETTINGS]
tags: [date_time]
img_path: /assets/images/jss0/
---

# Changing the Date/Time display in Jira  
If you want to change how the date and time is displayed in Jira Server/DC, there are two places where you need to configure settings:

## General configuration

The date or date/time formats for date pickers are defined by a pair of properties (one for Java and the other for JavaScript). The two properties in this Java/JavaScript pair must match in order for the date (or date/time) picker they define to function correctly.

**Menu:**  
<kbd>Jira Administration/System/General configuration/Advanced settings</kbd>

Settings

```md
jira.date.picker.java.format
dd/MM/yyyy

jira.date.picker.javascript.format
%d/%m/%Y

jira.date.time.picker.java.format
dd/MM/yyyy HH:mm

jira.date.time.picker.javascript.format
%d/%m/%Y $H:%M
```
![img-description](/jsds01.png)
_Jira System General configuration_

# Look and feel configuration

Date/Time Formats configuration options on the Look and Feel page, which only customize JIRA's presentation of times and dates to users.  

```md
Time Format
HH:mm

Day Format
EEEE HH:mm

Complete Date/Time Format
dd/MM/yyyy HH:mm

Day/Month/Year Format
dd/MM/yyyy

Use ISO8601 standard in Date Picker
Yes
```

![img-description](/jsds02.png)
_Look and feel configuration_

`Documentation`  
[Changing the Due Date Input Format](https://confluence.atlassian.com/jira/changing-the-due-date-input-format-192536.html)

# More information

[More information and tutorials on https://jlabnotes.com](https://jlabnotes.com/)
