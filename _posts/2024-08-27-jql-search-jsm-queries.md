---
title: Jira JQL - searching JSM Queries
date: 2026-02-26 09:00:00 +0200
pin: false
categories: [JQL]
tags: [jql-cookbook,jql]
---
## Searching for Jira Service Management fields and values

Jira Service Management has specific fields with specific values, relating only to that Atlassian product.  

## Queries

**Approvals**  
Approvals in Jira Service Management workflows.  

`approvals = approved()`  
`approvals = approver("john smith")`  
`approvals = pending()`  
`approvals = pendingBy("john smith")`  
`approvals = myPendingApproval()`  

**Monitoring and approvals explained**  
*The Approvals* field enables you to return tickets based on their approval status or approver.  
Example: Return all tickets pending approval from Marin.  
`approvals = pendingBy(marin)`

*The Request last activity time* field enables you to return tickets based on the time of their creation. You can use this field with date values, ranges, and functions.  
Example: Return all tickets created between January 1 and January 31, 2024.  
`request-last-activity-time > "2024/01/01" and request-last-activity-time < "2024/01/31"`

*The Request channel type* field enables you to return tickets based on the channel they were submitted through.  
Example: Return all tickets that weren’t submitted through the portal.  
`request-channel-type != portal`

*approved()* function returns all tickets that have been approved.  
Example: Return all tickets that have not been approved.  
`approvals != approved()`

*pending()* function returns all tickets waiting for approval from any user.  
Example: Return all tickets waiting for approval.  
`approvals = pending()`

*The pendingBy()* function returns all tickets waiting for approval from a specific user.  
Example: Return all tickets waiting for approval from Haruki.  
`approvals = pendingBy(haruki)`

*myPendingApproval()* function returns all tickets waiting for approval from the current user.  
Example: Return all tickets waiting for my approval.  
`approvals = myPendingApproval()`

**Organisations**  
Organizations are used to group customers and determine which requests they can view in the JSM customer portal.  

`reporter in organizationMembers(organization-name)`  
`organizations = organization-name`  
`organizations in (organization1, organization2)`  

If your service projects use customer organizations, you can use JQL to find and report on data for specific organizations.  
The *organizationMembers()* function enables you to find tickets associated with a specific organization. The function requires one or multiple organization names as the parameter.  
Example: Return all tickets where the reporter is a member of the ACME customer organization.  
`Reporter IN organizationMembers(“ACME”)`

**Service Level Agreements (SLAs)**  
SLAs represent a goal or commitment between service providers and customers.  

`SLA-name = breached()`  
`SLA-name = paused()`  
`SLA-name = running()`  
`SLA-name = completed()`  
`"Time to Resolution" > elapsed("8h")`  
`"Time to Resolution" > remaining("8h")`  

**SLA explained**  
You can use the name of your SLA as a field in JQL to return information for requests associated with that SLA. Example: Return all tickets that have less than two hours remaining before they breach their Time to resolution SLA.  
`“Time to resolution” < remaining(“2h”)`

*breached()* function returns tickets where the specified SLA is currently or will be breached. 
Example: Return all tickets at risk of breaching their Time to resolution SLA.  
`"Time to resolution" = breached()`

*paused()* function returns tickets where the specified SLA is currently or will be paused.
Example: Return all tickets that use the Time to first response SLA currently paused.  
`“Time to first response” = paused()`

*elapsed()* function returns tickets where the time remaining on a specified SLA has elapsed.
This function will not return tickets when the specified SLA is completed.
Example: Return all tickets that have elapsed their Time to first response SLA by more than two hours.  
`“Time to first response” > elapsed(2h)`

*remaining()* function returns tickets where the time remaining on a specified SLA has more or less time remaining than a value you define.
This function will not return tickets when the specified SLA is completed.
Exampple: Return tickets with more than 12 hours remaining before their Time to resolution SLA breaches.  
`“Time to resolution” > remaining(“12h”)`

*withinCalendarHours()* function returns all tickets where the SLA’s target is active according to its associated calendar.
👉 For example: Return all tickets where the Premier Support SLA is within its calendar hours.  
`"Premier Support SLA" = withinCalendarHours()`