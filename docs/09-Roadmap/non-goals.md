# Non-Goals

Status: Draft
Version: 1.0
Last Updated: 2026-07-26
Owner: Bhyn

## Purpose

Define features that are intentionally excluded from Version 1.

This document protects the project from scope creep and ensures development remains focused on delivering a working MVP.

---

# Why Non-Goals Matter

Every feature added to Version 1:

- Increases development time
- Increases testing requirements
- Increases maintenance burden
- Delays launch

Version 1 should focus on solving the core problem:

```text
Track people, tasks, events, documents, and activities
with basic automation support.
```

Anything that does not directly support this goal should be deferred.

---

# Version 1 Philosophy

Build:

```text
Simple
Reliable
Secure
Useful
```

Do Not Build:

```text
Complex
Highly Customizable
Enterprise-Level
Feature Rich
```

---

# AI Features

Version 1 will NOT include:

✗ AI Assistant

✗ AI Chatbot

✗ AI Workflow Builder

✗ AI Recommendations

✗ AI Content Generation

✗ AI Search

Reason:

AI introduces significant complexity and is not required to validate the core product.

---

# Mobile Applications

Version 1 will NOT include:

✗ iOS App

✗ Android App

✗ Tablet App

Reason:

Responsive web application is sufficient for initial users.

---

# Billing & Payments

Version 1 will NOT include:

✗ Subscription Billing

✗ Invoice Generation

✗ Payment Processing

✗ Stripe Integration

✗ Payment Reminders

Reason:

The platform should first prove its operational value before financial workflows are added.

---

# Marketplace Features

Version 1 will NOT include:

✗ Template Marketplace

✗ Automation Marketplace

✗ Plugin Marketplace

✗ Community Templates

Reason:

Marketplaces require a healthy user base before they become valuable.

---

# Advanced Automation

Version 1 will NOT include:

✗ Visual Workflow Builder

✗ Drag-and-Drop Automation Editor

✗ Conditional Branching UI

✗ Scheduled Automation Builder

✗ Automation Templates

Reason:

n8n already provides workflow creation capabilities.

---

# Public Developer Platform

Version 1 will NOT include:

✗ Public API Keys

✗ Developer Portal

✗ API Marketplace

✗ Third-Party App Ecosystem

Reason:

Developer ecosystems are only useful after product-market fit.

---

# Advanced Reporting

Version 1 will NOT include:

✗ Custom Dashboards

✗ BI Reports

✗ Forecasting

✗ Trend Analysis

✗ Executive Analytics

Reason:

Basic dashboards are sufficient for MVP validation.

---

# Advanced User Management

Version 1 will NOT include:

✗ Single Sign-On (SSO)

✗ Enterprise Identity Providers

✗ SCIM Provisioning

✗ Organization Switching

✗ Multi-Organization Users

Reason:

Target users do not require enterprise identity features.

---

# Advanced Permissions

Version 1 will NOT include:

✗ Custom Roles

✗ Permission Builder

✗ Field-Level Permissions

✗ Row-Level Permission Rules

Reason:

Predefined roles are sufficient for launch.

---

# White Label Features

Version 1 will NOT include:

✗ Custom Domains

✗ Full Rebranding

✗ White Label Deployments

✗ Client Portals

Reason:

Branding flexibility is not critical during validation.

---

# Collaboration Features

Version 1 will NOT include:

✗ Real-Time Collaboration

✗ Live Editing

✗ Presence Indicators

✗ Team Chat

✗ Internal Messaging

Reason:

These features significantly increase technical complexity.

---

# Advanced Document Features

Version 1 will NOT include:

✗ OCR

✗ Document Versioning

✗ Digital Signatures

✗ Document Approval Workflows

✗ Document Comparison

Reason:

Simple upload and storage is enough initially.

---

# Industry-Specific Features

Version 1 will NOT include:

✗ Attendance Tracking

✗ Grade Management

✗ Student Portals

✗ CRM Pipelines

✗ Inventory Management

✗ Payroll

✗ Accounting

Reason:

The platform must remain industry-agnostic at launch.

---

# Integrations

Version 1 will NOT include:

✗ Google Workspace Integration

✗ Microsoft 365 Integration

✗ Slack Integration

✗ WhatsApp Integration

✗ Zoom Integration

✗ Calendar Synchronization

Reason:

Core workflows must be validated before expanding integrations.

---

# Infrastructure Enhancements

Version 1 will NOT include:

✗ Multi-Region Hosting

✗ High Availability Clusters

✗ Disaster Recovery Automation

✗ Advanced Monitoring

✗ Auto Scaling

Reason:

Not required at MVP scale.

---

# Future Candidate Features

These features may move into future releases:

```text
Attendance Module
Assignment Module
CRM Module
Billing Module
Workflow Builder
Template Marketplace
Custom Roles
Public APIs
AI Features
Mobile Apps
Integrations
```

---

# Scope Control Rule

When evaluating a new feature request:

Ask:

```text
Does this directly help users manage:

- People
- Tasks
- Events
- Documents
- Activities
```

If the answer is:

```text
No
```

the feature should be deferred until after Version 1.

---

# Version 1 Definition

Version 1 is complete when:

✓ MVP Features are complete

✓ Security is verified

✓ Multi-tenancy is verified

✓ Automations work

✓ Core workflows work

Version 1 is NOT complete when:

✗ Every possible feature exists

✗ Every industry is supported

✗ Every integration is built

---

# Related Documents

- MVP Features
- Future Features
- Product Vision
- Template Architecture
- System Architecture
