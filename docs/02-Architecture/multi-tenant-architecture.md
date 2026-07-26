# Multi-Tenant Architecture

Status: Draft
Version: 1.0
Last Updated: 2026-07-26
Owner: Bhyn

## Purpose

Define how multiple organizations share the same platform while keeping all data completely isolated and secure.

This document establishes the foundation for scaling from one organization to thousands.

---

# What is a Tenant?

A tenant is an organization using the platform.

Examples:

```text id="v7t92m"
ABC Tuition Centre

XYZ Marketing Agency

John Freelancer Workspace

Bright Future Academy
```

Each tenant has:

- Users
- People
- Tasks
- Events
- Documents
- Activities

---

# Core Principle

Every piece of data belongs to exactly one organization.

Example:

```text id="r5xmj3"
Organization
    ↓
Owns
    ↓
Users
People
Tasks
Events
Documents
Activities
```

---

# Architecture Strategy

Version 1 uses:

## Shared Database

```text id="v8jnz4"
One PostgreSQL Database
```

with

```text id="84m5yh"
organization_id
```

on every record.

---

Example:

Tasks Table

| id  | organization_id | title          |
| --- | --------------- | -------------- |
| 1   | Org A           | Call Customer  |
| 2   | Org B           | Prepare Lesson |
| 3   | Org A           | Send Invoice   |

Users from Org A only see:

```text id="2u0q9n"
Call Customer
Send Invoice
```

Users from Org B only see:

```text id="g1v2ze"
Prepare Lesson
```

---

# Tenant Identification

Every authenticated user belongs to:

```text id="xj7iq0"
organization_id
```

stored in:

```text id="zmw06g"
users
```

table.

Example:

```text id="q1gc42"
user_id

organization_id

role_id
```

---

# Authentication Flow

```text id="r2it4y"
Login
 ↓
Validate User
 ↓
Get Organization ID
 ↓
Issue JWT
 ↓
User Access Granted
```

---

# JWT Payload

Example:

```json id="qckw48"
{
  "user_id": "123",
  "organization_id": "456",
  "role": "admin"
}
```

Every request carries tenant information.

---

# API Security

Every API request must verify:

## Step 1

User is authenticated.

---

## Step 2

Organization exists.

---

## Step 3

Requested record belongs to user's organization.

Example:

```text id="5uhkgz"
Task Requested
 ↓
Task.organization_id
 =
User.organization_id
```

If not:

```text id="o7g6hn"
403 Forbidden
```

---

# Database Security

Every query must filter by:

```sql
organization_id
```

Example:

```sql
SELECT *
FROM tasks
WHERE organization_id = :current_organization;
```

Never:

```sql
SELECT * FROM tasks;
```

without tenant filtering.

---

# Service Layer Rules

Business logic must always receive:

```text id="upjlwm"
organization_id
```

before performing operations.

Example:

```text id="ob6zgm"
Get Tasks
 ↓
Filter By Organization
 ↓
Return Results
```

---

# Activity Isolation

Activities are tenant-specific.

Example:

Organization A Timeline

```text id="50og38"
Task Created

Document Uploaded

Person Added
```

Organization B cannot access these records.

---

# Document Isolation

Documents belong to one organization.

Example:

```text id="zngoqj"
invoice.pdf
```

uploaded by:

```text id="fyq3i9"
Organization A
```

cannot be viewed by:

```text id="ovb0je"
Organization B
```

---

# Automation Isolation

Automations execute within the tenant context.

Example:

```text id="xgr48o"
Task Created
 ↓
Automation Triggered
 ↓
Send Reminder
```

Only affects records belonging to that organization.

---

# User Invitation Flow

```text id="0f6o3j"
Owner
 ↓
Invite User
 ↓
User Receives Email
 ↓
User Joins Organization
```

New users inherit:

```text id="hz1x2g"
organization_id
```

from inviter.

---

# Organization Ownership

Each organization has:

```text id="uzrjlwm"
One Owner
```

Version 1 supports:

```text id="xfewhf"
Single Owner Model
```

Future versions may support:

```text id="93f4hi"
Multiple Owners
```

---

# Soft Deletion

Organizations should never be immediately deleted.

Instead:

```text id="1zj8v4"
status = inactive
```

or

```text id="cgnt2g"
deleted_at
```

This prevents accidental data loss.

---

# Backup Strategy

Version 1 Requirements:

- Daily database backup
- Weekly full backup verification
- Ability to restore a single organization if required

---

# Security Requirements

## Required

✓ Organization isolation

✓ Role checks

✓ JWT validation

✓ Tenant-aware database queries

✓ Secure password hashing

---

## Forbidden

✗ Cross-tenant data access

✗ Shared documents between organizations

✗ Direct database access from frontend

✗ Trusting frontend organization IDs

---

# Future Enhancements

Not Version 1.

Examples:

```text id="9kn6o8"
Multi-Organization Users

Organization Switching

Enterprise Hierarchies

Cross-Organization Collaboration

White-Label Organizations
```

---

# Version 1 Decision

Chosen Model:

```text id="pijy8n"
Shared Database
+
Shared Application
+
organization_id Isolation
```

Reason:

- Simpler development
- Lower hosting cost
- Easier maintenance
- Suitable for first 1,000+ organizations

---

# Success Criteria

The architecture is successful when:

- Organizations cannot access each other's data.
- Every query is tenant-aware.
- Authentication carries tenant identity.
- Automations remain tenant-scoped.
- New organizations can be created without code changes.

---

# Related Documents

- Product Vision
- Database Schema
- User Roles & Permissions Matrix
- System Architecture
- Automation Architecture
- API Specification
