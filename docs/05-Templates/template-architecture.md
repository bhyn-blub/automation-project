# Template Architecture

Status: Draft
Version: 1.0
Last Updated: 2026-07-26
Owner: Bhyn

## Purpose

Define how the platform supports multiple industries using a shared core system.

Templates allow organizations to start with a predefined setup rather than building everything from scratch.

---

# Vision

The platform should not be:

```text id="t1m8xk"
Student App

Teacher App

CRM App

Tuition Centre App
```

Instead, it should be:

```text id="a5v2qd"
Core Platform
+
Templates
+
Modules
```

This allows one codebase to support many use cases.

---

# Core Platform

Every organization receives the same foundation.

Core Objects:

```text id="c7j4pn"
People
Tasks
Events
Documents
Activities
```

These objects are always available.

---

# Template Definition

A template is a predefined configuration that:

- Enables specific modules
- Creates default views
- Creates default roles
- Creates default workflows
- Creates default settings

Templates do not create separate databases.

Templates do not create separate applications.

---

# Architecture Overview

```text id="g3r8vw"
Core Platform
│
├── Student Template
├── Teacher Template
├── Tuition Centre Template
├── Freelancer Template
└── Small Business Template
```

All templates share:

```text id="m9k5tx"
Authentication
Database
API
Automation
Storage
Permissions
```

---

# Template Components

Every template consists of:

## 1. Modules

Examples:

```text id="p4w7nh"
Attendance

CRM

Billing

Assignments

Scheduling
```

---

## 2. Roles

Examples:

Student Template:

```text id="d8c1ql"
Student
Teacher
Admin
```

---

Small Business Template:

```text id="e2v9kp"
Owner
Manager
Employee
```

---

## 3. Views

Examples:

Student Dashboard

```text id="h5r3mb"
Assignments Due

Upcoming Exams

Study Progress
```

---

Business Dashboard

```text id="j7n6yt"
Leads

Tasks

Upcoming Meetings
```

---

## 4. Automations

Examples:

```text id="l1q4cw"
Task Assigned
↓
Email Notification
```

```text id="n8v2jh"
Student Absent
↓
Notify Parent
```

---

# Module System

Modules add functionality to the platform.

---

## Core Modules

Always enabled.

```text id="r3m7pd"
People

Tasks

Events

Documents

Activities
```

---

## Optional Modules

Enabled by template.

```text id="s5j9kf"
Attendance

CRM

Billing

Assignments

Scheduling

Reporting
```

---

# Version 1 Template Structure

Example:

```json id="u7v3nb"
{
  "template_name": "Tuition Centre",
  "modules": ["attendance", "assignments", "scheduling"]
}
```

---

# Student Template

## Target User

Individual student.

---

## Enabled Modules

```text id="w4p8zx"
Assignments

Scheduling
```

---

## Primary Objects

```text id="y2m5qd"
Tasks

Events

Documents
```

---

## Default Dashboard

```text id="z9k1rv"
Assignments Due

Upcoming Classes

Recent Notes
```

---

# Teacher Template

## Target User

Individual tutor or teacher.

---

## Enabled Modules

```text id="b6n3mh"
Assignments

Scheduling

Reporting
```

---

## Default Dashboard

```text id="c8v5jq"
Classes

Student Tasks

Upcoming Events
```

---

# Tuition Centre Template

## Target User

Educational organizations.

---

## Enabled Modules

```text id="e4r7kx"
Attendance

Assignments

Scheduling

Reporting
```

---

## Default Roles

```text id="f2j9wp"
Owner

Admin

Teacher

Student
```

---

## Default Dashboard

```text id="g1m4nb"
Student Count

Today's Classes

Attendance Summary
```

---

# Freelancer Template

## Target User

Solo professionals.

---

## Enabled Modules

```text id="h7v2qd"
CRM

Scheduling
```

---

## Default Dashboard

```text id="i5p8rk"
Clients

Upcoming Work

Outstanding Tasks
```

---

# Small Business Template

## Target User

Businesses with staff.

---

## Enabled Modules

```text id="k3m7qx"
CRM

Scheduling

Reporting
```

---

## Default Roles

```text id="l9v4jw"
Owner

Manager

Employee
```

---

## Default Dashboard

```text id="m6r2ph"
Leads

Tasks

Meetings

Activities
```

---

# Template Selection Flow

During organization setup:

```text id="n4k8ty"
Create Organization
 ↓
Choose Template
 ↓
Apply Configuration
 ↓
Generate Default Setup
```

---

# Changing Templates

Version 1:

```text id="p2v5mc"
Not Supported
```

Reason:

Changing templates introduces complexity.

Organizations should choose a template once during setup.

---

# Custom Template Support

Version 1:

```text id="q8j1hr"
Not Supported
```

Future Version:

```text id="r5m9wk"
Create Custom Template

Save Template

Share Template
```

---

# Design Rules

## Rule 1

Templates never modify core database structure.

---

## Rule 2

Templates only configure behavior.

---

## Rule 3

Templates must remain lightweight.

---

## Rule 4

Every template must operate on the same API.

---

## Rule 5

Modules should be reusable across templates.

Example:

```text id="s7n4qp"
Scheduling
```

can be used by:

- Student
- Teacher
- Tuition Centre
- Freelancer
- Business

---

# Version 1 Scope

Build:

✓ Student Template

✓ Teacher Template

✓ Tuition Centre Template

✓ Freelancer Template

✓ Small Business Template

✓ Module Configuration

Do Not Build:

✗ Template Marketplace

✗ Template Sharing

✗ Custom Template Builder

✗ Third-Party Templates

---

# Success Criteria

The template system is successful when:

- New organizations onboard quickly.
- One platform supports multiple industries.
- Templates require minimal maintenance.
- Modules remain reusable.
- No industry-specific code forks are required.

---

# Related Documents

- Product Vision
- System Architecture
- Database Schema
- Multi-Tenant Architecture
- Automation Architecture
- MVP Features
