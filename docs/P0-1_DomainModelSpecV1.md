# ARI Target Document Reconstruction Export

---------------------------------------------------------
Target Document Title:
ARI V1 — P0 Domain Model Specification v1.0
---------------------------------------------------------

Context:

This document is derived from the approved discussion after ARI documents:

#44 Farm AIOS
#45 Software Architecture & Monorepo Specification Rev2.0
#46 MVP Software Build Plan
#46A Mobile App UX Flow & Screen Specification
#46B Web App UX Flow & Screen Specification
#47 AI Agent Development Workflow Framework

Goal:

Reconstruct only the final agreed P0 Domain Model.

Rules:

1. Export only the final agreed Domain Model.
2. Do not redesign ARI.
3. Do not introduce new architecture.
4. Preserve all confirmed decisions:
   - Farm/Zone/Tree Nullable
   - entry_context exists in Domain Model
   - Consultation = Notebook Entry Type
   - Notebook Entry = Note Session
   - Note Item supports photo/video/voice/text/file/link
   - sequence_order support
   - Save ≠ Upload ≠ Analyze
5. Separate:
   - P0 Required
   - Optional Extension
   - Future Enhancement
   - Assumptions Requiring Owner Confirmation
6. Output Markdown only.



   ----------------------------------------
    After Owner Reviewed : Freeze 
    Reviewed by          : owner 
    Reviewed date        : 2026-06-15
    ----------------------------------------


รับทราบครับ

ARI V1 — P0 Domain Model Specification v1.0

Status: FROZEN

Freeze Confirmation

เอกสารต่อไปนี้ถือเป็น Source of Truth สำหรับการพัฒนา ARI P0 ในส่วน Domain Model:

ARI V1 — P0 Domain Model Specification v1.0
Status: FROZEN
Frozen Decisions
D1 — Identity Assignment
created_by_user_id = required
organization_id = required

farm_id = nullable
zone_id = nullable
tree_id = nullable
D2 — Entry Context
entry_context exists in Domain Model

แต่

ไม่บังคับให้ผู้ใช้เลือกใน Mobile P0
D3 — Consultation Model
Consultation = Notebook Entry Type

ไม่สร้าง Consultation Entity แยกใน P0

entry_type:
- note
- consultation
D4 — Notebook Structure
Notebook Entry = Note Session

รองรับ

Note Item
- photo
- video
- voice
- text
- file
- link
D5 — Timeline Support
sequence_order required

รองรับการบันทึกแบบ Timeline

photo
→ voice
→ photo
→ video
→ text
D6 — Link Support

รองรับ

YouTube
Facebook
TikTok
Website
Article
PDF URL

ผ่าน

item_type = link

ไม่เพิ่มเมนูใหม่ใน Mobile P0

D7 — Offline First
Save Local
≠ Upload
≠ Analyze

เป็นหลักการบังคับของ P0

D8 — Ownership Model
Organization owns data

Users create data
Freeze Scope

เอกสารนี้ใช้เป็นฐานสำหรับ:

Phase 2
P0 Database Schema Specification

และเป็น Domain Source of Truth สำหรับ:

Mobile App (#46A)
Web App (#46B)
FastAPI Backend
PostgreSQL Schema
RBAC Design
Offline Sync Design
Change Control

หลังจาก Freeze แล้ว

แนวคิดใหม่หรือการเปลี่ยนแปลงใด ๆ ต้องถูกระบุเป็น:

Revision Proposal

หรือ

Future Enhancement

ห้ามแก้ไขเนื้อหา Frozen โดยตรง

ARI V1 — P0 Domain Model Specification v1.0
FROZEN ✅

พร้อมเข้าสู่:

Phase 2 — P0 Database Schema Specification