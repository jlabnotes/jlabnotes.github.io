---
title: Workflow transition properties
date: 2022-09-07 11:33:00
categories: [WORKFLOWS]
tags: [workflow-properties]
img_path: /assets/wtp0/
---

# Two must-have workflow properties
Go to <kbd>Jira Administration / Issues / Workflows</kbd>, edit the selected workflow exactly the same way as previously. Select the resolving transition and edit its properties.

![edit workflow properties](wtp001.png)
_Click on the transition to see options_

## Limit the list of available resolutions on the transtion screen

```
jira.field.resolution.include
```
Property value: 10000,10004,10100

## Workflow buttons sequence
The lower the number, it will be closer to the left.  
The higher the number, it will be closer to the right

```
opsbar-sequence
```
Property value: 10,20,30,40




# More information

[More information and tutorials on https://jlabnotes.com](https://jlabnotes.com/)
