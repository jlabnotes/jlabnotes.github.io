---
title: Global Loop advanced workflow in Jira
date: 2021-02-21  09:00:00 +0200
categories: [WORKFLOWS]
tags: [events,automation]
img_path: /assets/images/glaw/
---

# How to create a global loop transition?
Let’s start with a simple workflow

![simple workflow](glaw01.png)

For the purpose of this article, let’s use the following use case scenario:

_I need a global loop transition so I will be able to initiate an automation on every status._

If I wanted this to be possible for only one status then I would use a local looping transition on only one status. In many use case scenarios this is enough. 

![loop transition](glaw02.png)

In my scenario, I want this special ‘Take over’ transition to be possible on every transition. I am not going to create four local looping transitions because I have four statuses. That is why I need a global loop transition and here is how you can do it too.

![transition screen](glaw03.png)

Add a new global transition following the steps:

1. click Add transition (1)
2. then select options From status: Any status (2)
3. select option To status: Itself (3).
4. finally give the transition a name. When you click Add, you will see the additional and separate transition available.

![global loop transition](glaw04.png)

# Adding a special Event

The simplest use case on how to use the global loop is to secure the editing of fields for some users.

All you have to do is to place a secured field on a special transition screen which you hide from not authorized users with a workflow condition.

In this article I wanted to show you a more advanced scenario - with Automation for Jira initiated by a special Jira event. The procedure described below will work only for Jira Server, because you cannot (yet?) assign Jira events to Automation for Jira Cloud.

Let’s start from adding a new event in Jira. Go to Jira Administration / System / Event and add a new event. See the example below.

![adding event](glaw07.png)

Later on go to your workflow with a global loop transition and replace a generic event with a newly created event in your post-functions.

![adding event](glaw08.png)

Now your workflow with a global loop is ready for linking it with an Automation procedure.

# Using the Global Loop transition with Automation for Jira

In my use case I want to do three changes in one go when I press the Take Over button:

1. Assign the issue to current user
2. Add a comment that the issue has been taken over by a current user
3. Send a notification about this change to a Reporter, if the Reporter is different from a current user.
4. If you use the app Jira for Automation, this is how the Automation could look like.

![automation](glaw09.png)

In the first part of this automation procedure, I declare that the procedure should be initiated only when a special event is triggered - Automation Start added to the workflow post-function.

Then I edit the issue by changing the Assignee to current user and make a note about it in the Comments area: This issue has been taken over by {{initiator.DisplayName}}

In the second part I check if the Reporter is not current user. If not, I want to send a current Reporter an e-mail notification that the issue has been taken over by a different user.

![automation](glaw10.png)

# More information

[More information and tutorials on https://jlabnotes.com](https://jlabnotes.com/)
