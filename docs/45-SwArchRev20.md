# Project

ARI — Agricultural Intelligence Platform

# Document Number

#45

# Document Title

Software Architecture & Monorepo Specification rev2.0

# Export Mode

Target Document Reconstruction Export

# Human Verification Required

YES

# Status

DRAFT until reviewed by project owner

---

# Reconstruction Notes

This reconstruction is based only on content explicitly confirmed within the available conversation history.

Where the original #45 content was not present in the conversation, items are placed under **Unverified / Needs Human Review**.

---

# Objective

Transform frozen ARI business architecture into a production-grade software architecture supporting:

```text
Digital Twin
↓
Evidence Layer
↓
Knowledge Layer
↓
Intelligence Layer
↓
Trust Layer
↓
Commerce Layer
↓
Mobile / Web Applications
↓
AI Agents
↓
Future Robotics
```

---

# Unified Platform Architecture

ARI shall be implemented as a single unified platform consisting of:

* One Mobile Application
* One Web Platform
* One Backend Platform
* One Database Architecture
* One Domain Model
* One RBAC System

Mobile App and Web Platform are different presentation interfaces of the same platform.

Access to features, menus, consoles, workflows, and data shall be controlled by:

* Role-Based Access Control (RBAC)
* Permissions
* Assigned Work
* Organization Scope
* Farm Scope
* Feature Flags
* Progressive Adoption Level

ARI shall not create separate applications for:

* Farmers
* Agronomists
* Reviewers
* ARI Staff
* Admins
* Other user groups

All users operate on the same platform and share the same underlying:

* Data Architecture
* Evidence Architecture
* Knowledge Architecture
* Trust Architecture
* Compliance Architecture
* Commerce Architecture

---

# Platform Architecture Principles

## One Platform

```text
ARI Platform

├─ Mobile App
└─ Web Platform
```

Both interfaces share:

```text
Backend
Database
Domain Model
RBAC
Evidence Layer
Knowledge Layer
Trust Layer
Commerce Layer
```

---

## Mobile = Work Anywhere

Primary characteristics:

* Field operation
* Evidence capture
* Ask AI
* Follow-up
* Notification handling
* Quick review
* Quick approval
* Mobile-first operation

---

## Web = Work Deep

Primary characteristics:

* Review
* Analysis
* Search
* Knowledge preparation
* Administration
* Reporting
* Deep workflow execution

---

## RBAC-Based Access

ARI shall use:

```text
Single Application
Single Platform
Role-Based Access
```

User experience varies according to:

* Role
* Permission
* Assigned Work
* Organization Scope
* Farm Scope
* Feature Flags

---

# Mobile Platform Relationship

Reference:

```text
#46A Mobile Platform UX
```

P0 Mobile UX remains the Digital Farm Notebook experience.

Farmer base experience:

* Ask AI
* Add Record
* Farm Notebook
* Notifications
* Profile

Additional role-based functionality may be exposed through RBAC.

No separate mobile applications shall be created.

---

# Web Platform Relationship

Reference:

```text
#46B Web Platform UX
```

Web Platform serves as the deep-work interface of the same ARI platform.

Role-based consoles and workflows are controlled through RBAC.

No separate web platforms shall be created.

---

# P0 Scope (Confirmed)

Architecture supports:

* Mobile Platform
* Web Platform
* Backend Platform
* RBAC
* Evidence Layer
* Knowledge Preparation
* Review Workflow
* AI Session Workflow
* Farm Notebook Workflow

P0 focuses on:

```text
Capture
Review
Search
Follow-up
Administration
```

---

# Future Architecture (Confirmed Direction)

Reserved for later phases:

* Trust Layer Expansion
* Compliance Layer Expansion
* Commerce Layer Expansion
* AI Operations
* Robot Operations
* Farm AIOS Integration
* Advanced Intelligence Modules

---

# Relationship to Other Documents

This document serves as the software architecture foundation for:

* #43 Robot Authority Model
* #44 Farm AI Operating System (Farm AIOS)
* #46 MVP Software Build Plan
* #46A Mobile Platform UX
* #46B Web Platform UX
* #47 AI Agent Development Workflow

---

# Unverified / Needs Human Review

The following sections were referenced during #45 discussions but the finalized content was not available in the reconstruction source:

## System Architecture

* Presentation Layer
* Application Layer
* Domain Layer
* Data Layer
* Infrastructure Layer
* AI Layer
* Integration Layer

## Core Domains

* Farm Domain
* Identity Domain
* Tree Domain
* Fruit Domain
* Evidence Domain
* Knowledge Domain
* Intelligence Domain
* Trust Domain
* Commerce Domain
* Compliance Domain
* Sustainability Domain
* AI Agent Domain
* Robot Domain

## Bounded Context Design

* Ownership
* Responsibilities
* Inter-domain Communication

## Monorepo Structure

* apps/
* services/
* packages/
* agents/
* infra/
* data-models/
* shared/
* docs/
* tools/

## Data Architecture

* PostgreSQL Design
* TimescaleDB Design
* MinIO Design
* Knowledge Graph Design

## AI Architecture

* Agent Platform
* LLM Routing
* RAG
* Vector Database

## Infrastructure Architecture

* Deployment Models
* Hybrid Edge / Cloud Architecture
* Security Architecture
* Observability

## Development Architecture

* Git Strategy
* CI/CD
* Testing
* Release Management

These sections require verification against the original #45 Revision 2.0 source document before final freeze.


    ----------------------------------------
    After Owner Reviewed : Freeze 
    Reviewed by          : owner 
    Reviewed date        : 2026-06-14
    ----------------------------------------


รับทราบครับ

สถานะล่าสุด:

Project: ARI — Agricultural Intelligence Platform

Document Number: #45

Document Title:
Software Architecture & Monorepo Specification rev2.0

Status: FROZEN

Freeze Date:
Confirmed by Project Owner

Notes:
- Unified Platform Architecture included.
- One Mobile App + One Web Platform + One Backend Platform.
- One Domain Model + One RBAC System.
- Mobile = Work Anywhere.
- Web = Work Deep.
- RBAC governs visibility, permissions, workflows, and consoles.
- No separate applications for different user groups.
- Frozen document becomes Source of Truth for subsequent documents.

สำหรับเอกสารถัดไปตาม Roadmap:

#44 Farm AI Operating System (Farm AIOS)

และ #44 ต้องสอดคล้องกับ:

#43 Robot Authority Model (FROZEN)
#45 Software Architecture & Monorepo Specification rev2.0 (FROZEN)
#46 MVP Software Build Plan (FROZEN)
#46A Mobile Platform UX (FROZEN)
#46B Web Platform UX (FROZEN)

โดยห้ามเปลี่ยน Architecture ที่ Freeze แล้ว และหากมีแนวคิดใหม่ต้องระบุเป็น Future Enhancement, Optional Extension หรือ Revision Proposal เท่านั้น.