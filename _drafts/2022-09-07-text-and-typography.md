---
title: Text and Typography
author: Demo Author
date: 2022-09-07 11:33:00
categories: []
tags: [drafts]
img_path: /assets/img/
math: true
mermaid: true
---

# Full front matter  

```md
---
title: Text and Typography
date: 2022-09-07 11:33:00
categories: []
tags: []
img_path: /assets/img/
# pinned post
pin: true
# introduction image (optional)
image:
  path: android-chrome-192x192.png
  width: 192
  height: 192
  alt: Responsive rendering of Chirpy theme on multiple devices.
---
```
# References and sources
Jekyll Spaceship Plugin
: [Github Repo](https://github.com/jeffreytse/jekyll-spaceship)

# Styling text
Bold text ** or __  
(Example) **bold text** or __bold text__  

Italic text * 8 or _ _  
(Example) *italic text* or _italic text_  

Docs github reference page  
[Github Docs basic writing and formatting syntax](https://docs.github.com/en/get-started/writing-on-github/getting-started-with-writing-and-formatting-on-github/basic-writing-and-formatting-syntax)

# Headers and skipped headers
---
Header which is picked up by TOC. Below headers skipped by TOC

<h1 data-toc-skip>H1 - Main heading</h1>

<h2 data-toc-skip>H2 - heading</h2>

<h3 data-toc-skip>H3 - heading</h3>

<h4>H4 - heading</h4>
---
<br>

# Links
## Simple as-is

<http://127.0.0.1:4000>

## Hyperlink
`Chirpy Theme` this is the link to the source file:  
[How to write a post](https://chirpy.cotes.page/posts/write-a-new-post/)

```md
<http://127.0.0.1:4000>
[How to write a post](https://chirpy.cotes.page/posts/write-a-new-post/)
```

## Links to PDFs

... you can [get the PDF](/assets/mydoc.pdf) directly.

```
... you can [get the PDF](/assets/mydoc.pdf) directly.
```
## Links to YouTube

[![Video Title](https://img.youtube.com/vi/fe8QgK3j4gw/0.jpg)](https://www.youtube.com/watch?v=fe8QgK3j4gw "This is a tooltip when you hover")

```
[![Video Title](https://img.youtube.com/vi/dTd7f-jK_BE/0.jpg)](https://www.youtube.com/watch?v=dTd7f-jK_BE "This is a tooltip when you hover")
```
# Lists

## Ordered list

1. Firstly
2. Secondly
3. Thirdly

```md
1. Firstly
2. Secondly
3. Thirdly
```
## Unordered list

- Chapter
  - Section
    - Paragraph

```md
- Chapter
  - Section
    - Paragraph
```

## Task list

- [ ] TODO
- [x] Completed
- [ ] Defeat COVID-19
  - [x] Vaccine production
  - [ ] Economic recovery
  - [ ] People smile again

```md
- [x] Completed
- [ ] Defeat COVID-19
  - [x] Vaccine production
```

## Description list

Sun
: the star around which the earth orbits

Moon
: the natural satellite of the earth, visible by reflected light from the sun

```md
Sun
: the star around which the earth orbits
```

# Text highlighters

## /kbd/ tag for Buttons/Menus
Click the button <kbd>Select your Favicon image</kbd> to upload your image file.
```md
Click the button <kbd>Select your Favicon image</kbd> to upload your image file.
```

## /mark/ tag to highlight
The changes are needed in the following spots:  
- <mark>timezone:</mark> Whatever matches your locale. (ex. America/New_York)
- <mark>title:</mark> Replace this with your website Title. (ex. Jadehawk's Tech Notes)
- and this is emoji :joy:

```md
The changes are needed in the following spots:  
- <mark>timezone:</mark> Whatever matches your locale. (ex. America/New_York)
- <mark>title:</mark> Replace this with your website Title. (ex. Jadehawk's Tech Notes)
```
## Block Quote
This is a normal text line  
> This line shows the _italics block quote_.  

This is another normal line

```md
> This line shows the _italics block quote_.
```

## Prompts

> An example showing the `tip` type prompt.
{: .prompt-tip }

>  ✓ means keep the file, ✗ means delete the file
{: .prompt-info }

> An example showing the `warning` type prompt.
{: .prompt-warning }

> An example showing the `danger` type prompt.
{: .prompt-danger }

```md
> An example showing the `tip` type prompt.
{: .prompt-tip }

>  ✓ means keep the file, ✗ means delete the file
{: .prompt-info }

> An example showing the `warning` type prompt.
{: .prompt-warning }

> An example showing the `danger` type prompt.
{: .prompt-danger }

```
## Expand and collapse text
<details>
<summary><strong>Click for more details</strong></summary>
Lorem ipsum dolor sit amet, consectetur adipiscing elit. Duis eget congue risus. Nulla in purus velit. Pellentesque non dolor aliquet, feugiat ligula vitae, lobortis nibh. Fusce placerat dolor ipsum, sit amet viverra felis laoreet ut. Proin ultrices sem placerat congue porta. Maecenas ut sapien mollis mauris posuere semper.
</details>

```md
<details>
<summary><strong>Click for more details</strong></summary>
Lorem ipsum dolor sit amet, consectetur adipiscing elit. Duis eget congue risus. Nulla in purus velit. Pellentesque non dolor aliquet, feugiat ligula vitae.
</details>
```

# Code Snippets
## Simple Highlight
{% highlight ruby %}
# some comment about the code
puts "Hello World!"
{% endhighlight %}

## Just text

```
# just put three commas
puts "Hello World!"

```
## Console

```console
$ env |grep SHELL
SHELL=/usr/local/bin/bash
PYENV_SHELL=bash
```

## Shell

```bash
if [ $? -ne 0 ]; then
    echo "The command was not successful.";
    #do the needful / exit
fi;
```

## Filename reference

```sass
@import
  "colors/light-typography",
  "colors/dark-typography"
```
{: file='_sass/just-a-demo-file.scss'}

# Tables

| Company                      | Contact          | Country |
|:-----------------------------|:-----------------|--------:|
| Alfreds Futterkiste          | Maria Anders     | Germany |
| Island Trading               | Helen Bennett    | UK      |
| Magazzini Alimentari Riuniti | Giovanni Rovelli | Italy   |

The following table will help you understand the changes to the favicon files:

| File(s)             | From Online Tool                  | From Chirpy |
|:--------------------:|:---------------------------------:|:-----------:|
| `*.PNG`             | ✗                                | ¼           |
| `*.ICO`             | ✓                                | ✗           |

```md
| Company                      | Contact          | Country |
|:-----------------------------|:-----------------|--------:|
| Alfreds Futterkiste          | Maria Anders     | Germany |
| Island Trading               | Helen Bennett    | UK      |
| Magazzini Alimentari Riuniti | Giovanni Rovelli | Italy   |

The following table will help you understand the changes to the favicon files:

| File(s)             | From Online Tool                  | From Chirpy |
|:--------------------:|:---------------------------------:|:-----------:|
| `*.PNG`             | ✗                                | ¼           |
| `*.ICO`             | ✓                                | ✗           |

```

# Images

- Default (with caption)
In order to prevent the page content layout from shifting when the image is loaded, **we should set the width and height for each image.**  

![Desktop View](mockup.png){: w="972" h="589" }
_Full screen width and center alignment_

```md
![img-description](/path/to/image)
_Image Caption_
```

<br>

- Shadow

![Window shadow](window.png){: .shadow width="1548" height="864" style="max-width: 90%" }
_shadow effect (visible in light mode)_

```md
![Window shadow](window.png){: .shadow width="1548" height="864" style="max-width: 90%" }
_shadow effect (visible in light mode)_
```
<br>

- Left aligned

![Desktop View](mockup.png){: width="972" height="589" style="max-width: 70%" .normal}

```md
![Desktop View](mockup.png){: width="972" height="589" style="max-width: 70%" .normal}
```
<br>

- Float to left

  ![Desktop View](mockup.png){: width="972" height="589" style="max-width: 200px" .left}
  "A repetitive and meaningless text is used to fill the space. A repetitive and meaningless text is used to fill the space. A repetitive and meaningless text is used to fill the space. A repetitive and meaningless text is used to fill the space. A repetitive and meaningless text is used to fill the space. A repetitive and meaningless text is used to fill the space. A repetitive and meaningless text is used to fill the space. A repetitive and meaningless text is used to fill the space. A repetitive and meaningless text is used to fill the space. A repetitive and meaningless text is used to fill the space. A repetitive and meaningless text is used to fill the space. A repetitive and meaningless text is used to fill the space."

```md
![Desktop View](mockup.png){: width="972" height="589" style="max-width: 200px" .left}
  "A repetitive and meaningless text is used to fill the space. A repetitive and meaningless text is used to fill the space. A repetitive and meaningless text is used to fill the space. A repetitive and meaningless text is used to fill the space.
```
<br>

- Float to right

  ![Desktop View](mockup.png){: width="972" height="589" style="max-width: 200px" .right}
  "A repetitive and meaningless text is used to fill the space. A repetitive and meaningless text is used to fill the space. A repetitive and meaningless text is used to fill the space. A repetitive and meaningless text is used to fill the space. A repetitive and meaningless text is used to fill the space. A repetitive and meaningless text is used to fill the space. A repetitive and meaningless text is used to fill the space. A repetitive and meaningless text is used to fill the space. A repetitive and meaningless text is used to fill the space. A repetitive and meaningless text is used to fill the space. A repetitive and meaningless text is used to fill the space. A repetitive and meaningless text is used to fill the space."
```md
![Desktop View](mockup.png){: width="972" height="589" style="max-width: 200px" .right}
  "A repetitive and meaningless text is used to fill the space. A repetitive and meaningless text is used to fill the space.
```
<br>
