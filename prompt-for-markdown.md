*******************************************
***** Step 1 : Create Markdown file *******
*******************************************
1.copy ข้อความข้างล่างนี้ ไปใส่ prompt ให้สร้าง Markdown file ออกมา โดยแก้ไข เลขที่/ชื่อ เอกสารให้ตรงตามต้องการ

*********************************************


# ARI Target Document Reconstruction Export

---------------------------------------------------------
Target Document Number : #46A  **** (แก้ไขตามเลขเอกสาร)
Target Document Title  : Mobile App UX Flow & Screen Specification    ****  (แก้ตามชื่อเอกสาร)
Reconstruct only ARI V1 #46A from this conversation. **** (แก้ตามเลขเอกสาร)
---------------------------------------------------------


Rules:
1. Export only Document #46A
2. Ignore all content that belongs to #46, #46B, #47, or later documents.   **** แก้ตามจริง
3. Ignore all “prompt for new chat” sections for next documents.
4. Use the latest confirmed decisions related to #46A.  **** แก้ตามจริง
5. Do not invent new content.
6. Do not add new architecture.
7. Do not redesign ARI.
8. If a decision is unclear, place it under “Unverified / Needs Human Review”.
9. The output may organize and reconstruct the document into clean Markdown.
10. This is not a lossless export of the full chat. It is a reconstruction of the final target document from the available conversation.
11. Separate current P0 scope from Future Enhancements.
12. Preserve Frozen / Ready for Freeze / Revision status if stated.

Output as Markdown only.

Required metadata:
- Project: ARI — Agricultural Intelligence Platform
- Document Number: #46A  *** (แก้ไขตามเลขเอกสาร)
- Document Title: Mobile App UX Flow & Screen Specification  **** (แก้ไขตามเลขเอกสาร)
- Export Mode: Target Document Reconstruction Export
- Human Verification Required: YES
- Status: DRAFT until reviewed by project owner

-----------------------------------------------------------



***************************************
******  step 2 : Review & Freeze ******
***************************************
1.เราตรวจ Markdown chat ที่ตอบกลับมา
2. ถ้าถูกต้อง -> ให้ copy markdown chat นี้มาเก็บใน github ืในชื่อ : 46-MVP**.md และ เพิ่ม note นี้ต่อ

    ----------------------------------------
    After Owner Reviewed : Freeze 
    Reviewed by          : owner 
    Reviewed date        : 2026-06-14
    ----------------------------------------

3. ส่ง Prompt "Ok, Freeze now" ให้ chatgpt สรุปเป็น Frozen file มา

******************************************
******  Step 3 : Frozen Markdown file  ***
******************************************
1.ตรวจ Frozen chat ที่ตอบกลับมา 
2.ถ้าถูกต้อง -> ให้ copy Frozen chat นี้ไปเก็บต่อท้ายไฟล์ *.md ใน github
