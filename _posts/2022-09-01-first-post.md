---
title: First Post Ever
description: This is a small description to the first post
date: 2022-09-01
pin: true
categories: [HOMELAB,HARDWARE]
tags: [servers,dell,hp,suprmicro]
toc: false
---
### About Chirpy
This is the link to the source file:  
[How to write a post](https://chirpy.cotes.page/posts/write-a-new-post/)

This is how you insert a picture  
```md
![img-description](/path/to/image)
_Image Caption_
```
This is how you size the picture  
```md
![Desktop View](/assets/img/sample/mockup.png){: w="700" h="400" }
```

![Picture](/assets/img/android-chrome-192x192.png){: .shadow }
_This is the image caption_

> Example line for prompt.
{: .prompt-tip }

`inline code part`

> /path/to/a/file.extend
{: .prompt-danger }

## Interesting formatting  

Prepare a square image (PNG, JPG, or SVG) with a size of 512x512 or more, and then go to the online tool [**Real Favicon Generator**](https://realfavicongenerator.net/) and click the button <kbd>Select your Favicon image</kbd> to upload your image file.

In the next step, the webpage will show all usage scenarios. You can keep the default options, scroll to the bottom of the page, and click the button <kbd>Generate your Favicons and HTML code</kbd> to generate the favicon.

The following table will help you understand the changes to the favicon files:

| File(s)             | From Online Tool                  | From Chirpy |
|:--------------------:|:---------------------------------:|:-----------:|
| `*.PNG`             | ✗                                | ¼           |
| `*.ICO`             | ✓                                | ✗           |

>  ✓ means keep, ✗ means delete.
{: .prompt-info }

The Jekyll-Theme-Chirpy has added a lot of things to this file but we will only concentrate on a few to get us started, the changes are needed in the following spots:  

- <mark>timezone:</mark> Whatever matches your locale. (ex. America/New_York)
- <mark>title:</mark> Replace this with your website Title. (ex. Jadehawk's Tech Notes)
- <mark>tagline:</mark> This will be display under  the main title. (ex. A Small Collection Of Tutorials && Notes)
- <mark>url:</mark> This is your Github Pages url (ex. https://jadehawk.github.io)
- <mark>avatar:</mark> A URL to your avatar that will be display on the website.
