# AI-Powered Tax Client Onboarding & Advisor Routing Workflow

An automated onboarding workflow built using **n8n** that streamlines client intake, document validation, complexity assessment, advisor assignment, and advisor notification.

The workflow reduces manual effort by automatically processing client information, identifying missing documents, classifying case complexity, routing clients to the correct advisor queue, maintaining records in Google Sheets, and sending advisor notifications through Gmail.

---

## Problem Statement :

Tax advisory teams often spend significant time on:

- Collecting and validating client information
- Following up for missing documents
- Manually assessing case complexity
- Assigning advisors
- Preparing onboarding summaries
- Maintaining onboarding records

This creates delays, repetitive work, and inconsistent onboarding experiences.

---

## Solution :

This workflow automates the complete onboarding process from client submission to advisor notification.

### Workflow Overview :

```text
Client Submission
       ↓
Extract Form Data
       ↓
Missing Documents Check
       ↓
Complexity Classification
       ↓
Advisor Brief Generation
       ↓
Complexity Routing
       ↓
Advisor Queue Assignment
       ↓
Google Sheets Logging
       ↓
Email Notification
```

---

## Workflow Architecture :

### 1. Webhook Trigger

The workflow starts when a client submits their onboarding information.

The webhook receives the client data and initiates the automation process.

---

### 2. Extract Form Data

This step standardizes incoming client information and extracts relevant fields such as:

- Name
- Email
- Income Type
- Annual Income
- Submitted Documents

This ensures a consistent data structure throughout the workflow.

---

### 3. Missing Documents Check

The workflow evaluates whether all required documents have been provided.

Examples:

- Form 16
- Salary Slips
- Investment Proofs
- Bank Statements
- Capital Gain Statements

Any missing documents are captured and stored for advisor review.

---

### 4. Complexity Classifier

The workflow categorizes each client based on predefined business rules.

Possible categories:

- Standard Case
- Complex Case

Classification may depend on:

- Income level
- Multiple income sources
- Investment activity
- Business income
- Special tax scenarios

---

### 5. Generate Advisor Brief

A structured advisor summary is created containing:

- Client details
- Income information
- Missing documents
- Complexity level
- Recommended action

This eliminates the need for advisors to manually review raw submissions.

---

### 6. Complexity Router

The workflow routes clients based on classification.

```text
Complex Case
      ↓
Senior Advisor Queue

Standard Case
      ↓
Standard Advisor Queue
```

---

### 7. Advisor Queue Assignment

Based on routing logic, the client is assigned to:

#### Senior Advisor Queue

For:

- High-value clients
- Multiple income streams
- Complex tax scenarios
- Advanced advisory requirements

#### Standard Advisor Queue

For:

- Salaried individuals
- Straightforward tax filings
- Standard onboarding cases

---

### 8. Merge Node

Both advisor queues converge into a common processing path.

This ensures a unified downstream workflow regardless of advisor assignment.

---

### 9. Google Sheets Logging

The workflow records onboarding details for tracking and auditing.

Captured fields include:

| Field | Description |
|---------|-------------|
| Timestamp | Submission Time |
| Name | Client Name |
| Email | Client Email |
| Income Type | Income Category |
| Annual Income | Declared Income |
| Complexity | Classification Result |
| Missing Docs | Missing Documents |
| Advisor Queue | Assigned Queue |
| Advisor Brief | Generated Summary |

---

### 10. Gmail Notification

A notification email is sent containing:

- Client information
- Complexity classification
- Missing documents
- Assigned advisor queue
- Advisor brief

This enables advisors to immediately begin client engagement.

---

## n8n Nodes Used :

| Node | Purpose |
|--------|---------|
| Webhook | Receive onboarding submissions |
| Code Node | Extract and transform client data |
| Code Node | Missing document validation |
| Code Node | Complexity classification |
| Code Node | Advisor brief generation |
| IF Node | Routing logic |
| Set Node | Queue assignment |
| Merge Node | Combine routing paths |
| Google Sheets | Store onboarding records |
| Gmail | Send advisor notifications |

---

## Tech Stack :

### Workflow Automation

- n8n Community Edition

### Data Storage

- Google Sheets

### Communication

- Gmail

### Processing

- JavaScript (Code Nodes)

### Integrations

- Webhooks
- Google Workspace

---

## Example Workflow Output :

```json
{
  "name": "Rahul Sharma",
  "email": "rahul@example.com",
  "income_type": "Salary",
  "annual_income": 1200000,
  "complexity": "Standard",
  "missing_docs": ["Form 16"],
  "advisor_queue": "Standard Advisor",
  "advisor_brief": "Salaried client. Missing Form 16. Proceed after document collection."
}
```

---

## Business Impact :

### Before Automation

- Manual onboarding reviews
- Repeated client follow-ups
- Delayed advisor assignment
- Inconsistent summaries
- Increased operational workload

### After Automation

- Faster onboarding process
- Consistent case evaluation
- Automated advisor assignment
- Structured advisor briefs
- Centralized record management
- Reduced manual effort

---


## Future Enhancements :

- WhatsApp Notifications
- CRM Integration
- OCR-Based Document Validation
- Automated Follow-Up Emails
- Multi-Level Advisor Routing
- Dashboard & Analytics Layer
- AI-Based Tax Recommendation Engine

---

