# Entity Relationship Diagram (ERD)

Status: Draft
Version: 1.0
Last Updated: 2026-07-26
Owner: Bhyn

## Purpose

Provide a visual representation of the Version 1 database structure.

This diagram is the source of truth for table relationships before implementation in PostgreSQL.

---

# Version 1 ERD

```text
┌─────────────────────┐
│   organizations     │
├─────────────────────┤
│ id (PK)             │
│ name                │
│ slug                │
│ status              │
│ created_at          │
│ updated_at          │
└─────────┬───────────┘
          │
          │ 1
          │
          │
          ▼
          N

┌─────────────────────┐
│      users          │
├─────────────────────┤
│ id (PK)             │
│ organization_id(FK) │
│ role_id (FK)        │
│ email               │
│ password_hash       │
│ first_name          │
│ last_name           │
│ status              │
└───────┬───────┬─────┘
        │       │
        │       │
        │       ▼
        │
        │
        │
        ▼

┌─────────────────────┐
│      roles          │
├─────────────────────┤
│ id (PK)             │
│ organization_id(FK) │
│ name                │
│ description         │
└─────────────────────┘


┌─────────────────────┐
│      people         │
├─────────────────────┤
│ id (PK)             │
│ organization_id(FK) │
│ first_name          │
│ last_name           │
│ email               │
│ phone               │
│ category            │
│ status              │
└───────┬─────────────┘
        │
        │
        ▼

┌─────────────────────┐
│      tasks          │
├─────────────────────┤
│ id (PK)             │
│ organization_id(FK) │
│ assigned_user_id FK │
│ related_person_idFK │
│ title               │
│ status              │
│ priority            │
│ due_date            │
└─────────────────────┘


┌─────────────────────┐
│      events         │
├─────────────────────┤
│ id (PK)             │
│ organization_id(FK) │
│ title               │
│ start_time          │
│ end_time            │
│ location            │
└─────────────────────┘


┌─────────────────────┐
│    documents        │
├─────────────────────┤
│ id (PK)             │
│ organization_id(FK) │
│ uploaded_by (FK)    │
│ file_name           │
│ file_url            │
│ file_type           │
└─────────────────────┘


┌─────────────────────┐
│    activities       │
├─────────────────────┤
│ id (PK)             │
│ organization_id(FK) │
│ user_id (FK)        │
│ object_id           │
│ object_type         │
│ action_type         │
│ created_at          │
└─────────────────────┘
```

---

# Relationship Summary

## Organization Relationships

One organization has many:

- Users
- Roles
- People
- Tasks
- Events
- Documents
- Activities

Relationship:

```text
organizations (1)
      ↓
      ↓
      ↓
      N
all other tables
```

---

## Role Relationships

One role can be assigned to many users.

```text
roles (1)
    ↓
    N
users
```

---

## User Relationships

One user can:

- Own many tasks
- Upload many documents
- Generate many activities

```text
users (1)
    ↓
    N
tasks

users (1)
    ↓
    N
documents

users (1)
    ↓
    N
activities
```

---

## People Relationships

One person can be associated with many tasks.

Examples:

- Customer follow-ups
- Student assignments
- Parent meetings

```text
people (1)
    ↓
    N
tasks
```

---

# Primary Keys

All tables use:

```text
UUID
```

Example:

```text
550e8400-e29b-41d4-a716-446655440000
```

---

# Foreign Keys

## users

```text
organization_id
role_id
```

---

## roles

```text
organization_id
```

---

## people

```text
organization_id
```

---

## tasks

```text
organization_id
assigned_user_id
related_person_id
```

---

## events

```text
organization_id
```

---

## documents

```text
organization_id
uploaded_by
```

---

## activities

```text
organization_id
user_id
```

---

# Index Requirements

Create indexes on:

```text
organization_id
```

for every table.

---

Additional indexes:

```text
users.email

tasks.status

tasks.due_date

activities.created_at
```

---

# Database Rules

Rule 1

Every table contains:

```text
organization_id
```

except organizations.

---

Rule 2

No cross-organization relationships.

---

Rule 3

Use soft deletion where appropriate.

---

Rule 4

Activities are append-only.

Never edit historical activity records.

---

# Version 1 Scope

Included:

✓ organizations

✓ users

✓ roles

✓ people

✓ tasks

✓ events

✓ documents

✓ activities

Excluded:

✗ billing

✗ attendance

✗ notifications

✗ automations

✗ custom_fields

✗ integrations

These will be introduced in future versions.

---

# Related Documents

- Product Vision
- Database Schema
- System Architecture
- Multi-Tenant Architecture
- API Specification
