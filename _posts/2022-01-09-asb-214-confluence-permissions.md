---
title: ASB-214 Confluence Permissions Pro Skills Notes
date: 2022-01-09 09:00:00 +0200
categories: [CONFLUENCE]
tags: [badge,acp]
---

[Configuring and Troubleshooting Permissions in Confluence: Skillbuilder](https://enable.atlassian.com/student/page/817161-configuring-and-troubleshooting-permissions-in-confluence-asb-214-course-description)

__Free course notes__

Permission levels:
- global
- space: space-by-space
- content: page-by-page

Global permissions can be added to users and groups

**Global permissions**  
- system administrator
- confluence administrator
- can use Confluence
- create spaces
- personal space

**Default groups:**
- confluence-administrators (the superuser group)
  - superuser group, access all content
  - permissions to this group cannot be modified
  - you cannot delete this group
  - they have system administrator and confluence administrator global permission
- confluence-users
  - created when Confluence is installed
  - possible to delete this group
  - you will not be able to add new users if deleted

**Global permissions:**
1. can-use (Use Confluence)
   1. can log-in (always, even without this permission)
   2. counts toward license count
   3. needed to access any content
   4. it is a pre-requisite to access spaces
   5. you can see all the users with this permission via profile and directory
   6. you can interact with other users
2. can-use permission and anonymous users
   1. needed to be able to access confluence at all
   2. view user profiles can be used to allow or limit interaction with other users
   3. does not consume a license seat
   4. do not have to log in
   5. can access content and spaces based on space permissions
   6. without a can-use global permission, you cannot add a space permission to anonymous
   7. Space permissions such as Restrictions Add/Delete and Space Admin cannot be given to Anonymous users - it is blocked and cannot be changed
   8. By mistake, you can give permissions to Export a space
   9. When a page or content is added to space by anonymous, the author will be Anonymous
3. View user profiles
   1. with this permission, a user can (at)mention other users
   2. without this permission, at mention is only possible with the user who created the page while commenting or editing.

4. Other global permissions
   1. Confluence Administrator permission
      1. can administer the application but is disallowed from operations that may compromise system security.
      2. can create groups
      3. can add users to groups
      4. can manage global permissions
      5. cannot manage or add users the confluence-administrators group
      6. cannot grant system administration permission
   2. System Administrator permission
      1. Has complete control and access to all administrative functions. 
      2. can manage and add users to the confluence-administrators super-group
      3. grant system administration permission to others
   3. Membership in the confluence-administrators **group** will give you more permissions than if you had both system administrator and confluence administrator permissions.
      1. being a member of this group you will not need space-level and page content-level permissions to be able to access them
      2. users with the confluence administrators global permission still need space permissions and page access

**Space related global permissions**  
   1. Personal space
      1. Able to create a personal space for their profile.
   2. Create space
      1. Able to add spaces to the site.

**Space-level permissions**
1. All section - view/delete
   1. view - users can access a space
   2. delete - delete own content even if others have edited it
2. Add - add pages, blogs, attachments and comments
3. Delete - delete pages, blogs, attachments and comments
4. Delete Mail - users can delete mail items archived in the space (related to the Confluence Mail Archiving Plugin) - retrieve, store and browse email within a Confluence space
5. Space Admin - users can administer the space all aspects
6. Space Export - can export the space as XML, HTML or PDF. Without the View permission to certain pages, these pages will not be exported
7. Restrictions Add/delete - add or delete restrictions to pages or blogs
8. Space permissions and page restrictions affect how links between Confluence pages are displayed.
   1. If someone doesn't have 'View' space permission, links to pages in that space won't be shown at all.
   2. If someone has the "View" space permission, but the page has view restrictions, the link will be visible but they'll get an "access denied" message when they click the link. 
   3. Links to attachments - if the visitor doesn't have permission to view the page the attachment lives on, the link won't be rendered.

**Content Restrictions**
1. Inheritance
   1. view restrictions are inherited
   2. edit restrictions are NOT inherited


### Moving Pages permissions

To move a page, you need the following permissions:

- 'Add' permission on the page you're moving,
- 'View' permission on the page's parent page. 
- If you're moving the page to a different parent, you need 'View' permission on the new parent.

To move a page into a different space, you also need:

- 'Delete' permission on the space you're moving from, and
- 'Add' permission on the space you're moving to.

If the page has restrictions, and you want to keep the page restrictions in the new location
- you need 'Restrict' permission on the space you're moving to. 
- Alternatively, remove the page restrictions before performing the move.

### Links visibility
Space permissions and page restrictions affect how links between Confluence pages are displayed.

If someone doesn't have 'View' space permission:
- links to pages in that space will be visible,
- they'll get a "page not found" message
- the space key is not revealed in the link URL.

If someone has the "View" space permission, but the page has view restrictions
- the link will be visible
- they'll get an "access denied" message when they click the link. 

Links to attachments are also affected.  
If the visitor doesn't have permission to view the page the attachment lives on, the link won't be rendered.

To link to a Confluence page from outside Confluence:  
- use the share link which is a permanent URL
- this ensures that the link to the page is not broken if the page name changes.