# Automated-Network-Request-Management-in-ServiceNow

A ServiceNow PDI-based solution for automating the end-to-end lifecycle of network service requests — from request submission and approval to fulfillment, SLA tracking, notifications, and closure.

## Project Overview

**Automated Network Request Management in ServiceNow** is designed to improve the efficiency of handling network-related service requests.

The solution replaces manual request handling with a **centralized and standardized ServiceNow workflow**. Users submit requests through the Service Catalog, required information is captured and validated, approvals are routed automatically, fulfillment tasks are assigned to the appropriate network team, and request progress is tracked through ServiceNow.

## Business Objectives

- Reduce manual effort and human error.
- Accelerate network request fulfillment.
- Standardize request and approval processes.
- Provide centralized request visibility and tracking.
- Improve the end-user experience.
- Support IT and security policy compliance.
- Maintain clear and auditable request records.

## Key Features

### 1. Service Catalog Request

Users can submit network-related requests through a ServiceNow Service Catalog item.

Examples:

- VPN access
- Firewall-related requests
- IP/network access
- Other approved network services

### 2. Dynamic Request Form

The catalog form captures the information required to process the request.

- Mandatory fields
- Request category
- Conditional fields
- Basic client-side validation
- Clear user guidance

### 3. Automated Approval

Requests requiring authorization are automatically routed to the appropriate approver.

**Flow:**

`Request Submitted → Approval → Approved / Rejected`

### 4. Automatic Fulfillment Assignment

After approval, the request is routed to the appropriate network fulfillment group.

### 5. SLA Tracking

ServiceNow SLA capabilities can be used to track response and resolution targets.

### 6. Notifications

Automatic notifications keep users and support teams informed about important request events.

Examples:

- Request submitted
- Approval required
- Request approved/rejected
- Request assigned
- Status updated
- Request completed

### 7. Request Tracking

Requesters can view the current status of their requests through ServiceNow.

### 8. Closure and Audit Trail

Completed requests are closed with relevant status information, work notes, and system history.

### 9. Reports & Dashboard

ServiceNow reports and dashboards provide visibility into:

- Total requests
- Open and closed requests
- Request categories
- Priority
- SLA status
- Fulfillment trends


## Conclusion

The **Automated Network Request Management in ServiceNow** project provides a simple and structured way to manage network-related service requests. By using Service Catalog, Flow Designer, approvals, notifications, SLA tracking, and basic JavaScript, the project reduces manual effort and improves request processing.

The solution provides better visibility, faster fulfillment, standardized workflows, and proper tracking of requests from submission to closure.

Overall, this project demonstrates how ServiceNow can be used to automate and manage network request processes efficiently in a ServiceNow PDI environment.
## High-Level Architecture

```text

┌──────────────────────┐
│   Employee / User    │
│      Requester       │
└──────────┬───────────┘
           │
           │ Submit Request
           ▼
┌──────────────────────────────┐
│       ServiceNow PDI         │
│                              │
│  Service Catalog             │
│  Catalog Variables           │
│  Client Scripts              │
│  UI Policies                 │
│  Business Rules              │
│  Flow Designer / Workflow    │
│  Notifications               │
│  SLA                         │
│  Reports & Dashboards        │
└───────┬───────────────┬──────┘
        │               │
        │ Approval      │ Store / Retrieve
        ▼               ▼
┌───────────────┐   ┌──────────────────┐
│    Manager    │   │ ServiceNow       │
│   Approver    │   │ Platform Tables  │
└───────┬───────┘   └──────────────────┘
        │
        │ Approved
        ▼
┌──────────────────────────┐
│ Network Fulfillment Team │
│        Assignee          │
└────────────┬─────────────┘
             │
             │ Update Status
             ▼
       ┌──────────────┐
       │     User     │
       │ Notifications│
       └──────────────┘
--------------------------------------------------------------------------------------------------------------------------
