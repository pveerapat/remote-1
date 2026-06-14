# Project: ARI — Agricultural Intelligence Platform

## Document Number

#46B

## Document Title

Web App UX Flow & Screen Specification

## Export Mode

Target Document Reconstruction Export

## Human Verification Required

YES

## Status

DRAFT until reviewed by project owner

---

# Document Purpose

This document defines the UX architecture, navigation model, workspaces, workflows, permissions model, and P0 implementation scope for the ARI Web Platform.

The document focuses on the web platform only.

---

# 1. Objective

Design the ARI Web Platform UX for deep-work activities.

The Web Platform is not a Farm ERP.

The Web Platform is not an Executive Dashboard.

The Web Platform serves as the deep-work interface of the ARI Platform and supports transforming:

```text
Farm Notebook
↓
Validated Memory
↓
Knowledge Assets
↓
Agricultural Intelligence
```

---

# 2. Design Principles

## Core Principles

* Memory First
* Knowledge First
* Human-Centered
* Minimal
* Simple
* Pilot Reality First

---

## Scaling Assumption

Design for:

```text
5 Farms
↓
20 Farms
↓
50 Farms
```

before larger-scale expansion.

---

# 3. Platform Definition

## ARI Web Platform

ARI Web Platform is a single web platform for all ARI users.

The modules, workspaces, consoles, dashboards, and workflows described in this document represent the full platform capability.

Users may see different menus, workflows, actions, and data based on:

* RBAC permissions
* Assigned work
* Farm assignment
* Organization scope
* Project scope
* Geographic scope
* Feature flags
* Future platform capabilities

---

## Single Platform Principle

ARI shall not create separate web applications for:

* Farmers
* Family Members
* Workers
* Coordinators
* Agronomists
* Reviewers
* Experts
* Commentators
* ARI Staff
* Admins
* Root Users

All users share the same platform.

Differences in user experience shall be controlled through permissions and assignments rather than separate applications.

---

## Shared Platform Architecture

All users share:

* Web Platform
* Backend Services
* Database
* Domain Model
* Digital Twin Layer
* Evidence Layer
* Knowledge Layer
* Intelligence Layer
* Trust Layer
* Commerce Layer

---

## Web Platform Purpose

The ARI Web Platform serves as the:

**Work Deep Interface**

Typical activities include:

* Review
* Analysis
* Knowledge Curation
* Knowledge Publishing
* Planning
* Forecasting
* Simulation
* Administration
* Governance
* Future Commerce Operations

---

# 4. Global Navigation

## Navigation Model

Hybrid Navigation

---

## Left Sidebar

### P0 Navigation

* Home
* Farms
* Notebook
* Review
* Knowledge
* Search
* Follow-ups
* Simulator
* Administration

---

## Top Bar

* Global Search
* Notifications
* Language Selector (TH / EN)
* Profile

---

# 5. Information Architecture

```text
Home

Farms
 ├─ Farm List
 └─ Farm Detail

Notebook

Review

Knowledge

Search

Follow-ups

Simulator

Administration
```

---

# 6. Home Workspace

## Purpose

Work Queue

Not Executive Dashboard

---

## Sections

* My Farms
* Assigned Reviews
* Pending Tasks
* New Notes
* Knowledge Candidates
* Follow-ups
* System Alerts

---

## Goal

Answer:

> What should I work on today?

---

# 7. Farms Workspace

## Purpose

Farm Directory

---

## Farm List

Displays:

* Farm Name
* Province
* Crop
* Coordinator
* Activity Status

---

## Filters

* Province
* Crop
* Coordinator
* Status

---

## Navigation

```text
Farm List
↓
Select Farm
↓
Farm Detail
```

---

# 8. Farm Detail Workspace

## Purpose

Single workspace containing everything related to one farm.

---

## Sections

### Overview

Farm profile and operational context.

---

### Map

P0:

* Farm Location Marker
* Latitude
* Longitude

Future Ready:

* Farm Boundary
* Zone Boundary
* Block Boundary
* Tree Location
* Sensor Location
* Robot Routes

---

### Identity

Displays:

* Owner ID
* Farm ID
* Zone ID
* Block ID
* Tree ID

Associated QR codes may be accessed through Identity Management.

---

### Timeline

Chronological farm activity history.

---

### Notebook

Farm-specific notebook records.

---

### Media

Farm-specific media repository.

---

### AI Sessions

History of AI-assisted interactions.

---

### Follow-ups

Open and completed follow-up activities.

---

### Knowledge

Knowledge assets related to the farm.

---

### Members

Farm participants and assignments.

---

### Activity

Recent actions and events.

---

# 9. Notebook Workspace

## Purpose

Global Memory Repository

Contains notebook records from all farms.

---

## Supported Content

* Notes
* Stories
* Lessons
* Photos
* Videos
* Voice Notes
* AI Sessions

---

## Filters

### Farm

* All Farms
* Individual Farm

### Date

### Crop

### Disease

### Tags

### AI Session

### User

### Status

* Draft
* Pending Approval
* Approved
* Knowledge Candidate

---

## Actions

* Open Note
* Edit Tags
* Link Case
* Assign Follow-up
* Promote to Knowledge Candidate

---

# 10. Review Workspace

## Purpose

Knowledge Curation Workflow

Transforms:

```text
Raw Memory
↓
Validated Memory
```

---

## Supported Activities

* Review
* Edit
* Tag
* Classification
* Evidence Linking
* Follow-up Request
* Knowledge Candidate Promotion

---

## Workflow

```text
New Note
↓
AI Processing
↓
Suggested Summary
↓
Suggested Tags
↓
Reviewer Review
↓
Approval
↓
Knowledge Candidate
```

---

## Statuses

* New
* In Review
* Needs Follow-up
* Approved
* Knowledge Candidate
* Rejected

---

# 11. Knowledge Workspace

## Purpose

Agricultural Think Tank

Transforms:

```text
Validated Memory
↓
Knowledge Assets
```

---

## Components

### Knowledge Articles

### Lessons Learned

### Best Practices

### Case Library

### Expert Notes

### Knowledge Relationships

### Search

### Tagging

### Versioning

---

## Knowledge Flow

```text
Note
↓
Validated Note
↓
Knowledge Candidate
↓
Case
↓
Knowledge Asset
↓
Knowledge Library
```

---

## Knowledge Confidence

Reserved for future implementation.

Examples:

* Observed
* Repeated
* Validated
* Expert Verified
* ARI Standard

---

# 12. Case Library

## Case Detail Page

Displays:

* Timeline
* Photos
* Videos
* Voice Notes
* Farmer Learning
* Actions Taken
* Outcome
* Reviewer Notes
* Agronomist Notes
* Expert Notes
* Knowledge Links
* Evidence

---

# 13. Search Workspace

## Purpose

Unified Search

---

## Search Targets

* Farms
* Notes
* AI Sessions
* Media
* Cases
* Knowledge Assets

---

## Example Queries

* โรครากเน่า
* เคสที่ถาม ChatGPT
* สวนที่เคยใช้ปุ๋ยนี้
* ผลลัพธ์ดีขึ้น
* ทุเรียนอายุ 10 ปี

---

# 14. Follow-ups Workspace

## Purpose

Learning Completion Workflow

---

## Views

* Pending
* Today
* This Week
* Overdue
* Completed

---

## Workflow

```text
Review
↓
Need Follow-up
↓
Assign
↓
Collect Result
↓
Review
↓
Knowledge Update
```

---

## Outcome Types

* Improved
* No Change
* Worse
* Unknown

---

# 15. Simulator Workspace

## Purpose

Training and Experimentation

---

## Supported Uses

* Testing
* Workflow Validation
* Dataset Creation
* Training

---

## Simulator IDs

* SIM-001
* SIM-002
* SIM-DURIAN
* SIM-MANGO
* SIM-TEST

---

## Rule

Simulator data must remain isolated from production data.

---

# 16. Administration Workspace

## Purpose

Governance and Platform Administration

---

## Components

### Users

### Roles

### Permissions

### Farm Assignment

### Identity Management

### Audit Logs

### System Monitoring

### Storage Usage

### Backup Status

### Privacy Configuration

---

# 17. Identity Management & QR Registry

## Purpose

Manage Digital Identity Objects used throughout ARI.

---

## Registries

### Owner Registry

Creates:

* Owner ID

---

### Farm Registry

Creates:

* Farm ID

---

### Zone Registry

Creates:

* Zone ID

---

### Block Registry

Creates:

* Block ID

---

### Tree Registry

Creates:

* Tree ID

---

## QR Generator

Generates:

* Owner QR
* Farm QR
* Zone QR
* Block QR
* Tree QR

---

## Export

Supports:

* PDF
* PNG

for printing and field deployment.

---

# 18. Access Control Model

## Role-Based Access Control (RBAC)

Roles may include:

* Farm Owner
* Family
* Worker
* Coordinator
* Agronomist
* Reviewer
* Expert
* Staff
* Admin
* Root

---

## Assignment-Based Access

Examples:

* Assigned Farms
* Assigned Reviews
* Assigned Projects
* Assigned Regions

---

## Future Attribute-Based Access Control (ABAC)

Examples:

* Crop Type
* Geography
* Organization Scope
* Project Scope

---

# 19. Notification Center

## Notification Types

* New Notes
* Review Requests
* Assignments
* Knowledge Candidates
* Follow-ups
* Overdue Tasks
* System Alerts
* Sync Issues

---

# 20. Unified Activity Timeline

## Includes

* Notes
* AI Sessions
* Reviews
* Knowledge Updates
* Assignments
* Follow-ups
* Media Uploads
* System Events

---

# 21. Error Handling

## Supported Cases

* Permission Denied
* Sync Failure
* Conflict Resolution
* Missing Media
* Deleted Files
* Review Collision

---

# 22. Accessibility

Design for:

* Field Staff
* Tablet Users
* Laptop Users
* Large Displays
* Low Technical Skill Users

---

# 23. P0 Analytics

Minimal Only

## Metrics

* New Notes
* Review Backlog
* Knowledge Candidates
* Knowledge Published
* Follow-up Completion
* Farm Activity
* Search Usage

---

# 24. UX Metrics

* Review Time
* Knowledge Extraction Rate
* Knowledge Reuse
* Case Reuse
* Search Usage
* Follow-up Completion
* Farm Engagement

---

# 25. P0 Scope

## Included

### Core Workspaces

* Home
* Farms
* Farm Detail
* Notebook
* Review
* Knowledge Candidate Workflow
* Knowledge Library (Basic)
* Search
* Follow-ups
* Administration (Basic)

---

### Identity

* Owner ID
* Farm ID
* Zone ID
* Block ID
* Tree ID
* QR Generator

---

### Farm Location

* Latitude
* Longitude
* Farm Map Marker

---

### Platform Features

* RBAC
* TH / EN Language Selector

---

## Not Included

* Farm Boundary Mapping
* Zone Boundary Mapping
* Block Boundary Mapping
* Tree GPS Mapping
* Sensor GPS Mapping
* Robot Route Mapping
* Yield Heat Maps
* Production Heat Maps
* Advanced Forecasting
* Commerce Operations
* Trading
* Auction
* Carbon Management
* ESG Operations
* Robot Operations
* AI Agent Operations
* Advanced GIS
* Advanced Knowledge Graph

---

# 26. Future Expansion Readiness

The Web Platform shall be designed to support future modules without major UX redesign.

Reserved future areas include:

* Farm Intelligence
* Forecasting & Simulation
* Input Intelligence
* Geographic Intelligence
* Commerce & Market Intelligence
* Sustainability Intelligence
* AI Agent Operations
* Robot Operations
* Developer Operations

---

# 27. RBAC Clarification

ARI Web Platform is a single web platform for all ARI users.

All modules described in this document represent full platform capability.

Users may see different menus, consoles, dashboards, workflows, actions, and data based on:

* RBAC permissions
* Assigned work
* Farm assignment
* Organization scope
* Project scope
* Geographic scope
* Feature flags

ARI shall not create separate web applications for different user groups.

Differences in user experience shall be controlled through permissions and assignments rather than separate applications.

---

# 28. Architecture Summary

```text
ARI Platform

├─ Mobile Platform
│  └─ Work Anywhere
│
└─ Web Platform
   └─ Work Deep

Shared:

- Backend
- Database
- Domain Model
- Digital Twin
- Evidence
- Knowledge
- Intelligence
- Trust
- Commerce

Controlled By:

- RBAC
- Assignments
- Visibility Rules
- Feature Flags
```

---

# 29. Final Principle

The goal of the Web Platform is not farm management.

The goal of the Web Platform is:

```text
Collect Knowledge
↓
Curate Knowledge
↓
Manage Knowledge
↓
Reuse Knowledge
↓
Build Agricultural Intelligence
```

The Web Platform serves as the deep-work interface of the ARI Platform.

---

# Unverified / Needs Human Review

1. Whether the menu name "Review" should remain "Review" or be renamed in a future revision.
2. Whether a dedicated Media Workspace should be added as a first-class menu in a future revision.
3. Exact future navigation placement of Forecasting, Commerce, AI Agent Operations, Sustainability, and Geographic Intelligence modules.
4. Future implementation details of Knowledge Confidence scoring.
5. Future implementation details of Farm Boundary, Zone Boundary, Block Boundary, and Tree GPS mapping.

---

Status: DRAFT until reviewed by project owner.


    ----------------------------------------
    After Owner Reviewed : Freeze 
    Reviewed by          : owner 
    Reviewed date        : 2026-06-14
    ----------------------------------------


รับทราบครับ

ARI V1 #46B
Web App UX Flow & Screen Specification

Status: FROZEN

Freeze Confirmation

เอกสาร #46B ถูก Freeze ตาม Reconstruction Export ฉบับล่าสุด โดยรวมการตัดสินใจเพิ่มเติมดังนี้:

Included in P0
Home Workspace
Farms Workspace
Farm Detail Workspace
Notebook Workspace
Review Workspace
Knowledge Workspace
Search Workspace
Follow-ups Workspace
Simulator Workspace
Administration Workspace
Identity Management & QR Registry
Owner ID
Farm ID
Zone ID
Block ID
Tree ID
QR Generator
Farm Latitude / Longitude
Farm Map Marker
RBAC
TH / EN Language Selector
Platform Principles
Single Web Platform
Shared Backend
Shared Database
Shared Domain Model
Shared Evidence Layer
Shared Knowledge Layer
Shared Intelligence Layer
Shared Trust Layer
Shared Commerce Layer
Access Principles
All user groups use the same Web Platform
Visibility controlled by RBAC
Visibility controlled by Assignments
No role-specific web applications
No duplicated platforms
Web Platform Purpose
Work Deep

Supports:

Review
Analysis
Knowledge Curation
Knowledge Publishing
Planning
Governance
Administration
Future Expansion Reserved
Farm Intelligence
Forecasting & Simulation
Input Intelligence
Geographic Intelligence
Commerce & Market Intelligence
Sustainability Intelligence
AI Agent Operations
Robot Operations
Developer Operations
Document Status

FROZEN

Frozen Document

ARI V1 #46B — Web App UX Flow & Screen Specification

Freeze Date

2026-06-14

Source of Truth

Latest Reconstruction Export approved by Project Owner.

No further modifications should be made without creating a formal revision document (e.g. #46B Revision 1.1).