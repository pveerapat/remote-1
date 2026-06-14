# Project: ARI — Agricultural Intelligence Platform

## Document Number

#46A

## Document Title

Mobile App UX Flow & Screen Specification

---

## Export Metadata

* Export Mode: Target Document Reconstruction Export
* Human Verification Required: YES
* Status: DRAFT until reviewed by project owner

---

# 1. Objective

Design the mobile user experience for ARI P0.

The application is designed as a Digital Farm Notebook focused on:

* Capturing observations
* Capturing experiences
* Preserving farm memory
* Supporting future knowledge generation
* Supporting future intelligence generation

The application is not intended to function as:

* Farm ERP
* Farm Management System
* Marketplace
* Farm AIOS

in P0.

---

# 2. Mobile Strategy

## Unified Mobile Application

ARI Mobile App is a single unified mobile application for all ARI users.

The P0 Digital Farm Notebook UX described in this document represents the base mobile experience for farmer-side users.

Other roles, including:

* ARI Staff
* Farm Coordinator
* Agronomist
* Reviewer
* Admin
* Root

may see additional menus, actions, workflows, assigned tasks, and administrative functions depending on:

* RBAC permissions
* Assigned farms
* Assigned work
* Organization scope
* Feature flags
* Deployment phase

ARI shall not create separate mobile applications for different user groups in P0.

All users share:

* Mobile application
* Backend
* Database
* Domain model
* Authentication system
* Permission framework

The user experience may differ by role, but the platform remains unified.

---

# 3. Mobile UX Philosophy

Users should not need to understand:

* Event
* Story
* Memory
* Knowledge
* Classification
* Data Structure

The user only needs to:

* Ask
* Record
* Review
* Learn

---

# 4. Home Screen

## Top Bar

### Farm Selector

Support:

* Single Farm
* Multiple Farms
* Simulator Farms

Examples:

* SIM-001
* SIM-002
* SIM-DURIAN
* SIM-MANGO
* SIM-TEST

### Profile

Accessible from the top-right corner.

---

## Main Actions

### 🤖 Ask AI

### ➕ เพิ่มบันทึก

### 📒 สมุดชาวสวน

### 🔔 แจ้งเตือน

---

## Navigation Model

No bottom navigation is required in P0.

The Home Screen serves as the primary navigation hub.

---

# 5. Profile

The Profile menu may include:

* Switch Farm
* Settings
* Privacy
* Language
* Upload Status
* Storage Information
* About ARI
* Logout

---

# 6. Ask AI

## Purpose

Provide immediate access to external AI tools.

Supported AI providers may include:

* ChatGPT
* Gemini
* Claude
* Other AI applications

ARI does not guarantee correctness of AI responses.

Users are responsible for validating recommendations.

---

## Workflow

Ask AI

↓

Create AI Session

↓

Capture input

* Photo
* Video
* Voice
* Text
* File

↓

(Optional) Attach Context

* Farm
* Zone
* Tree

↓

Save Local

↓

Select AI

↓

Open External AI Application

↓

User Consults AI

↓

Return to ARI

↓

"What Did You Learn?"

* Voice
* Text

↓

(Optional) Create Follow-up

* 3 Days
* 7 Days
* 14 Days

↓

Save

↓

Store in Farm Notebook

---

## Follow-up Outcome

Users may later record:

* Improved
* No Change
* Worse
* Unknown

with optional notes.

---

# 7. เพิ่มบันทึก

## Purpose

Capture farm observations, experiences, and records.

---

## Notebook Session

A Notebook Session represents a single note.

Users may mix multiple media types within the same session.

Supported content:

* Photos
* Videos
* Voice Notes
* Text Notes
* Existing Photos
* Existing Videos
* Files

---

## Workflow

เพิ่มบันทึก

↓

Create Notebook Session

↓

(Optional) Attach Context

↓

Add Content

* Photo
* Video
* Voice
* Text

↓

Save

↓

Store Locally

↓

Upload Queue

↓

Future Processing

↓

Store in Farm Notebook

---

## Timeline-Based Capture

A single Notebook Session may contain:

Photo

↓

Voice

↓

Photo

↓

Video

↓

Voice

↓

Text

All items remain within the same note.

---

# 8. Farm Notebook

## Purpose

Provide access to historical records and farm memory.

---

## Core Functions

### Search

Users may search records using natural language.

Examples:

* เคยเจอโรคนี้ไหม
* ปีที่แล้วเกิดอะไรขึ้น
* เคยใช้ปุ๋ยนี้ไหม
* ใครเป็นคนบันทึก

---

### Filters

Examples include:

* All Records
* Stories
* Lessons
* Media
* AI Sessions

---

## Record View

A Notebook Record may display:

* Timeline
* Photos
* Videos
* Voice Notes
* Text Notes
* AI Summary
* Tags
* Date
* User
* Context Information

---

## Record Editing

Users may:

* Edit
* Continue Note
* Add Content
* Modify Tags

subject to permissions.

---

# 9. Notifications

## Supported Notifications

### Reminder

### Follow-up

### Upload Success

### Upload Failure

### AI Processing Complete

### System Alerts

---

## Follow-up Example

Reminder

↓

"What happened later?"

↓

Select:

* Improved
* No Change
* Worse
* Unknown

↓

Save Outcome

---

# 10. Offline-First Operation

The application shall support:

* Offline Capture
* Local Storage
* Deferred Upload
* Retry Upload
* Synchronization When Connected

Users shall be able to continue working without internet connectivity.

---

# 11. Context-Aware Note Capture

## Purpose

Support Digital Twin linkage while preserving low-friction data capture.

---

## Supported Context References

### Farm QR / Farm ID

### Zone QR / Zone ID

### Tree QR / Tree ID

---

## User Experience Principle

Context assignment is:

### Optional

but

### Recommended

Users shall be able to create:

* Notes
* Ask AI Sessions
* Reminders
* Follow-up Records

without QR scanning.

---

## Capture Priority

### 1. Capture Data

### 2. Attach Context

### 3. Validate Later

The system shall prioritize:

> Ease of Capture over Strict Data Entry Requirements

---

## Supported Context Sources

### Explicit Context

* QR Scan
* ID Selection

### Implicit Context

* Current Farm
* Current Zone
* Current Tree
* GPS Location
* Previous Activity
* User Context

Implicit context shall not be treated as confirmed context unless validated.

---

## Active Context

The application may maintain:

* Current Farm
* Current Zone
* Current Tree

as the active working context.

Users may continue creating records without re-scanning QR codes for every operation.

Users may:

* Change Context
* Clear Context
* Scan New Context

at any time.

---

## QR / ID Workflow

### Option A — Scan QR

Farm QR

↓

Zone QR

↓

Tree QR

↓

Create Record

---

### Option B — Select ID

Farm

↓

Zone

↓

Tree

↓

Create Record

---

### Option C — No Context

Create Record

↓

Save Record

↓

Attach Context Later (Optional)

---

## Supported Record Types

Context references may be attached to:

* Ask AI Sessions
* Notebook Records
* Photos
* Videos
* Voice Notes
* Text Notes
* Reminders
* Follow-up Records
* Evidence Records
* Sensor Readings
* Future AI Insights

---

## Strategic Objective

The Digital Farm Notebook shall be designed so that captured memory can be linked to the correct Farm, Zone, and Tree context whenever practical while preserving a low-friction user experience.

---

# 12. Simulator Farm Support

Supported simulator environments include:

* SIM-001
* SIM-002
* SIM-DURIAN
* SIM-MANGO
* SIM-TEST

Use cases:

* Testing
* Training
* Demo
* Dataset Creation

Simulator data shall remain logically separated from production farm data.

---

# 13. Accessibility

The application should support:

* Elderly farmers
* Low digital literacy users
* Outdoor operation
* Bright sunlight conditions

The user experience should minimize complexity and reduce required training.

---

# 14. P0 Scope Summary

The P0 user mental model is:

| User Intent                | Action        |
| -------------------------- | ------------- |
| Ask a question             | 🤖 Ask AI     |
| Record something           | ➕ เพิ่มบันทึก |
| Review history             | 📒 สมุดชาวสวน |
| Check tasks and follow-ups | 🔔 แจ้งเตือน  |

Users are not required to understand underlying data structures.

---

# 15. Future Enhancements

The following items are outside P0 scope but may be added in future phases:

* Farm Master Timeline
* Crop Playbooks
* Harvest Intelligence
* Fruit Identity Integration
* Commerce Integration
* Pre-Order Management
* Compliance Workflows
* Farm AIOS Integration
* Advanced AI Workflows
* Additional Knowledge Services

---

# 16. Status

Status: READY FOR HUMAN REVIEW

Human Verification Required: YES

This reconstruction is based only on confirmed decisions available from the conversation and should be reviewed by the project owner before being marked as FROZEN.


        ----------------------------------------
        After Owner Reviewed : ok -> Freeze 
        Reviewed by          : owner 
        Reviewed date        : 2026-06-14
        ----------------------------------------


รับทราบครับ

ARI V1 #46A
Mobile App UX Flow & Screen Specification

Status: FROZEN

Frozen Scope Includes
Mobile UX Foundation
Unified Mobile Application
RBAC-Based Access
Single Mobile App for all user roles
Home Screen
🤖 Ask AI
➕ เพิ่มบันทึก
📒 สมุดชาวสวน
🔔 แจ้งเตือน
👤 Profile
Ask AI Workflow
External AI Consultation
ChatGPT
Gemini
Claude
Learning Capture
Follow-up Workflow
Notebook Session Workflow
Photo
Video
Voice
Text
Existing Media
Mixed Media Support
Timeline-Based Note Structure
Farm Notebook
Search
Timeline
Stories
Lessons
Media
AI Sessions
Notification System
Reminder
Follow-up
Upload Status
System Alerts
Offline-First UX
Local Storage
Deferred Upload
Retry
Synchronization
Context-Aware Data Capture
Farm QR / Farm ID
Zone QR / Zone ID
Tree QR / Tree ID

Optional but Recommended

Active Context Model
Current Farm
Current Zone
Current Tree
Simulator Farm Support
SIM-001
SIM-002
SIM-DURIAN
SIM-MANGO
SIM-TEST
Unified Mobile Strategy

No Separate Farmer App

No Separate ARI Team Mobile App

One Mobile App

Role-Based Access Control

Frozen Decisions
Mobile P0 focuses on simplicity and usability.
Users should think only:
Ask
Record
Review
Learn
Context linkage is optional.
Capture-first is prioritized over strict data entry.
Home Screen remains the primary navigation model.
No Bottom Navigation in P0.
ARI Team uses the same mobile application as farmers.
Future features may be added without changing the core P0 philosophy.
Document Status

#46A Mobile App UX Flow & Screen Specification

✅ FROZEN

Ready to serve as baseline for:

#46B ARI Team Web App UX Flow & Screen Specification
#46C Data Model & Database Specification
#46D API & Backend Specification
#46E MVP Sprint Planning

ตอนนี้ #46A ถือเป็น Frozen Source of Truth สำหรับ Mobile UX ของ ARI P0 แล้วครับ 🌳📒🤖.