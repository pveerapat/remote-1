# RBAC Clarification

## Overview

ARI Web Platform is a single web platform for all ARI users.

The modules, workspaces, consoles, dashboards, and workflows described throughout ARI documentation represent the full platform capability.

Users may see different menus, modules, dashboards, workflows, actions, and data based on:

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

Differences in user experience shall be controlled through permissions, assignments, and visibility rules rather than separate applications.

---

## Shared Platform Architecture

All users share the same:

* Web Platform
* Mobile Platform
* Backend Services
* Database
* Domain Model
* Digital Twin Layer
* Evidence Layer
* Knowledge Layer
* Intelligence Layer
* Trust Layer
* Commerce Layer

ARI maintains a unified platform architecture for all user groups.

---

## Access Control Model

Visibility and capabilities shall be determined by:

### Role-Based Access Control (RBAC)

Examples:

* Farm Owner
* Worker
* Coordinator
* Agronomist
* Reviewer
* Expert
* Staff
* Admin
* Root

### Assignment-Based Access

Examples:

* Assigned Farms
* Assigned Projects
* Assigned Regions
* Assigned Tasks
* Assigned Reviews

### Future Attribute-Based Access Control (ABAC)

Examples:

* Crop Type
* Geographic Region
* Organization Scope
* Project Scope
* Feature Access
* Compliance Scope

---

## Web Platform Purpose

The ARI Web Platform serves as the **Deep-Work Interface** of the ARI Platform.

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

## Mobile Platform Purpose

The ARI Mobile Platform serves as the **Work-Anywhere Interface** of the ARI Platform.

Typical activities include:

* Ask AI
* Field Data Collection
* Photos
* Videos
* Voice Notes
* Notebook Entries
* Follow-Ups
* Notifications
* Quick Reviews
* Quick Approvals

---

## Platform Usage Principle

All roles may use both:

* Mobile Platform
* Web Platform

The choice of platform depends on:

* Task complexity
* User preference
* Work environment
* Permission level

rather than user role alone.

---

## Anti-Fragmentation Principle

ARI shall prefer role-based visibility and feature control over application fragmentation.

New roles, capabilities, and workflows should be introduced through:

* RBAC
* Assignments
* Feature Flags
* Platform Modules

rather than creating new applications.

ARI shall avoid creating:

* Farmer App
* Expert App
* Reviewer App
* Admin App
* Trading App
* Carbon App
* Other role-specific applications

unless there is a compelling architectural reason to do so.

---

## Architecture Summary

```text
ARI Platform

├── Mobile Platform
│   └── Work Anywhere
│
└── Web Platform
    └── Work Deep

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

## Status

FROZEN

Applicable to:

* #46A ARI Mobile Platform UX
* #46B ARI Web Platform UX Architecture
* Future ARI Platform Modules
