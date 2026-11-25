# Review of docs/ai/backlog-draft.md
Reviewers: ten101popo and bankjunjan (Team 01). Checked against docs/intent/product.md and SMART.

| บรรทัดในร่าง | ปัญหา | ตัดสิน: แก้ ตัด หรือเก็บ |
|---|---|---|
| Story 1 (Browse available lab equipment by category) | ตรงกับ Proposed outcome ใน intent ครบ Connextra และวัดผล happy/sad ได้ชัดเจน | เก็บ (points:2) |
| Story 2 (Submit an equipment loan request) | ตรงกับความต้องการหลักของนักศึกษาและกติกายืมไม่เกิน 14 วัน | เก็บ (points:3) |
| Story 3 (Approve or reject pending loan requests) | ตรงกับบทบาท lab technician และป้องกันสต็อกติดลบเมื่อของหมด | เก็บ (points:3) |
| Story 4 (Record equipment return and update stock) | ตรงกับขั้นตอนรับคืนอุปกรณ์และแยกกรณีของชำรุดชัดเจน | เก็บ (points:2) |
| Story 5: "(assumed 2 days prior; *unconfirmed in intent*)" | ร่างสมมติจำนวนวันแจ้งเตือนเองแทนการถาม Open question ข้อ 1 | แก้: ถาม customer proxy (ยืนยันให้ส่งแจ้งเตือนล่วงหน้า 2 วันก่อนครบกำหนดคืน, points:3) |
| Story 6 (Manage lab equipment catalog and broken status) | ครอบคลุมทั้งการเพิ่ม แก้ไขสต็อก และตั้งสถานะชำรุด ขนาดค่อนข้างใหญ่ | แก้: เก็บเข้า Backlog ที่ขนาด points:5 เพื่อเตรียมแยกย่อยใน requirements clinic สัปดาห์ที่ 5 |
| Story 7 (Online loan renewal) | ตอบ Open question ข้อ 2 แทนลูกค้า ซึ่งลูกค้าตัดสินใจว่ายังไม่ทำระบบต่ออายุออนไลน์ในรอบแรก | ตัด |
| Story 8 (Late-return fine payment gateway) | ระบบเก็บค่าปรับและชำระเงินไม่ได้อยู่ใน intent เลย ลูกค้าไม่ได้ขอ | ตัด |

Kept: โครงสร้าง Story 1–4 และข้อกังวลเรื่อง Concurrent approvals กับ SMTP delivery reliability เพราะสอดคล้องกับ entity ทั้ง 3 ชนิด (Equipment, Borrower, LoanRequest), ผู้ใช้ 2 บทบาท และการเชื่อมต่อ SMTP ภายนอกตามที่ระบุใน intent
Counts: แก้ 2 ตัด 2 เก็บ 4
Customer proxy: ผู้สอน/ผู้ช่วยสอนยืนยัน Story 1 ถึง Story 6 เมื่อ 2026-11-25 (แจ้งเตือนล่วงหน้า 2 วัน และยังไม่เปิดต่ออายุออนไลน์ใน Iteration 0)
