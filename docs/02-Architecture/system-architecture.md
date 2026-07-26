# System Architecture

Status: Draft
Version: 1.0
Last Updated: 2026-07-26
Owner: Bhyn

## Purpose

Define the technical architecture of the platform and how all major components communicate.

This document serves as the blueprint for development.

---

# High-Level Architecture

```text
Users
  ↓
Frontend (Web App)
  ↓
Backend API (FastAPI)
  ↓
PostgreSQL Database

Backend API
  ↓
Automation Engine (n8n)

Backend API
  ↓
File Storage

Backend API
  ↓
Authentication Service
```

---

# Architecture Principles

## Principle 1 — Modular

Modules should be added without changing the core system.

Examples:

- Attendance Module
- CRM Module
- Billing Module
- Assignment Module

---

## Principle 2 — Multi-Tenant

Every organization operates independently.

Example:

```text
Organization A
Organization B
Organization C
```

Data never mixes.

---

## Principle 3 — API First

Frontend never talks directly to the database.

All communication goes through the API.

---

## Principle 4 — Automation Ready

Every important action can trigger workflows.

Examples:

```text
Task Created
Task Completed
Document Uploaded
Student Absent
```

---

# Frontend Layer

## Technology

```text
Next.js
React
TypeScript
```

---

## Responsibilities

- User Interface
- Forms
- Dashboards
- Tables
- Authentication screens
- Reports

---

## Major Screens

### Authentication

```text
Login
Register
Forgot Password
```

---

### Dashboard

```text
Upcoming Tasks
Recent Activities
Upcoming Events
Quick Actions
```

---

### People

```text
List
Create
Edit
Delete
```

---

### Tasks

```text
List
Create
Assign
Complete
```

---

### Events

```text
Calendar
Schedule
Attendance (future)
```

---

### Documents

```text
Upload
Download
Search
```

---

### Settings

```text
Organization
Users
Roles
Modules
```

---

# Backend Layer

## Technology

```text
FastAPI
Python
```

---

## Responsibilities

- Business Logic
- Validation
- Authentication
- Authorization
- API Endpoints
- Automation Triggers

---

## Service Structure

```text
backend/

├── api/
├── models/
├── schemas/
├── services/
├── database/
├── auth/
├── automation/
└── tests/
```

---

# Database Layer

## Technology

```text
PostgreSQL
```

---

## Core Tables

```text
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

## Design Rules

### Rule 1

Use UUIDs.

### Rule 2

Every table contains:

```text
organization_id
```

except organizations.

### Rule 3

Never allow direct database access from frontend.

---

# Authentication Layer

## Version 1

Technology:

```text
JWT
```

---

## Flow

```text
Login
 ↓
Verify Credentials
 ↓
Generate JWT
 ↓
Return Token
 ↓
Access Protected Routes
```

---

## Future

Possible additions:

```text
Google Login
Microsoft Login
2FA
SSO
```

Not required for MVP.

---

# Authorization Layer

Based on:

```text
Role
+
Organization
```

Examples:

```text
Owner
Admin
Manager
Staff
Member
Viewer
```

Defined in:

User Roles & Permissions Matrix

---

# File Storage Layer

## Purpose

Store uploaded files.

Examples:

```text
Worksheets
Invoices
Contracts
Study Notes
Images
```

---

## Version 1 Options

Development:

```text
Local Storage
```

Production:

```text
Cloudflare R2
or
AWS S3
```

---

# Automation Layer

## Technology

```text
n8n
```

---

## Purpose

Automate repetitive actions.

Examples:

```text
Task Overdue
 ↓
Send Reminder
```

```text
Student Added
 ↓
Send Welcome Email
```

```text
Lead Created
 ↓
Assign Salesperson
```

---

## Trigger Types

Version 1:

```text
Person Created
Task Created
Task Updated
Event Created
Document Uploaded
```

---

## Action Types

Version 1:

```text
Send Email
Create Task
Update Status
Log Activity
```

---

# Activity Logging

Every important action creates an activity record.

Examples:

```text
User Logged In
Task Completed
Document Uploaded
Event Created
```

Stored in:

```text
activities
```

table.

---

# Module System

## Goal

Allow features to be enabled per organization.

Example:

```text
Core Platform

+
CRM Module

+
Attendance Module

+
Billing Module
```

---

## Version 1

Modules exist conceptually but are not dynamically installed.

Organizations simply enable or disable available features.

---

# Deployment Architecture

## Development

```text
Frontend
↓
localhost:3000

Backend
↓
localhost:8000

Database
↓
localhost:5432

n8n
↓
localhost:5678
```

---

## Production

```text
Frontend
↓
Vercel

Backend
↓
Docker Container

Database
↓
Managed PostgreSQL

Automation
↓
n8n

Storage
↓
Cloudflare R2
```

---

# Security Requirements

## Required

- Password Hashing
- JWT Validation
- Organization Isolation
- Role Checks
- Input Validation

---

## Not Required For MVP

- Single Sign-On
- Enterprise Permissions
- Audit Compliance
- Advanced Security Monitoring

---

# Version 1 Scope

Build:

✓ Frontend

✓ FastAPI Backend

✓ PostgreSQL

✓ Authentication

✓ Roles

✓ People

✓ Tasks

✓ Events

✓ Documents

✓ Activities

✓ Basic n8n Integration

Do Not Build Yet:

✗ AI Assistant

✗ Billing

✗ Marketplace

✗ Public API

✗ Mobile App

✗ Advanced Analytics

---

# Related Documents

- Product Vision
- Database Schema
- User Roles & Permissions Matrix
- Automation Architecture
- API Specification
- Template Architecture
