---
title: Jira JQL - searching JSM Queries
date: 2024-08-27 09:00:00 +0200
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

**Organisations**  
Organizations are used to group customers and determine which requests they can view in the JSM customer portal.  

`reporter in organizationMembers(organization-name)`  
`organizations = organization-name`  
`organizations in (organization1, organization2)`  

**Service Level Agreements (SLAs)**  
SLAs represent a goal or commitment between service providers and customers.  

`SLA-name = breached()`  
`SLA-name = paused()`  
`SLA-name = running()`  
`SLA-name = completed()`  
`"Time to Resolution" > elapsed("8h")`  
`"Time to Resolution" > remaining("8h")`  