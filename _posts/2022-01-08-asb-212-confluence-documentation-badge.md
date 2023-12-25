---
title: ASB-212 Confluence Documentation Pro Skills Notes
date: 2022-01-08 09:00:00 +0200
categories: [CONFLUENCE]
tags: [badge,acp]
---

[Using Confluence for Documentation & Knowledge Bases: Skillbuilder](https://enable.atlassian.com/student/page/817160-using-confluence-for-documentation-and-knowledge-bases-asb-212-course-description)

# Using Confluence to build documentation space

Good documentation space:
- self-explanatory, no user-guide needed
- searchable
- easy to read, well designed, well presented
- targeted at your audience - meet their needs
- well maintained - no scroll intensive, difficult to understand

Consider the audience before you start  
Page hierarchy no more than 4-5 layers - more will be difficult to find  
Do not create too many spaces  
Reuse existing space when possible

To create a space you need a global permission 'create space'  
To make content easy to find:
1. reduce the amount of content on one page
2. move information to the first hierarchy level
3. avoid the need to scrolling TLDR - too long did not read

## Templates and Blueprints

Confluence has:
- documentation space blueprints
- page level blueprints: how to articles and troubleshooting articles
- templates which you can generate yourself

You can change the blueprint and the template content on a space level (space administrator) or for the whole confluence (confluence administrator).   

## Space settings

Make sure that the space key does not have to be changed.  
It is not easy to change the space key.  
You can give the space a category. They group the spaces in a catalog.  

Page level permissions:
- can view
- can view and edit
- has no access  

Page permissions marked by the red lock

Space level permissions are much more granular.  
Delete permission should be given only to certain people.  
Deleted content can be retrieved but it is an overhead.  

## Making a Space publicly accessible
Making Space externally accessible is difficult from the security point of view.

Giving the access:
1. Go to Confluence Administration and edit global permissions
2. Check 'can use' for anonymous access
3. In the context of documentation/knowledge base, giving the permission 'view user profiles' is not desirable.
4. In space, go to permissions and to Anonymous access section
5. Decide which permissions you want to give, most likely only the View permission
6. You can't grant 'space admin' and 'restrict' permissions to anonymous users

Links between Confluence and Service Desk
-----------------------------------------
- relieve pressure on your support team
- create a self service support system
- identify gaps in documentation
- identify gaps in functionality

Exporting Content
----------------------
- Single Page export - only published content is exported
- Space Export

|       | PDF Export | XML Export | HTML export |
|-------|:----------:|:-----------:|:------------:|
| Pages |    Yes     |    Yes     |    Yes      |
| Blogs |    No     |    Yes     |    No      |
| Comments |    No     |    Option     |    Option      |
| Attachments |    Images     |    Yes     |    Yes      |  
| Unpublished Changes |    No     |    Yes     |    No      |
| Restricted pages |    When you can view     |    Yes, restricted too     |    When you can view      |
| Trash |    No     |    Yes     |    No      |
| Download as |  PDF    |    ZIP     |    ZIP      |
| Team Calendars |    No     |    No     |    No      |

PDF Export - Generates a PDF file for each page in this space, excluding blogs. Comments are excluded and attachments as pictures on a page.

HTML Export - Generates a HTML file for each page in this space, excluding blogs. Comments and attachments are optional.

XML Export - Generates an XML file for each page in this space, including those not visible to you. The export includes comments and attachments, but excludes blog posts.

### Page access request - who can grant access to a restricted page

When a user requests access to a restricted page, Confluence will send an email to up to 5 people who are most likely to be able to grant access, in the following order:

- person who created a page
- people who have contributed to the page in the past from latest to newest
- can see the page and have 'Restrict' or 'Admin' space permission (sorted by last edit date)
- space administrators who can see the page (sorted alphabetically).

### Searching in Confluence
**OR search:** searching for 'marketing' OR 'digital' will show results that contain one of these terms.  
**AND search:** searching for 'marketing' AND 'digital' will show results that contain both of these terms.  
**NOT search:** searching for 'marketing' NOT 'digital' will show results that only contain 'marketing' and do not contain 'digital.' Character minus is also allowed for example butter -cheese
**Group search:** searching for (marketing OR digital) AND content will show results that can contain either 'marketing' or 'digital,' but must contain 'content.'

**Wildcards**
- For example, a search of b?g will show pages that have any of the following words: big, bug, bag, beg, or bog.
- A search of manag* will show pages that have words such as: manage, manager, management, managing, managerial, etc.

> You can combine exact matches, operators, and wildcards in one search query. For example, you can search  manag* AND past? AND ("article" OR "post")  

**Good to know about searching**
1. Confluence ignores common words (stop words) — such as 'and', 'the', 'or', and 'it' — even if they are included within double quotes. For example, searching for "the IT budget" will only return pages containing 'budget', because 'the' and 'it' are stop words.
2. Confluence doesn't allow wildcards at the beginning of your search. You can't search for *hum* or ?hum*, as they begin with a wildcard

### Comments visibility ###
Inline comments with (at)mentions don't appear to viewers until the page is published.  
Any teammate (at)mentioned in a comment won’t be notified until you publish the page.

### Notifications
**Page created/modified notifications**
Who gets notified when a user, John Doe, modifies his page?
1. A person (at)mentioned in the text is notified
2. All watchers of the page are notified
3. All watchers of the site are notified
4. Everybody who liked the page is notified
5. All followers of John Doe are notified

Notifications are sent by e-mail and are available in the workbox button on the main toolbar of the page

### Email settings
__Autowatch__  
Pages and blog posts that you create, edit or comment on will automatically be watched for future changes.

__Subscribe to daily updates__    
You will receive a daily email report summarizing all changes that you have permission to view.

__Subscribe to all blog posts__  
You will receive an email when any blog post is added, even if it is in a space you aren’t watching. You won’t receive emails for comments on those blog posts, or changes to them.

__Subscribe to network__   
You will receive an email when anyone you are following adds or changes content.

__Subscribe to new follower notifications__  
You will receive an email when anyone chooses to follow you.

__Notify on my actions__  
You will receive notifications for changes you make, in addition to other people's changes.

__Show changed content__  
Check this option to see changes made in Edit notification emails.

__Subscribe to recommended updates__  
You will receive an email with recommended items based on comments and likes
