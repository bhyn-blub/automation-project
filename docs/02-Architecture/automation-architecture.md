# Automation Architecture

Status: Draft
Version: 1.0
Last Updated: 2026-07-26
Owner: Bhyn

## Purpose

Define how automation works throughout the platform.

Automation is a core capability of the platform and allows organizations to automatically respond to events without manual intervention.

Examples:

- Send reminders
- Create follow-up tasks
- Notify users
- Update records
- Trigger workflows

---

# Vision

Every important action in the platform should be capable of triggering automation.

Example:

```text
Task Created
    ↓
Automation Triggered
    ↓
Email Sent
```

---

# Core Concepts

The automation system is built around three concepts:

## Trigger

Something happened.

Examples:

```text
Person Created
Task Created
Task Updated
Task Completed
Event Created
Document Uploaded
```

---

## Conditions

Rules that determine whether automation should continue.

Examples:

```text
Task Priority = High

Person Category = Customer

Task Status = Overdue
```

---

## Actions

What happens next.

Examples:

```text
Send Email
Create Task
Update Status
Log Activity
Notify User
```

---

# Architecture Overview

```text
User Action
    ↓
FastAPI
    ↓
Database Update
    ↓
Activity Logged
    ↓
Automation Event Published
    ↓
n8n Workflow Triggered
    ↓
Action Executed
```

---

# Event Flow

## Example: Task Created

Step 1

User creates task.

---

Step 2

Task saved to database.

```text
tasks
```

---

Step 3

Activity recorded.

```text
Task Created
```

saved to:

```text
activities
```

---

Step 4

Automation event generated.

```json
{
  "event": "task.created",
  "organization_id": "xxx",
  "task_id": "xxx"
}
```

---

Step 5

n8n receives webhook.

---

Step 6

Workflow executes.

Example:

```text
Send Email
```

---

# Event Naming Convention

Use consistent names.

Format:

```text
resource.action
```

Examples:

```text
person.created
person.updated

task.created
task.updated
task.completed

event.created
event.updated

document.uploaded
```

---

# Version 1 Triggers

## People

```text
person.created
person.updated
```

---

## Tasks

```text
task.created
task.updated
task.completed
```

---

## Events

```text
event.created
event.updated
```

---

## Documents

```text
document.uploaded
```

---

# Version 1 Actions

## Send Email

Example:

```text
Task Assigned
↓
Send Email
```

---

## Create Task

Example:

```text
Lead Created
↓
Create Follow-Up Task
```

---

## Update Status

Example:

```text
Payment Received
↓
Mark Account Active
```

---

## Log Activity

Example:

```text
Automation Executed
↓
Record Activity
```

---

# n8n Integration

## Purpose

n8n acts as the workflow engine.

The platform handles:

- Users
- Data
- Security
- Permissions

n8n handles:

- Workflow logic
- External integrations
- Notifications

---

# Communication Method

Version 1:

```text
FastAPI
↓
Webhook
↓
n8n
```

---

# Webhook Structure

Example:

```json
{
  "event": "task.created",
  "organization_id": "org_123",
  "task_id": "task_456",
  "timestamp": "2026-07-26T12:00:00Z"
}
```

---

# Activity Integration

Every automation action should create activity records.

Example:

```text
Task Created
↓
Automation Triggered
↓
Reminder Sent
```

Timeline:

```text
09:00 Task Created

09:01 Automation Triggered

09:01 Reminder Email Sent
```

---

# Failure Handling

Automation failures must not break the platform.

Bad:

```text
Task Created
↓
Email Failure
↓
Task Creation Fails
```

---

Good:

```text
Task Created
↓
Email Failure
↓
Task Still Created
↓
Failure Logged
```

---

# Retry Strategy

Version 1:

```text
Attempt 1

Attempt 2

Attempt 3
```

If all fail:

```text
Mark Failed
Log Activity
```

---

# Security Rules

## Rule 1

Never expose database credentials to n8n.

---

## Rule 2

All automation requests must be authenticated.

---

## Rule 3

Validate organization ownership before workflow execution.

---

## Rule 4

Never allow automations to access another organization's data.

---

# Future Automation Features

Not Version 1.

Examples:

```text
Visual Workflow Builder

Conditional Branching

Scheduled Automations

Approval Workflows

AI-Powered Automations

Marketplace Templates
```

---

# Version 1 Scope

Build:

✓ Trigger Events

✓ Webhooks

✓ n8n Integration

✓ Activity Logging

✓ Retry Logic

✓ Failure Logging

Do Not Build:

✗ Workflow Builder

✗ Drag-and-Drop Automation Editor

✗ AI Automation Generator

✗ Automation Marketplace

✗ Cross-Organization Workflows

---

# Success Criteria

An automation system is considered successful when:

- Events trigger reliably
- Workflows execute consistently
- Failures are logged
- Users can trust automations
- Platform performance remains unaffected

---

# Related Documents

- Product Vision
- Database Schema
- User Roles & Permissions Matrix
- System Architecture
- API Specification
- Template Architecture
