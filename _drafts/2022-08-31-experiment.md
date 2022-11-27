---
title: Experiment
date: 2022-09-07  09:00:00 +0200
categories: []
tags: [drafts]
img_path: /assets/img/
---
Lorem Ipsum is simply dummy text of the printing and typesetting industry. Lorem Ipsum has been the industry's standard dummy text ever since the 1500s, Lorem Ipsum is simply dummy text of the printing and typesetting industry. Lorem Ipsum has been the industry's standard dummy text ever since the 1500s, 
<!--more-->
# Table Experiment

<table>
<thead>
<tr class="header">
<th>Field</th>
<th>Description</th>
<th>Another column</th>
</tr>
</thead>
<tbody>
<tr>
<td markdown="span">First column **fields**</td>
<td markdown="span">
It is a long established fact that a reader will be distracted<br/>
by the readable content of a page when looking at its layout.<br/>
The point of using Lorem Ipsum is that it has a more-or-less normal<br/>
distribution of letters, as opposed to using 'Content here, content here',<br/>
making it look like readable English..</td>
<td markdown="span">Just something</td>
</tr>
<tr>
<td markdown="span">Second column **fields**</td>
<td markdown="span">There are many variations of passages of Lorem Ipsum available, but the majority have suffered alteration in some form, by injected humour, or randomised words which don't look even slightly believable. If you are going to use a passage of Lorem Ipsum, you need to be sure there isn't anything embarrassing hidden in the middle of text.</td>
<td markdown="span">Just something</td>
</tr>
</tbody>
</table>

{:color-style: style="background: black;"}
{:color-style: style="color: white;"}
{:text-style: style="font-weight: 800; text-decoration: underline;"}

|:             Here's an Inline Attribute Lists example                :||||
| ------- | ------------------ | -------------------- | ------------------ |
|:       :|:  <div style="color: red;"> &lt; Normal HTML Block > </div> :|||
| ^^      |   Red    {: .cls style="background: orange" }                |||
| ^^ IALs |   Green  {: #id style="background: green; color: white" }    |||
| ^^      |   Blue   {: style="background: blue; color: white" }         |||
| ^^      |   Black  {: color-style text-style }                         |||

$ \int\_a^b f(x)\,dx. $

```plantuml!
Bob -> Alice : hello world
```

```mermaid!
pie title Pets adopted by volunteers
  "Dogs" : 386
  "Cats" : 85
  "Rats" : 35
```

Youtube Usage

[![HG quality](https://img.youtube.com/vi/dTd7f-jK_BE/hqdefault.jpg)](https://www.youtube.com/watch?v=dTd7f-jK_BE "This is a tooltip")

<ul>
  {% for post in site.posts %}
    <li>
      <a href="{{ post.url }}">{{ post.title }}</a>
    </li>
  {% endfor %}
</ul>
