---
title: Calculate math result of two drop down values
date: 2020-09-12 09:00:00 +0200
categories: [AUTOMATION,SmartValues]
tags: [smart-values-math]
img_path: /assets/img/cmro01
---

# Use case
I have two custom field fields:
- Impact, type: _select List (single choice)_ with values:
  - 1-Very Low
  - 2-Low
  - 3-Medium
  - 4-High
  - 5-Very High
- Probability, type: _select List (single choice)_ with values:
  - 1-Very Low
  - 2-Low
  - 3-Medium
  - 4-High
  - 5-Very High

I have the third field - Risk Rating, type: Number Field

I want to send the result of calculations of Impact and Probability to the Risk rating field

# Solution

Smart value:
```groovy
{% raw %} {{#=}}{{issue.probability.value.left(1)}} * {{issue.impact.value.left(1)}}{{/}} {% endraw %}
```
> `value.left` means to cut off the first character from the drop-down value.  
{: .prompt-info }

## Automation config
![screenshot02](cmro01.png){: w="328" h="553" }

Use the smart value in the Edit Issue action.
![screenshot02](cmro03.png){: w="577" h="240" }

## Result
![screenshot01](cmro02.png){: w="248" h="87" }

# More information

[More information and tutorials on https://jlabnotes.com](https://jlabnotes.com/)
