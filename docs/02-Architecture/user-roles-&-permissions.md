# User Roles & Permission

Status: Draft
Version: 1.0
Last Updated: 2026-07-26
Owner: Bhyn

## Purpose

Define who can access, create, modify, and delete information within the platform.

This document applies to all templates and modules.

---

# Design Principles

## Principle 1 — Least Privilege

Users should only see and do what they need.

Example:

- Student should not view financial data.
- Employee should not manage platform settings.
- Teacher should not access another organization's data.

---

## Principle 2 — Organization Isolation

Users only access data belonging to their organization.

Example:

```
Tuition Centre A
    ↓
Only sees Tuition Centre A data

Tuition Centre B
    ↓
Only sees Tuition Centre B data
```

---

## Principle 3 — Role-Based Access Control (RBAC)

Permissions are assigned to roles.

Users receive permissions through their role.

---

# Core Roles

## Owner

Highest permission level.

Responsibilities:

- Manage organization
- Manage billing
- Manage users
- Manage permissions
- Access all records

Typical Examples:

- Business owner
- Tuition centre owner
- Founder

---

## Admin

Manages daily operations.

Responsibilities:

- Manage users
- Manage records
- View reports
- Configure modules

Cannot:

- Transfer ownership
- Access billing settings (optional)

---

## Manager

Department-level management.

Responsibilities:

- Manage assigned users
- Manage tasks
- View reports

Examples:

- Operations manager
- Lead teacher

---

## Staff

Operational user.

Responsibilities:

- Create and update records
- Manage assigned work

Examples:

- Teacher
- Employee
- Tutor

---

## Member

Limited access.

Examples:

- Student
- Customer portal user
- Parent

Can only access authorized information.

---

## Viewer

Read-only access.

Examples:

- Auditor
- Observer
- Consultant

Cannot edit data.

---

# Permission Categories

The platform controls permissions by resource.

Resources:

```
People
Tasks
Events
Documents
Activities
Users
Roles
Settings
Reports
```

---

# Permission Actions

Each resource supports:

```
View
Create
Edit
Delete
Export
```

---

# Permissions Matrix

## People

| Role    | View          | Create | Edit          | Delete | Export |
| ------- | ------------- | ------ | ------------- | ------ | ------ |
| Owner   | Yes           | Yes    | Yes           | Yes    | Yes    |
| Admin   | Yes           | Yes    | Yes           | Yes    | Yes    |
| Manager | Yes           | Yes    | Yes           | No     | Yes    |
| Staff   | Assigned Only | Yes    | Assigned Only | No     | No     |
| Member  | Self Only     | No     | Self Only     | No     | No     |
| Viewer  | Yes           | No     | No            | No     | No     |

---

## Tasks

|         |               |        |                    |        |        |
| ------- | ------------- | ------ | ------------------ | ------ | ------ |
| Role    | View          | Create | Edit               | Delete | Export |
| Owner   | Yes           | Yes    | Yes                | Yes    | Yes    |
| Admin   | Yes           | Yes    | Yes                | Yes    | Yes    |
| Manager | Yes           | Yes    | Yes                | No     | Yes    |
| Staff   | Assigned Only | Yes    | Assigned Only      | No     | No     |
| Member  | Assigned Only | No     | Update Status Only | No     | No     |
| Viewer  | Yes           | No     | No                 | No     | No     |

---

## Events

|         |               |        |               |        |        |
| ------- | ------------- | ------ | ------------- | ------ | ------ |
| Role    | View          | Create | Edit          | Delete | Export |
| Owner   | Yes           | Yes    | Yes           | Yes    | Yes    |
| Admin   | Yes           | Yes    | Yes           | Yes    | Yes    |
| Manager | Yes           | Yes    | Yes           | No     | Yes    |
| Staff   | Assigned Only | Yes    | Assigned Only | No     | No     |
| Member  | Assigned Only | No     | No            | No     | No     |
| Viewer  | Yes           | No     | No            | No     | No     |

---

## Documents

|         |               |        |               |        |        |
| ------- | ------------- | ------ | ------------- | ------ | ------ |
| Role    | View          | Create | Edit          | Delete | Export |
| Owner   | Yes           | Yes    | Yes           | Yes    | Yes    |
| Admin   | Yes           | Yes    | Yes           | Yes    | Yes    |
| Manager | Yes           | Yes    | Yes           | No     | Yes    |
| Staff   | Assigned Only | Yes    | Assigned Only | No     | No     |
| Member  | Assigned Only | No     | No            | No     | No     |
| Viewer  | Yes           | No     | No            | No     | No     |

---

## Users

|         |      |        |      |        |
| ------- | ---- | ------ | ---- | ------ |
| Role    | View | Create | Edit | Delete |
| Owner   | Yes  | Yes    | Yes  | Yes    |
| Admin   | Yes  | Yes    | Yes  | No     |
| Manager | No   | No     | No   | No     |
| Staff   | No   | No     | No   | No     |
| Member  | No   | No     | No   | No     |
| Viewer  | No   | No     | No   | No     |

---

## Roles & Permissions

|        |           |        |      |        |
| ------ | --------- | ------ | ---- | ------ |
| Role   | View      | Create | Edit | Delete |
| Owner  | Yes       | Yes    | Yes  | Yes    |
| Admin  | View Only | No     | No   | No     |
| Others | No        | No     | No   | No     |

---

## Settings

|         |         |
| ------- | ------- |
| Role    | Access  |
| Owner   | Full    |
| Admin   | Limited |
| Manager | No      |
| Staff   | No      |
| Member  | No      |
| Viewer  | No      |

---

# Future Custom Roles

Version 1 uses predefined roles.

Future versions may allow:

```
Create Custom Role
Assign Permissions
Save Role Template
```

Examples:

- Finance Manager
- Academic Coordinator
- CRM Specialist
- Operations Lead

---

# Special Rules

## Rule 1

Users can never access another organization's data.

---

## Rule 2

Owners always retain full access.

---

## Rule 3

Deleted records should be soft deleted.

Example:

```
deleted_at = 2026-07-26
```

Not permanently removed.

---

## Rule 4

Permission checks must occur on:

- Frontend
- Backend
- API

Never rely solely on UI restrictions.

---

# Related Documents

- Product Vision
- Database Schema
- System Architecture
- API Specification
- Template Architecture
