ARI Markdown Export Standard v1.0

Status: FROZEN

================================================

TARGET DOCUMENT LOCK

Document Number: #46
Document Title : MVP Software Build Plan

Only export this document.

Ignore:

- New Chat Prompts
- Next Document Prompts
- Future Document Definitions
- Follow-up Document Templates
- Revision Drafts for other documents
- Subsequent documents (#46A, #46B, #47, etc.)

================================================

แปลงเอกสารนี้เป็น Markdown พร้อมหัวข้อให้ครบถ้วน ตามกฎต่อไปนี้อย่างเคร่งครัด

## Critical Rules

1. ห้ามสรุป
2. ห้ามตัดเนื้อหา
3. ห้ามตีความใหม่
4. ห้ามเพิ่มแนวคิดใหม่
5. ห้ามแก้ Architecture
6. ห้ามแก้ Governance
7. ห้ามแก้ Workflow
8. ห้ามแก้ UX
9. ห้ามแก้ Data Model
10. ห้ามแก้ Operating Model
11. ห้ามรวมประเด็นจนรายละเอียดหาย
12. ห้ามเปลี่ยนคำตัดสินใจเดิม
13. ให้รักษาเนื้อหาเดิมให้ครบมากที่สุด
14. ถ้ามีหลาย Revision ให้เก็บเฉพาะ Revision ล่าสุดที่เป็น Final / Frozen / Ready for Freeze
15. ถ้ามีข้อขัดแย้งในบทสนทนา ให้ใช้ข้อสรุปล่าสุดเท่านั้น
16. ถ้าไม่แน่ใจว่าอะไรคือข้อสรุปล่าสุด ให้ใส่ไว้ในหัวข้อ:

## Unverified / Needs Human Review

17. ห้ามสร้างเนื้อหาใหม่เพื่อเติมช่องว่าง
18. ห้ามเดา
19. ห้ามขยายความเกินกว่าที่ปรากฏในเอกสารต้นฉบับ
20. ถ้าข้อมูลไม่ปรากฏในเอกสาร ให้ระบุว่าไม่พบข้อมูล

---

# Export Objective

วัตถุประสงค์ของการ Export คือ

Lossless Markdown Export

ไม่ใช่ Summary

ไม่ใช่ Rewrite

ไม่ใช่ Improvement

ไม่ใช่ Refactoring

ไม่ใช่ Architecture Review

ไม่ใช่ Enhancement Proposal

ต้องรักษาข้อมูลต้นฉบับให้ครบมากที่สุดเท่าที่เป็นไปได้

---

# Required Markdown Structure

ให้จัดเอกสารเป็น Markdown ตามโครงสร้างนี้

```markdown
# ARI V1 #[Document Number]

[Document Title]

## Document Metadata

- Project: ARI — Agricultural Intelligence Platform
- Document Number: #[Document Number]
- Document Title: [Title]
- Version / Revision: [Version if known]
- Status: DRAFT / READY FOR FREEZE / FROZEN / VERIFIED
- Source Type: Chat-derived Markdown Export
- Export Standard: ARI Markdown Export Standard v1.0
- Human Verification Required: YES
- Last Updated: [Date if known]

---

## Governance Notice

This document is a structured Markdown export from ARI project discussions.

This document shall not be treated as final Source of Truth until reviewed and marked as:

Status: VERIFIED

or

Status: FROZEN

by the project owner.

---

## Purpose

[Keep original purpose.]

---

## Scope

[Keep original scope.]

---

## Core Decisions

[List all confirmed decisions.]

---

## Main Content

[Full document content with complete headings and subheadings.]

---

## Frozen Decisions

[List decisions explicitly agreed as frozen.]

---

## Ready for Freeze Items

[List items ready for freeze but not yet frozen.]

---

## Open Questions

[List unresolved items only if present.]

---

## Future Enhancements

[List only items explicitly marked future.]

---

## Optional Extensions

[List only items explicitly marked optional.]

---

## Revision Proposals

[List only items explicitly marked revision proposal.]

---

## Unverified / Needs Human Review

[List only items that cannot be verified.]

---

## Validation Checklist

- [ ] No intentional summary
- [ ] No intentional deletion
- [ ] No new architecture added
- [ ] Latest decision preserved
- [ ] Conflicting older ideas removed or marked obsolete
- [ ] Frozen decisions clearly marked
- [ ] Future items separated from current scope
- [ ] Human reviewed
- [ ] Ready to commit to repository

---

## Status

Current Status: DRAFT
```

---

# Output Requirement

ให้ Output เป็น Markdown เท่านั้น

ห้ามใส่คำอธิบายก่อนเอกสาร

ห้ามใส่คำอธิบายหลังเอกสาร

ห้ามแสดงความคิดเห็นของ AI

ห้ามสรุปท้ายเอกสาร

ห้ามเพิ่มข้อเสนอแนะ

ห้ามเพิ่ม Future Ideas ที่ไม่ปรากฏในต้นฉบับ

ห้ามเพิ่ม Architecture ใหม่

ถ้าพบข้อมูลที่ไม่สามารถยืนยันได้

ให้ย้ายไปหัวข้อ

## Unverified / Needs Human Review

เท่านั้น
