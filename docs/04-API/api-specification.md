# API Specification

Status: Draft
Version: 1.0
Last Updated: 2026-07-26
Owner: Bhyn

## Purpose

Define all Version 1 API endpoints.

This document serves as the contract between:

- Frontend (Next.js)
- Backend (FastAPI)

The frontend should only interact with the backend through these APIs.

---

# API Standards

## Base URL

Development:

```text id="a1d4pf"
http://localhost:8000/api/v1
```

Production:

```text id="s9k2lm"
https://api.yourdomain.com/api/v1
```

---

## Response Format

Success:

```json id="h3w8qn"
{
  "success": true,
  "data": {}
}
```

---

Error:

```json id="b5r7tc"
{
  "success": false,
  "message": "Resource not found"
}
```

---

# Authentication APIs

## Login

```http id="x7f2de"
POST /auth/login
```

Request:

```json id="j4n8vk"
{
  "email": "user@example.com",
  "password": "password"
}
```

Response:

```json id="y2m1qa"
{
  "success": true,
  "token": "jwt_token"
}
```

---

## Register

```http id="m9s6zg"
POST /auth/register
```

---

## Get Current User

```http id="t4c8hr"
GET /auth/me
```

---

## Logout

```http id="n6k3jp"
POST /auth/logout
```

---

# Organization APIs

## Get Organization

```http id="p7w5lu"
GET /organizations/current
```

---

## Update Organization

```http id="q2e9yx"
PATCH /organizations/current
```

---

# User APIs

## List Users

```http id="r5m4tv"
GET /users
```

---

## Get User

```http id="u8j2co"
GET /users/{id}
```

---

## Create User

```http id="v3h7nf"
POST /users
```

---

## Update User

```http id="w9q1dk"
PATCH /users/{id}
```

---

## Deactivate User

```http id="z6b4eg"
DELETE /users/{id}
```

Soft delete only.

---

# Role APIs

## List Roles

```http id="k2n8sm"
GET /roles
```

---

## Get Role

```http id="l7c5px"
GET /roles/{id}
```

---

# People APIs

## List People

```http id="o4r9wb"
GET /people
```

Supports:

```text id="g1u7kh"
Search
Pagination
Filters
```

---

## Get Person

```http id="c3e6yt"
GET /people/{id}
```

---

## Create Person

```http id="d8j1mq"
POST /people
```

Request:

```json id="f2s5na"
{
  "first_name": "John",
  "last_name": "Doe",
  "email": "john@email.com",
  "phone": "12345678",
  "category": "customer"
}
```

---

## Update Person

```http id="h6v9zr"
PATCH /people/{id}
```

---

## Delete Person

```http id="i3w7lf"
DELETE /people/{id}
```

Soft delete only.

---

# Task APIs

## List Tasks

```http id="j5k2nx"
GET /tasks
```

Filters:

```text id="m4y8pq"
Status
Priority
Assigned User
Due Date
```

---

## Get Task

```http id="n1c6sv"
GET /tasks/{id}
```

---

## Create Task

```http id="p8f3dh"
POST /tasks
```

---

## Update Task

```http id="q7m5uk"
PATCH /tasks/{id}
```

---

## Complete Task

```http id="r2v9ge"
POST /tasks/{id}/complete
```

---

## Delete Task

```http id="s6n1wb"
DELETE /tasks/{id}
```

Soft delete only.

---

# Event APIs

## List Events

```http id="t3k7yd"
GET /events
```

---

## Get Event

```http id="u5r2nm"
GET /events/{id}
```

---

## Create Event

```http id="v9c6pl"
POST /events
```

---

## Update Event

```http id="w4j8hs"
PATCH /events/{id}
```

---

## Delete Event

```http id="x2m5qa"
DELETE /events/{id}
```

Soft delete only.

---

# Document APIs

## List Documents

```http id="y8v1nc"
GET /documents
```

---

## Get Document

```http id="z4k7tm"
GET /documents/{id}
```

---

## Upload Document

```http id="a6j2ph"
POST /documents
```

Multipart upload.

---

## Delete Document

```http id="b3r9wd"
DELETE /documents/{id}
```

Soft delete only.

---

# Activity APIs

## List Activities

```http id="c7m4yn"
GET /activities
```

Supports:

```text id="d2v8kp"
Date Range
Object Type
User
```

---

## Get Activity

```http id="e5j1lr"
GET /activities/{id}
```

Read only.

---

# Dashboard APIs

## Dashboard Summary

```http id="f9n6qs"
GET /dashboard
```

Response:

```json id="g4w2dh"
{
  "tasks_due": 12,
  "upcoming_events": 3,
  "recent_activities": 25
}
```

---

# Automation APIs

Version 1:

Internal use only.

No public endpoints.

Automation triggers are generated automatically through platform events.

---

# Security Requirements

## Authentication

Protected endpoints require:

```http id="h8k3zm"
Authorization: Bearer JWT_TOKEN
```

---

## Authorization

Every request validates:

```text id="i6v1pq"
Role
Organization
Permissions
```

---

## Multi-Tenant Protection

Every query must be filtered by:

```text id="j9c4nr"
organization_id
```

---

# HTTP Status Codes

## Success

```text id="k3m7wb"
200 OK
201 Created
204 No Content
```

---

## Client Errors

```text id="l5v2pd"
400 Bad Request
401 Unauthorized
403 Forbidden
404 Not Found
```

---

## Server Errors

```text id="m8j6qh"
500 Internal Server Error
```

---

# Version 1 API Scope

Build:

✓ Authentication

✓ Organizations

✓ Users

✓ Roles

✓ People

✓ Tasks

✓ Events

✓ Documents

✓ Activities

✓ Dashboard

Do Not Build:

✗ Billing APIs

✗ Marketplace APIs

✗ Public Developer APIs

✗ AI APIs

✗ Mobile APIs

---

# Related Documents

- Product Vision
- Database Schema
- ERD Diagram
- System Architecture
- Multi-Tenant Architecture
- User Roles & Permissions Matrix
