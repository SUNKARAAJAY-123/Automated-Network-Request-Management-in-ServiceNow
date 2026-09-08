# Automated Network Request Management in ServiceNow

A ServiceNow PDI-based project designed to automate and simplify the complete lifecycle of network-related service requests, from request submission and validation to approval, fulfillment, tracking, notifications, and closure.

## 🔗 ServiceNow Project

The project is developed and demonstrated using a ServiceNow Personal Developer Instance (PDI).

**ServiceNow PDI:**

[Open ServiceNow PDI](YOUR_SERVICENOW_PDI_LINK_HERE)

> **Note:** Access to the ServiceNow instance may require valid credentials and appropriate permissions. Do not publish usernames, passwords, API keys, or other confidential information.

## 🎥 Demo Video

The complete project demonstration is available here:

[Watch Project Demo Video](YOUR_DEMO_VIDEO_LINK_HERE)

Replace the placeholder with your actual YouTube, Google Drive, or other demo video link.

## 📌 Project Overview

**Automated Network Request Management in ServiceNow** is an IT service automation project developed to improve the handling of network-related service requests.

The system allows users to submit network requests through the ServiceNow Service Catalog. The submitted request is validated and processed through automated workflow logic using Flow Designer. The workflow can handle request information, approval processing, notifications, assignment, status updates, SLA tracking, and request closure.

The project aims to reduce manual intervention, improve request visibility, standardize request processing, and maintain organized and auditable request records.

## 🎯 Problem Statement

Traditional network request handling can involve several manual activities such as request submission, information verification, approval coordination, communication between users and IT teams, assignment, and status updates.

This can result in:

- Delayed request processing.
- Manual approval tracking.
- Incomplete or inconsistent request information.
- Incorrect assignment.
- Limited request status visibility.
- Repeated manual communication.
- Difficulty tracking SLA targets.
- Increased administrative effort.
- Difficulty maintaining an audit trail.

This project addresses these challenges by implementing a centralized and automated network request management process in ServiceNow.

## 🎯 Project Objectives

The main objectives of this project are:

- Create a standardized Network Request catalog item.
- Provide a simple request submission form.
- Capture required requester and network information.
- Validate required request information.
- Dynamically control form fields.
- Automate request processing using Flow Designer.
- Implement approval processing.
- Automatically assign approved requests to the network fulfillment team.
- Send notifications during important request stages.
- Track request status and SLA information.
- Provide reports and dashboards.
- Improve request visibility and auditability.

## 🏗️ Project Workflow

The complete request processing workflow is:

```text
Requester
    ↓
Service Catalog
    ↓
Network Request Form
    ↓
Request Validation
    ↓
Flow Designer
    ↓
Create / Update Request Record
    ↓
Approval
    ↓
Approval Decision
    ↓
 ┌───────────────┐
 │               │
Approved       Rejected
 │               │
 ↓               ↓
Assign          Update
Network Team    Request
 │               │
 ↓               ↓
Fulfillment    Notify User
 │
 ↓
SLA Tracking
 │
 ↓
Status Update
 │
 ↓
Request Completion
 │
 ↓
Closure
```

## 🛠️ Technology Stack

| Technology / ServiceNow Feature | Purpose |
|---|---|
| ServiceNow | IT Service Management platform |
| ServiceNow PDI | Development and demonstration environment |
| Service Catalog | Network request submission |
| Catalog Item | Provides the Network Request form |
| Catalog Variables | Captures request information |
| Variable Sets | Stores reusable requester information |
| UI Policies | Controls dynamic form behavior |
| Client Scripts | Provides basic form validation and behavior |
| Business Rules | Provides simple server-side automation |
| ServiceNow Tables | Stores request information |
| Flow Designer | Automates request processing |
| Approval Engine | Handles request approval |
| Email Notifications | Communicates request updates |
| SLA | Tracks response and resolution targets |
| Reports & Dashboards | Provides request visibility |

## 🔧 ServiceNow Configuration

The project uses standard ServiceNow configuration components to build the automated request process.

### 1. Network Request Table

A request table can be configured to store information generated through the Network Request process.

The table can maintain:

- Request number
- Requested by
- Requested for
- Request type
- Business justification
- Network details
- Required date
- Priority
- Approval status
- Assignment group
- Assigned to
- Request state
- Work notes
- Closure information

The request number provides a unique reference for identifying and tracking each network request.

### 2. Request Table Fields

The request record contains information required to process and track the request.

| Field | Purpose |
|---|---|
| Request Number | Unique request identification |
| Requested For | Identifies the user |
| Request Type | Identifies the type of network request |
| Business Justification | Reason for the request |
| Network Details | Required network information |
| Required Date | Required service date |
| Priority | Request priority |
| Approval Status | Approval result |
| Assignment Group | Network fulfillment group |
| Assigned To | Person handling the request |
| State | Current request status |
| Work Notes | Processing information |
| Close Notes | Completion information |

### 3. Approval Configuration

Requests that require authorization are routed to the appropriate approver.

```text
Request Submitted
       ↓
Approval Requested
       ↓
 ┌────────────┐
 ↓            ↓
Approved    Rejected
 ↓            ↓
Network      Notify
Team         User
 ↓
Fulfillment
```

## 🛒 Service Catalog

### Network Request Catalog Item

A **Network Request** catalog item is used to allow users to submit network-related requests.

### Catalog Item Configuration

| Property | Value |
|---|---|
| Name | Network Request |
| Catalog | Service Catalog |
| Category | Network |
| Purpose | Network request submission |

The catalog item provides a structured interface for collecting the information required to process the request.

## 📝 Catalog Variables

The Network Request catalog item can contain variables for collecting request and network-related information.

| Variable | Type | Purpose |
|---|---|---|
| Request Type | Choice | Selects the network request type |
| Business Justification | Multi Line Text | Captures the reason for the request |
| Network Details | Multi Line Text | Captures network/access information |
| Required Date | Date | Captures the required date |
| Additional Information | Multi Line Text | Captures extra details |
| Requested For | Reference | Identifies the requested user |

Example request types may include:

- VPN Access
- Firewall-related Request
- IP / Network Access
- Other Approved Network Service

The variables help ensure that required information is collected in a standardized format.

## 👤 Variable Set / Requester Information

A reusable requester information section can be used to collect user details.

Example information includes:

| Variable | Type | Purpose |
|---|---|---|
| Opened on behalf of | Reference | Selects the user |
| Email ID | Single Line Text | Stores user email |
| User Name | Single Line Text | Stores user name |
| Phone Number | Single Line Text | Stores user phone number |
| Supporting Document | Attachment | Allows supporting document upload |

Requester information can be populated from the selected ServiceNow user record where configured.

```text
Opened on behalf of
        ↓
ServiceNow User Record
        ↓
 ┌──────┼─────────┐
 ↓      ↓         ↓
Email  Name      Phone
```

This reduces manual data entry and improves consistency.

## ⚙️ Dynamic Form Behavior

UI Policies and Client Scripts can be used to provide dynamic behavior on the Network Request form.

### UI Policies

UI Policies can be used to:

- Show fields.
- Hide fields.
- Make fields mandatory.
- Make fields read-only.
- Display relevant fields based on user selections.

For example, when a particular request type is selected, additional fields can be displayed and made mandatory.

### Client Scripts

Basic JavaScript can be used for client-side validation and dynamic form behavior.

Example:

```javascript
function onChange(control, oldValue, newValue, isLoading) {
    if (isLoading) {
        return;
    }

    if (newValue == 'VPN') {
        g_form.setMandatory('access_reason', true);
    }
}
```

The project uses basic JavaScript only where required.

## 🔄 Flow Designer Automation

The main automation is implemented using **ServiceNow Flow Designer**.

### Flow Name

**Network Request**

### Trigger

The flow starts when the **Network Request** catalog item is submitted.

The catalog submission provides the input for the automated workflow.

## Flow Steps

### 1. Service Catalog Trigger

The flow starts when a user submits the Network Request catalog item.

### 2. Get Catalog Variables

The flow retrieves the values submitted through the catalog item.

Example information:

- Request Type
- Business Justification
- Network Details
- Required Date
- Requested For
- Requester Information
- Additional Information

The retrieved values can be used in later Flow Designer actions.

### 3. Create Request Record

A **Create Record** action can create the corresponding backend request record.

```text
Network Request Catalog Item
            ↓
    Get Catalog Variables
            ↓
       Create Record
            ↓
      Request Table
```

### 4. Send Notification

Notifications can be sent to the requester or responsible team during important request stages.

Examples:

- Request submitted.
- Approval required.
- Request approved.
- Request rejected.
- Request assigned.
- Request completed.

### 5. Ask for Approval

The **Ask for Approval** action handles the approval stage.

Possible outcomes include:

- Approved
- Rejected

### 6. Approval Decision

The flow evaluates the approval result.

```text
Ask for Approval
       ↓
   ┌───┴────┐
   ↓        ↓
Approved  Rejected
   ↓        ↓
Update    Update
Record    Record
```

### 7. Update Request Record

The request record is updated according to the approval outcome.

For an approved request, the record continues through the configured fulfillment process.

For a rejected request, the record is updated with the rejection outcome and the requester can be notified.

### 8. Request Fulfillment

Approved requests are assigned to the appropriate network fulfillment group.

The network team processes the request and updates the request status.

### 9. Request Closure

After fulfillment is completed, the request is updated with completion information and closed.

## 👥 User and Group Management

The project uses ServiceNow users and groups to support request processing.

Main participants include:

- Requesters
- Approvers
- Network Fulfillment Team
- IT Administrators

A network fulfillment group can be configured to receive and process approved requests.

Reference fields such as **Assignment Group** and **Assigned To** should use valid ServiceNow group and user records.

## 🔐 Roles and Access

The project follows a simple role-based approach.

| User Type | Responsibility |
|---|---|
| Requester | Submit and track network requests |
| Approver | Review and approve or reject requests |
| Network Team | Process approved network requests |
| Administrator | Configure and monitor the system |

This separation of responsibilities helps maintain an organized request management process.

## 📧 Notifications

Email notifications are used to communicate important information during the request lifecycle.

The notification flow can be represented as:

```text
Request Submitted
       ↓
Approval Required
       ↓
Approved / Rejected
       ↓
Request Processing
       ↓
Request Completed
       ↓
Request Closed
```

Notifications reduce manual follow-up and improve request visibility.

## ⏱️ SLA Management

ServiceNow SLA capabilities can be used to track response and resolution targets.

SLA tracking helps the team to:

- Monitor response time.
- Monitor resolution time.
- Identify delayed requests.
- Track SLA status.
- Support escalation when required.

## 📊 Reports and Dashboards

Reports and dashboards provide visibility into request activity.

Reports can display:

- Total requests
- Open requests
- Closed requests
- Request categories
- Request priority
- Approval status
- SLA status
- Fulfillment trends

A dashboard can provide a centralized view of request volume and SLA performance.

## 📋 Functional Requirements

| ID | Functional Requirement |
|---|---|
| FR-1 | Users can submit network requests through the Service Catalog. |
| FR-2 | The system validates required request information. |
| FR-3 | The system routes requests for approval. |
| FR-4 | Approved requests are assigned to the network fulfillment group. |
| FR-5 | SLA tracking and escalation are supported. |
| FR-6 | Users and teams receive notifications and status updates. |
| FR-7 | Fulfillment teams can update and close completed requests. |
| FR-8 | Administrators can view reports and dashboards. |

## 🔐 Non-Functional Requirements

| ID | Requirement | Description |
|---|---|---|
| NFR-1 | Usability | Simple and user-friendly request submission |
| NFR-2 | Security | Role-based access and ServiceNow ACL controls |
| NFR-3 | Reliability | Consistent request processing |
| NFR-4 | Performance | Efficient forms, scripts, and queries |
| NFR-5 | Availability | Runs on the ServiceNow cloud platform |
| NFR-6 | Scalability | Supports additional request types and request volume |

## 🧪 Testing

The system should be tested by submitting network requests and verifying the behavior of the catalog item, form behavior, workflow, approval, record creation, notifications, SLA, and request closure.

### Test Cases

| Test ID | Test Scenario | Expected Result |
|---|---|---|
| TC01 | Submit a valid Network Request | Request is submitted successfully |
| TC02 | Submit without mandatory information | Validation prevents incomplete submission |
| TC03 | Select different request types | Relevant fields behave correctly |
| TC04 | Submit request for approval | Approval process starts |
| TC05 | Approve a request | Request continues to fulfillment |
| TC06 | Reject a request | Request reflects rejection |
| TC07 | Verify backend request record | Corresponding record is created |
| TC08 | Verify notification | Configured notification is generated |
| TC09 | Verify request status | Status reflects current processing stage |
| TC10 | Verify assignment | Request is assigned to the appropriate team |

### User Acceptance Testing

UAT can involve representatives from:

- Requester
- Approver
- Network Fulfillment Team
- IT Administrator

The purpose of UAT is to confirm that the solution meets the expected requirements.

## 📸 Screenshots

Screenshots can be organized in the repository under a `Screenshots` directory.

Suggested folders:

```text
Screenshots/
├── 01_Project_Setup/
├── 02_Service_Catalog/
├── 03_Catalog_Variables/
├── 04_Variable_Set/
├── 05_UI_Policies/
├── 06_Client_Scripts/
├── 07_Flow_Designer/
├── 08_Approvals/
├── 09_Notifications/
├── 10_SLA/
├── 11_Reports_Dashboard/
└── 12_Testing/
```

Screenshots should demonstrate important parts of the implementation, including:

- ServiceNow PDI setup
- Network Request catalog item
- Catalog variables
- Request form
- UI Policies
- Client Scripts
- Flow Designer
- Approval
- Notifications
- SLA
- Request record
- Reports and dashboard
- Testing results

## 📁 Repository Structure

A simple repository structure can be:

```text
automated-network-request-management-servicenow/
│
├── README.md
│
├── Documentation/
│   └── Project_Documentation.pdf
│
├── Screenshots/
│   ├── 01_Project_Setup/
│   ├── 02_Service_Catalog/
│   ├── 03_Catalog_Variables/
│   ├── 04_Variable_Set/
│   ├── 05_UI_Policies/
│   ├── 06_Client_Scripts/
│   ├── 07_Flow_Designer/
│   ├── 08_Approvals/
│   ├── 09_Notifications/
│   ├── 10_SLA/
│   ├── 11_Reports_Dashboard/
│   └── 12_Testing/
│
├── Configuration/
│   ├── Catalog/
│   ├── Flows/
│   ├── Tables/
│   └── Security/
│
└── Test_Data/
    └── test_cases.md
```

## 📈 Key Benefits

The solution provides:

- Reduced manual intervention.
- Standardized network request submission.
- Automated request processing.
- Improved approval management.
- Better request visibility.
- Consistent information collection.
- Faster communication.
- Better request tracking.
- Improved auditability.
- Maintainable workflow automation.

## 🚧 Challenges Faced

During development, common ServiceNow configuration and workflow challenges may include:

### 1. Reference Field Configuration

Fields such as **Assignment Group** and **Assigned To** are reference fields. Valid ServiceNow group and user records must be selected.

### 2. Auto-Population

Requester information may require reference fields and dot-walking so that information such as name, email, and phone can be retrieved from the selected user record.

### 3. Dynamic Field Visibility

UI Policies can be configured to control field visibility and mandatory behavior based on user selections.

### 4. Flow Designer Record References

Reference fields used in Flow Designer require the correct ServiceNow record references.

### 5. Flow Execution and Testing

The flow should be tested to verify that catalog submission starts the automation, request information is processed correctly, approval is handled, and records are updated according to the workflow outcome.

## 📚 Learning Outcomes

This project provides practical experience with:

- ServiceNow Administration
- ServiceNow Development
- Service Catalog
- Catalog Items
- Catalog Variables
- Variable Sets
- Reference Fields
- ServiceNow Tables
- UI Policies
- Client Scripts
- Basic JavaScript
- Flow Designer
- Approval Workflows
- Email Notifications
- User and Group Management
- SLA Management
- Request Lifecycle Management
- Workflow Automation
- Testing and Troubleshooting
- Reports and Dashboards

## 🗺️ Implementation Roadmap

### Phase 1 — Requirement Analysis

- Identify network request types.
- Identify stakeholders.
- Define business objectives.
- Define request workflow.
- Identify approval requirements.

### Phase 2 — Service Catalog and Form

- Create Network Request catalog item.
- Configure variables.
- Add mandatory fields.
- Configure UI Policies.
- Configure Client Scripts.

### Phase 3 — Workflow Automation

- Create Flow Designer flow.
- Configure approval.
- Configure assignment.
- Configure notifications.
- Configure SLA.

### Phase 4 — Testing

- Perform functional testing.
- Perform end-to-end testing.
- Test different request scenarios.
- Perform UAT.
- Fix identified issues.

### Phase 5 — Deployment

- Prepare deployment checklist.
- Move configuration using appropriate ServiceNow deployment mechanisms such as Update Sets.
- Validate the target environment.
- Monitor the solution after deployment.

> **Note:** Development and testing are performed in the ServiceNow PDI. Production deployment should only be claimed when a separate target/production environment is available.

## 🚀 Future Enhancements

The project can be further enhanced with:

- SLA-based request tracking.
- Advanced approval routing.
- Automated fulfillment task creation.
- CMDB integration.
- REST integration with network management systems.
- Automated network configuration verification.
- ServiceNow reports and dashboards.
- Advanced role-based access control.
- Request analytics and performance monitoring.
- Enhanced audit and compliance reporting.
- Mobile request experience.
- Chat-based request submission.

## 🎓 Project Context

This project is designed as a practical ServiceNow IT Service Management automation project.

The implementation demonstrates how ServiceNow can combine Service Catalog, Catalog Variables, Variable Sets, UI Policies, Client Scripts, Business Rules, Flow Designer, approvals, notifications, SLA, and reporting to automate a network request lifecycle.

## 👨‍💻 Project Information

| Detail | Information |
|---|---|
| Project Title | Automated Network Request Management in ServiceNow |
| Platform | ServiceNow |
| Environment | ServiceNow Personal Developer Instance (PDI) |
| Service Catalog Item | Network Request |
| Automation Tool | Flow Designer |
| Development | ServiceNow Configuration + Basic JavaScript |
| Project Type | IT Service Management / Network Request Automation |
| Status | Completed / In Development |

## 📄 Documentation

Detailed project documentation can include:

- Requirement Analysis
- Ideation Phase
- Problem Statements
- Problem-Solution Fit
- Proposed Solution
- Solution Architecture
- Data Flow Diagram
- User Stories
- Functional Requirements
- Non-Functional Requirements
- Technology Stack
- Sprint Planning
- Project Development
- Testing
- Deployment

## ⭐ Project Objective

The main objective of this project is to automate the complete network request lifecycle in ServiceNow, from request submission to validation, approval, fulfillment, tracking, notification, and closure.

The solution helps make network request processing **faster, standardized, transparent, and auditable**.

## 📌 Conclusion

The **Automated Network Request Management in ServiceNow** project demonstrates how ServiceNow can be used to automate and standardize network request processing.

By combining Service Catalog, Catalog Variables, Variable Sets, dynamic form behavior, request records, approval processing, email notifications, SLA tracking, and Flow Designer automation, the solution provides a structured approach for managing network requests.

The automated workflow reduces manual intervention, improves request visibility, supports approval management, and provides a consistent request lifecycle from submission to closure.

The project also demonstrates practical skills in ServiceNow administration, development, workflow automation, configuration, testing, troubleshooting, and IT service management.

## ⭐ Project Status

**Completed / In Development**

The project is developed and tested in a ServiceNow Personal Developer Instance.

## 📄 License

This project is intended for **academic, learning, demonstration, and portfolio purposes**.
