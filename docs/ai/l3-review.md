# Review of docs/ai/l3-draft.md
Reviewers: Panussu and Peerapat-Aka. Checked against docs/intent/movie-filter.md and SMART.

| บรรทัดในร่าง | ปัญหา | ตัดสิน: แก้ ตัด หรือเก็บ |
|---|---|---|
| 23: "shall reject the call with an error that names the five allowed ratings" (REQ-10) | ผู้ปกครองเลือกจาก 5 ค่าที่มีอยู่ ไม่ได้พิมพ์ค่าเอง และลูกค้าไม่ได้ขอข้อความ error ที่ระบุ 5 ค่า | ตัด |
| 22: "shall return an empty list and shall not throw an exception" (REQ-9) | ร่างตอบ Open question ข้อ 1 แทนลูกค้าทั้งที่ลูกค้ายังไม่ได้ตัดสิน | แก้: ถาม customer proxy และใช้ผลยืนยัน (แสดงรายการว่างพร้อมข้อความ No movies with this rating) |
| 41: "The selection takes one call" (AC-1.5) | "one call" เป็นการวัดระดับโค้ด ไม่ใช่ผลที่ผู้ใช้สังเกตเห็นได้จากภายนอก จึงไม่ Measurable ตาม SMART | ตัด |
| 63-68: "Scenario: Selection is not one of the five ratings (sad path)" | ทดสอบ REQ-10 ที่ลูกค้าไม่ได้ขอ และผู้ใช้เลือกจากรายการ rating ที่กำหนดไว้แล้ว | ตัด |
| 70-73: "### Story 2: Newest first" | intent ระบุให้รายการทั้งหมดเรียงหนังใหม่ก่อน และ customer proxy ขอให้เรียงตามชื่อเรื่องได้ด้วย | แก้: เป็นบัตรใบที่ 2 (Sort movies: newest first or alphabetically) |
| 80-83: "### Story 3: Clear empty result" | ไม่ใช่ story ใหม่แยกต่างหาก แต่เป็น sad path ของ Story 1 (Filter by rating) | แก้: ย้ายไปเป็น Sad path ของบัตรใบที่ 1 |
| 97-102: "§4 Assumptions 1, 2, 6" | สมมติฐานสอดคล้องกับ domain classes (Movie, Rating, MovieCatalog) และชี้ชัดเรื่อง "newest" จาก release date | เก็บ |
| 110: "**Suitability is not the same as rating.**" | ข้อกังวลที่ถูกต้องและช่วยให้ทีมตระหนักถึงขอบเขตของ rating | เก็บ |

Kept: REQ-3, REQ-4, §4 Assumptions 1-2 & 6, and §5 "Suitability is not the same as rating" because they align with the intent, surface genuine domain boundaries, and do not invent unrequested behavior.
Counts: แก้ 3 ตัด 3 เก็บ 2
Customer proxy: Teacher/TA acting as customer proxy confirmed the 3 cards (single rating per selection, empty list with message "No movies with this rating" when none match, and alphabetical sorting in addition to newest-first).
