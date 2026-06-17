# ARI V1 — P0 Domain Model Specification v1.0

## Project

ARI — Agricultural Intelligence Platform

## Document Type

P0 Domain Model Specification

## Status

Ready for Freeze

## Source Documents

* #44 Farm AI Operating System (Farm AIOS)
* #45 Software Architecture & Monorepo Specification Rev2.0
* #46 MVP Software Build Plan
* #46A Mobile App UX Flow & Screen Specification
* #46B Web App UX Flow & Screen Specification
* #47 AI Agent Development Workflow Framework

---

# 1. Purpose

This document defines the final agreed domain model for ARI P0.

ARI P0 is a Digital Farm Notebook.

The purpose of P0 is to capture:

* Observations
* Events
* Experiences
* Stories
* Questions
* Lessons Learned
* Evidence
* AI Consultation Outcomes

before transforming them into knowledge and intelligence in later phases.

---

# 2. Domain Principles

## Evidence First

All important records should be traceable to evidence.

Evidence may include:

* Photo
* Video
* Voice Recording
* Text
* File
* External Link

---

## Human-in-the-Loop

Humans create records.

Humans validate records.

Humans remain accountable.

AI assists but does not replace human responsibility.

---

## Offline First

Save and Upload are separate operations.

```text
Save Local
≠
Upload
≠
Analyze
```

Records must be creatable without internet connectivity.

---

## Progressive Identity

Identity architecture must support future expansion without redesign.

Supported identity hierarchy:

```text
Organization
    └── Farm
            └── Zone
                    └── Tree
```

---

# 3. Core Entities

---

## 3.1 Organization

Represents the ownership boundary of data.

Examples:

* Individual Farmer
* Family Farm
* Cooperative
* Company
* ARI Internal Organization

### Responsibilities

* Own farms
* Own users
* Own operational data

### Core Attributes

```text
organization_id
name
type
status
created_at
```

---

## 3.2 User

Represents a human using ARI.

### Responsibilities

* Create records
* Upload evidence
* Review information
* Manage assigned farms

### Core Attributes

```text
user_id
organization_id
name
email
phone
role
status
created_at
```

---

## 3.3 Farm

Represents a physical farm.

### Core Attributes

```text
farm_id
organization_id
farm_name
location
description
status
created_at
```

---

## 3.4 Zone

Represents a logical subdivision within a farm.

Examples:

* Block A
* North Section
* Trial Area

### Core Attributes

```text
zone_id
farm_id
zone_name
description
created_at
```

---

## 3.5 Tree

Represents an optional tree-level identity.

### Core Attributes

```text
tree_id
zone_id
tree_code
status
created_at
```

Tree registration is optional in P0.

---

# 4. Notebook Domain

Notebook is the core domain of ARI P0.

---

## 4.1 Notebook Entry

Notebook Entry represents a Note Session.

A Notebook Entry may contain multiple Note Items arranged in timeline order.

### Entry Types

```text
note
consultation
```

### Entry Context

```text
general_note
registered_farm
external_observation
interview
```

### Core Attributes

```text
entry_id

organization_id

created_by_user_id

farm_id (nullable)

zone_id (nullable)

tree_id (nullable)

entry_type

entry_context

title (nullable)

summary (nullable)

suggested_category (nullable)

analysis_status

created_at

updated_at
```

### Notes

Farm, Zone and Tree references are optional.

This supports:

* External observations
* Interviews
* Expert consultations
* Events outside registered farms

---

## 4.2 Note Item

Represents an individual content item within a Notebook Entry.

A Notebook Entry may contain many Note Items.

### Supported Types

```text
photo
video
voice
text
file
link
```

### Core Attributes

```text
item_id

entry_id

item_type

sequence_order

content_text (nullable)

file_path (nullable)

url (nullable)

platform (nullable)

created_at

upload_status
```

### Timeline Support

Sequence order preserves capture order.

Example:

```text
Photo
→ Voice
→ Photo
→ Video
→ Text
```

---

## 4.3 Link Support

External URLs are supported through Note Items.

Examples:

* YouTube
* Facebook
* TikTok
* Website
* Article
* PDF URL

Links are stored as:

```text
item_type = link
```

No dedicated mobile menu is required.

Users may paste URLs into text entries.

The system may classify them as link items.

---

# 5. Ask AI Domain

Ask AI follows the workflow defined in #46A.

External AI providers include:

* ChatGPT
* Gemini
* Claude
* Other

ARI does not provide an internal AI assistant in P0.

---

## 5.1 Consultation Entry

Consultation is implemented as a Notebook Entry type.

```text
entry_type = consultation
```

### Additional Consultation Attributes

```text
ai_provider

ai_usefulness_status

learned_summary
```

### AI Usefulness Status

```text
useful
not_useful
later
```

---

## 5.2 Follow-Up

Follow-Up records track outcomes after AI consultation.

### Supported Follow-Up Periods

```text
3 Days
7 Days
14 Days
```

### Outcome Types

```text
improved
same
worse
unknown
```

### Core Attributes

```text
follow_up_id

entry_id

follow_up_day

outcome

notes

recorded_at
```

---

# 6. Notification Domain

Represents reminders and system notifications.

### Examples

* Upload Reminder
* AI Follow-Up Reminder
* System Notification

### Core Attributes

```text
notification_id

user_id

type

message

status

created_at
```

---

# 7. Upload Queue Domain

Supports Offline First operation.

### Purpose

Manage synchronization between device and backend.

### Core Attributes

```text
queue_id

entry_id

status

retry_count

created_at

uploaded_at
```

### Queue Status

```text
pending

uploading

failed

completed
```

---

# 8. Ownership Model

ARI ownership principle:

```text
Organization owns data.

Users create data.
```

### Ownership Hierarchy

```text
Organization
    ├── Users
    └── Farms
            └── Zones
                    └── Trees
```

### Operational Hierarchy

```text
Notebook Entry
    └── Note Items
```

### Consultation Hierarchy

```text
Notebook Entry
    └── Follow-Ups
```

---

# 9. Domain Relationship Summary

```text
Organization
 ├── Users
 └── Farms
        └── Zones
                └── Trees

Notebook Entry
 ├── Note Items
 └── Follow-Ups

User
 ├── Creates Notebook Entries
 └── Receives Notifications

Upload Queue
 └── References Notebook Entries
```

---

# P0 Required

## Identity

* Organization
* User
* Farm
* Zone
* Tree (Optional Registration)

## Notebook

* Notebook Entry
* Note Item
* Timeline Sequence Support

## Ask AI

* Consultation Entry
* Learned Summary
* Follow-Up

## Offline Operation

* Save Local
* Upload Queue
* Upload Retry

## Metadata

* Title
* Summary
* Suggested Category
* Analysis Status

## Notifications

* Upload Reminder
* Follow-Up Reminder
* System Notification

---

# Optional Extension

## External Link Capture

Support storing:

* YouTube Links
* Facebook Links
* TikTok Links
* Website Links
* Article Links
* PDF URLs

## Mobile Share Integration

Future optional support:

```text
Share → ARI
```

from external applications.

---

# Future Enhancement

Not part of P0.

## Intelligence Layer

* Knowledge Graph
* Evidence Graph
* Vector Database
* RAG
* Knowledge Extraction

## AI Layer

* Internal AI Assistant
* Agent Orchestration
* Autonomous Workflows

## Advanced Features

* Digital Twin
* Robot Integration
* Advanced GIS
* Forecasting
* Advanced Analytics

## Commerce Layer

* Marketplace
* Commerce
* Carbon Credits
* ESG Intelligence

---

# Assumptions Requiring Owner Confirmation

## A1

Tree registration remains optional during P0 deployment.

## A2

entry_context exists in the domain model but is not required as a mobile user input.

The system may assign default values and allow later review.

## A3

AI-generated metadata in P0 is limited to:

```text
title
summary
suggested_category
```

and does not constitute an internal AI assistant.


----------------------------------------
    After Owner Reviewed : Freeze 
    Reviewed by          : owner 
    Reviewed date        : 2026-06-14
    ----------------------------------------


    รับทราบครับ

สถานะเอกสาร:

ARI V1 — P0 Database Schema Specification v1.0

Status: FROZEN
Phase: P0 Digital Farm Notebook
Freeze State: Approved

เอกสารนี้ถือเป็น Source of Truth สำหรับ Phase 2 Database Layer โดยยึดตาม:

#44 Farm AIOS
#45 Software Architecture & Monorepo Specification Rev2.0
#46 MVP Software Build Plan
#46A Mobile App UX Flow & Screen Specification
#46B Web App UX Flow & Screen Specification
#47 AI Agent Development Workflow Framework
ARI V1 — P0 Domain Model Specification v1.0

Frozen Scope:

organizations
users
farms
zones
trees
notebook_entries
note_items
follow_ups
notifications
upload_queue

Frozen Principles:

One Platform
One Backend
One Database
One Domain Model
One RBAC System

Notebook Entry = Note Session

Save Local ≠ Upload ≠ Analyze

farm_id / zone_id / tree_id nullable

Simulator Farm supported

Offline First

หลังจากนี้ หากมีการเปลี่ยนแปลงให้จัดเป็น:

Revision Proposal
Optional Extension
Future Enhancement

ไม่แก้ไขเนื้อหาในเอกสาร Frozen โดยตรง

ขั้นตอนถัดไปที่แนะนำ:

ARI V1 — P0 API Specification v1.0

เพื่อกำหนด REST API Contracts ระหว่าง:

Flutter Mobile
Next.js Web
FastAPI Backend
PostgreSQL
MinIO

และเชื่อมต่อกับ P0 Domain Model + P0 Database Schema ที่ Frozen แล้ว.