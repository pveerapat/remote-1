# ARI V1 #46

MVP Software Build Plan

## Document Metadata

* Project: ARI — Agricultural Intelligence Platform
* Document Number: #46
* Document Title: MVP Software Build Plan
* Export Mode: Target Document Reconstruction Export
* Human Verification Required: YES
* Status: DRAFT until reviewed by project owner

---

## Governance Notice

This document is a reconstructed version of ARI V1 #46 based on confirmed decisions found within the conversation history.

This document shall not be treated as final Source of Truth until reviewed and approved by the project owner.

---

## Purpose

Define the MVP software build plan for ARI P0.

The objective is to build the first real ARI product, deploy it to pilot farms, collect real-world data, validate adoption, validate knowledge capture, and establish the foundation for future ARI platform development.

---

## Product Definition

### Product Name

ARI Digital Farm Notebook

Thai Name:

📒 สมุดบันทึกสวน

---

### ARI P0 Is

A Farm Memory Platform designed to help farmers capture:

* Events
* Observations
* Questions
* Experiences
* Stories
* Lessons Learned
* Family Knowledge

before transforming them into knowledge and intelligence.

---

### ARI P0 Is Not

* Farm ERP
* Marketplace
* Farm AIOS
* Autonomous Agriculture Platform
* Advanced AI System
* Dashboard Platform

---

## Product Philosophy

```text
Reality
↓
Memory
↓
Knowledge
↓
Intelligence
↓
Decision
```

---

## Core Mission

Help farmers capture:

* Observations
* Events
* Experiences
* Evidence
* Stories
* Knowledge

before transforming them into intelligence.

---

## MVP Target

### Pilot Scale

```text
5 Farms
↓
20 Farms
```

---

### Validation Goals

* Adoption
* Data Collection
* Knowledge Capture
* Farmer Retention
* Feedback Loop

---

## Development Philosophy

### Simple

Minimize complexity.

---

### Minimal

Build only what is necessary for pilot validation.

---

### Flexible

Allow future changes based on real-world learning.

---

### Build Fast

Deploy Fast

Learn Fast

---

## Architectural Principle

### P0 Rule

```text
One Platform
Multiple Roles
```

---

### Platform Strategy

ARI Unified Platform

Role-Based Access Control (RBAC)

Do not separate applications prematurely.

Use real pilot data before rearranging architecture.

---

## Platform Structure

### Farmer Side

Mobile App

Users:

* Farm Owner
* Family
* Worker
* Farm Manager

---

### ARI Team Side

Mobile App + Web App

Users:

* Root
* Admin
* Staff
* Farm Coordinator
* Agronomist
* Reviewer
* Expert Network

---

## Core Functional Domains

### Farm Identity

* Farm
* Owner
* Member
* Permission

---

### Farm Capture

* Question
* Event
* Reminder
* Story

---

### Farm Memory

* Timeline
* Story
* Experience
* Lesson Learned
* Knowledge

---

### Feedback Loop

* AI Analysis
* Expert Review
* Feedback

---

### Operations

* Review Queue
* Knowledge Validation
* Dataset Management
* Monitoring

---

## Technology Stack

### Mobile

Flutter

---

### Backend

FastAPI

Python

REST API

JWT Authentication

RBAC

---

### Database

PostgreSQL

TimescaleDB

---

### Object Storage

MinIO

---

### AI Services

* Speech-to-Text
* Image Tagging
* Video Processing
* LLM Summarization
* Classification
* Knowledge Extraction

---

### Infrastructure

Docker Compose

Ubuntu Server

FastAPI

PostgreSQL

TimescaleDB

MinIO

Redis

Worker Services

---

## Security Foundation

Must support:

* Authentication
* RBAC
* Farm-Level Permission
* Privacy Level
* Audit Log
* Backup
* Monitoring
* Recovery Procedures

---

## Simulator Farms

System must support:

* SIM-001
* SIM-002
* SIM-DURIAN
* SIM-MANGO
* SIM-TEST

Purpose:

* Testing
* Training
* Demo
* Dataset Creation

---

## MVP Scope

### Must Build

* Login
* Farm Setup
* Farm Profile
* Farm Cover Page
* Event Capture
* Voice Capture
* Photo Capture
* Video Capture
* Text Capture
* Offline Local Save
* Upload Queue
* Upload Center
* Farm Notebook
* Event Status
* AI Summary
* AI Tagging
* Human Review
* Feedback Timeline
* Notification
* Role Permission
* Privacy Controls

---

### Should Build

* QR Scan
* Product Scan
* Search
* Filters
* Story Capture
* Family Knowledge Capture
* Confidence Score
* Manual Feedback

---

### Nice To Have

* Advanced Disease Detection
* Map View
* Tree Digital Twin Link
* Product Traceability Link
* Cooperative Sharing Feed
* Voice Command

---

### Deferred

* ERP
* Accounting
* Inventory
* Marketplace
* Autonomous Robot Integration
* Farm AIOS
* Full Digital Twin Simulation
* Advanced Multi-Agent Systems

---

## Farmer Mobile App

### Core Navigation

* Home
* Capture
* Memory
* Notifications
* Settings

---

### Capture Types

* Ask ARI
* Event
* Reminder
* Farm Story

---

### Supported Inputs

* Voice
* Photo
* Video
* Text

---

## Farm Memory Concept

Farm Memory contains:

* Farm Notebook
* Stories
* Experiences
* Lessons Learned
* Knowledge

---

## Event Lifecycle

```text
Draft
↓
Saved Locally
↓
Waiting Upload
↓
Uploading
↓
Uploaded
↓
AI Processing
↓
Human Review
↓
Feedback Ready
↓
Closed
```

---

## Offline First Principle

### Core Rule

```text
Save ≠ Upload
```

Saving locally must be independent from uploading.

---

### Requirements

* Local Storage
* Background Sync
* Upload Resume
* Upload Retry
* Conflict Handling
* WiFi Only Upload
* Manual Upload

---

## AI Processing Pipeline

### Voice

```text
Voice
↓
Speech-to-Text
↓
Cleaning
↓
Summary
↓
Tagging
↓
Classification
```

---

### Photo

```text
Photo
↓
Image Analysis
↓
Tagging
↓
Summary
```

---

### Video

```text
Video
↓
Frame Extraction
↓
Speech Extraction
↓
Summary
↓
Knowledge Extraction
```

---

## Feedback Model

### P0 Authority Model

AI-assisted Human Feedback

```text
Farmer
↓
AI Analysis
↓
Human Review
↓
Feedback
```

---

### Feedback Types

* AI Feedback
* Human Feedback
* ARI Feedback
* Expert Feedback

---

## Operations Model

### ARI Team Functions

* Event Review
* Media Review
* Transcript Review
* Knowledge Validation
* Feedback Management
* Dataset Management

---

## Governance & Authority

### Root Owner

Highest authority.

Responsibilities:

* Policy
* Authority Rules
* Permission Governance
* Privacy Governance
* Dataset Governance
* Audit Review
* Strategic Direction

---

### System Admin

Responsibilities:

* System Administration
* Infrastructure
* Storage
* Backup
* Monitoring

---

### Operations Roles

* Staff
* Coordinator
* Agronomist
* Reviewer
* Expert

---

## Role Hierarchy

```text
ROOT OWNER
    │
    ▼
SYSTEM ADMIN
    │
    ▼
STAFF
    │
    ▼
COORDINATOR
    │
    ▼
AGRONOMIST
    │
    ▼
REVIEWER
    │
    ▼
EXPERT
    │
    ▼
FARM OWNER
    │
    ▼
FAMILY
    │
    ▼
WORKER
```

---

## Development Sprint Plan

### Sprint 1

Foundation

* Monorepo Setup
* Backend Foundation
* Database
* Authentication
* Mobile Foundation

---

### Sprint 2

Farm Identity

* Farm Setup
* Farm Profile
* Members
* Permissions

---

### Sprint 3

Capture

* Event Capture
* Media Capture
* Local Save

---

### Sprint 4

Upload Center

* Upload Queue
* Retry
* Resume
* WiFi Mode

---

### Sprint 5

Farm Notebook

* Timeline
* Search
* Filters
* Media History

---

### Sprint 6

Feedback

* AI Processing
* Review Workflow
* Feedback Delivery

---

### Sprint 7

Pilot Deployment

* Deploy
* Training
* Feedback Collection
* Bug Fixing

---

## Release Plan

### Alpha

Internal Testing

---

### Beta

5 Farms

---

### Pilot

20 Farms

---

## Success Criteria

### Product Metrics

* Active Farms
* Active Users
* Events Per Week
* Upload Volume
* Story Records
* Feedback Views

---

### Technical Metrics

* Upload Success Rate
* Retry Success Rate
* Crash Rate
* Processing Time
* Feedback Delivery Time

---

### Adoption Metrics

* Week 1 Retention
* Week 4 Retention
* Repeat Usage
* Team Participation

---

### Learning Metrics

* Validated Events
* Disease Cases
* Product Cases
* Knowledge Items
* Reusable Insights

---

## Technical Debt Strategy

### Can Be Postponed

* Kubernetes
* Microservices
* Advanced Semantic Search
* Graph Database
* ERP
* Marketplace
* Robot Integration
* Advanced Analytics

---

### Must Not Be Postponed

* Offline First
* Upload Reliability
* Privacy Controls
* Auditability
* Human Review
* Dataset Structure
* Simple UX
* Farmer Trust

---

## Frozen Decisions

* ARI P0 = ARI Digital Farm Notebook
* Simple / Minimal / Flexible Development Philosophy
* ARI Unified Platform
* RBAC Architecture
* Farmer Side = Mobile App
* ARI Team Side = Mobile App + Web App
* Simulator Farm Support
* Security Foundation
* AI-assisted Human Feedback
* Offline First Architecture
* Save ≠ Upload Principle

---

## Ready for Freeze Items

* MVP Software Build Plan Revision 1.1 Reconstruction

---

## Open Questions

Not Found

---

## Future Enhancements

* Advanced Disease Detection
* Tree Digital Twin Integration
* Product Traceability Integration
* Cooperative Sharing Feed
* Voice Command
* Autonomous Robot Integration
* Farm AIOS
* Full Digital Twin Simulation
* Advanced Multi-Agent Systems

---

## Optional Extensions

Not Found

---

## Revision Proposals

Not Found

---

## Unverified / Needs Human Review

* Exact version/revision number beyond MVP Software Build Plan could not be verified.
* Exact last updated date could not be verified.
* Exact role hierarchy ordering may require owner verification.
* Exact Sprint deliverable details may require owner verification.

---

## Status

Current Status: DRAFT

----------------------------------------
After Owner Reviewed : Freeze 
Reviewed by          : owner 
Reviewed date        : 2026-06-14
----------------------------------------

# Freeze Decision

## ARI V1 #46

### MVP Software Build Plan

Status: FROZEN

Freeze Date: Approved by Project Owner

---

## Freeze Scope

This freeze applies to:

* Product Definition
* Product Philosophy
* MVP Scope
* Development Philosophy
* Platform Strategy
* Platform Structure
* Technology Stack
* Security Foundation
* Simulator Farm Support
* Farmer Mobile App Scope
* ARI Team Mobile App Scope
* ARI Team Web App Scope
* Offline-First Architecture
* Event Lifecycle
* AI Processing Pipeline
* Feedback Model
* Governance & Authority Model
* Role Hierarchy
* Sprint Plan
* Release Plan
* Success Criteria
* Technical Debt Strategy

---

## Frozen Decisions

### Product

ARI P0 = 📒 ARI Digital Farm Notebook

---

### Development Philosophy

* Simple
* Minimal
* Flexible

Build Fast

Deploy Fast

Learn Fast

---

### Platform Strategy

ARI Unified Platform

Role-Based Access Control (RBAC)

One Platform

Multiple Roles

---

### User Platforms

#### Farmer Side

Mobile App

---

#### ARI Team Side

Mobile App + Web App

---

### Security Foundation

Required

---

### Simulator Farm Support

Required

---

### Feedback Model

AI-assisted Human Feedback

---

### Architecture Principle

Offline First

Save ≠ Upload

---

## Change Control

Any modification after this point shall be treated as:

* Revision Proposal
* Future Enhancement
* Optional Extension

until reviewed and approved by the Project Owner.

---

## Status

Current Status: FROZEN
