# MVP Features

Status: Draft
Version: 1.0
Last Updated: 2026-07-26
Owner: Bhyn

## Purpose

Define the minimum viable product (MVP) scope.

This document determines exactly what must be built before Version 1 can be considered complete.

Anything not listed here should be considered out of scope unless explicitly approved.

---

# MVP Goal

Deliver a working multi-tenant tracking platform that allows organizations to:

- Manage people
- Manage tasks
- Manage events
- Manage documents
- Track activities
- Use basic automations

without requiring industry-specific custom development.

---

# MVP Success Criteria

Version 1 is successful if a user can:

1. Create an organization
2. Invite users
3. Manage people
4. Manage tasks
5. Manage events
6. Upload documents
7. View activity history
8. Run basic automations

---

# Must-Have Features

These features are required before launch.

---

## Authentication

### Features

✓ Register

✓ Login

✓ Logout

✓ Password Reset

✓ JWT Authentication

---

## Organizations

### Features

✓ Create Organization

✓ Organization Settings

✓ Organization Isolation

✓ Multi-Tenant Support

---

## Users

### Features

✓ Create User

✓ Edit User

✓ Deactivate User

✓ Assign Role

✓ View User List

---

## Roles & Permissions

### Features

✓ Owner

✓ Admin

✓ Manager

✓ Staff

✓ Member

✓ Viewer

✓ Permission Enforcement

---

## People Management

### Features

✓ Create Person

✓ Edit Person

✓ View Person

✓ Delete Person (Soft Delete)

✓ Search People

---

## Task Management

### Features

✓ Create Task

✓ Edit Task

✓ Assign Task

✓ Complete Task

✓ Delete Task

✓ Task Filtering

---

## Event Management

### Features

✓ Create Event

✓ Edit Event

✓ Delete Event

✓ Event Listing

---

## Document Management

### Features

✓ Upload Document

✓ View Document

✓ Delete Document

✓ Document Listing

---

## Activity Tracking

### Features

✓ Activity Logging

✓ Activity Timeline

✓ Activity Search

---

## Dashboard

### Features

✓ Recent Activities

✓ Upcoming Tasks

✓ Upcoming Events

✓ Summary Metrics

---

## Automation

### Features

✓ Event Triggers

✓ Webhook Support

✓ n8n Integration

✓ Failure Logging

✓ Activity Logging

---

# Should-Have Features

Build if time allows.

---

## Advanced Search

Examples:

```text id="x8w3mj"
Search Tasks

Search Documents

Search Activities
```

---

## Dashboard Widgets

Additional metrics and visualizations.

---

## User Invitation Emails

Automatic onboarding emails.

---

## Saved Filters

Users can save commonly used searches.

---

# Nice-To-Have Features

Not required for launch.

---

## Dark Mode

---

## Custom Branding

Organization logo and colors.

---

## Profile Photos

---

## File Previews

Preview supported documents.

---

# MVP Screens

Required Screens:

```text id="h4v7pq"
Login

Register

Dashboard

People

Tasks

Events

Documents

Activities

Users

Settings
```

---

# MVP APIs

Required:

```text id="j6n2tw"
Authentication

Organizations

Users

Roles

People

Tasks

Events

Documents

Activities

Dashboard
```

---

# MVP Database Tables

Required:

```text id="k9r5xm"
organizations

users

roles

people

tasks

events

documents

activities
```

---

# MVP Integrations

Required:

```text id="m3v8qd"
PostgreSQL

n8n
```

---

Optional:

```text id="p7w1nk"
Email Provider
```

---

# Launch Checklist

## Platform

✓ Authentication Works

✓ Multi-Tenant Isolation Works

✓ Permissions Work

✓ CRUD Operations Work

✓ Activity Logging Works

✓ Automations Work

---

## Security

✓ Password Hashing

✓ JWT Validation

✓ Authorization Checks

✓ Tenant Validation

---

## Testing

✓ Core User Flows

✓ API Testing

✓ Permission Testing

✓ Tenant Isolation Testing

---

# Definition of Done

Version 1 is complete when:

- All Must-Have features are implemented.
- All critical bugs are fixed.
- Multi-tenant security is verified.
- Documentation is updated.
- Users can successfully complete core workflows.

---

# Out of Scope

Refer to:

```text id="r5j9mw"
Non-Goals Document
```

for features explicitly excluded from Version 1.

---

# Related Documents

- Product Vision
- System Architecture
- Database Schema
- API Specification
- Template Architecture
- Non-Goals
- Future Features
