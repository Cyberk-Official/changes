---
type: improvement-plan
tags: [operations, sales, delivery, handover, process, handbook]
status: todo
priority: high
created-date: 2026-09-18
updated-date: 2026-09-18
author: anderson
owner: Anderson (CEO)
---

#### Cải tiến 40 (IP-040): Chuẩn Hóa Quy Trình Bàn Giao Sale → Dự Án (Pre-Kick-off Handover)

* **Mục tiêu:** Thiết kế và chuẩn hóa quy trình bàn giao nội bộ từ Sale/BD sang team Dự án (PO, Tech Lead, Dev Lead) **trước bước kick-off**. Đảm bảo mọi thông tin quan trọng từ quá trình đàm phán, deal context, kỳ vọng khách hàng, và ràng buộc kỹ thuật được truyền đạt đầy đủ — không mất mát, không tam sao thất bản.

* **Lý do (Tại sao):**
  * Hiện tại, sau khi Sale chốt deal, thông tin được truyền miệng hoặc qua chat Telegram/WhatsApp — dẫn đến team dự án thiếu context, phải hỏi lại nhiều lần, hoặc tệ hơn là hiểu sai kỳ vọng khách hàng.
  * Không có checklist chuẩn → mỗi lần bàn giao khác nhau, tùy thuộc vào ai là người bàn giao.
  * Handbook hiện có `po-kick-off/` (bắt đầu dự án) và `po-handover/` (bàn giao sản phẩm cho client), nhưng **thiếu hoàn toàn bước giữa: Sale → Dự án**.
  * Khi công ty scale lên, nếu không chuẩn hóa bước này sẽ thành bottleneck — đặc biệt khi có nhiều deal chạy song song.

* **Phạm vi (Scope):**
  * Quy trình này nằm **SAU** khi deal chốt trên Board SALE (Status = Contract/Review) và **TRƯỚC** bước kick-off chính thức.
  * Vị trí trong handbook: `05-product-owner/` — đặt trước `po-kick-off/`, ví dụ `po-pre-kickoff-handover/` hoặc `sale-to-project-handover/`.

* **Key Results (Kết quả cần đạt):**

  * *KR1 (Handover Checklist):*
    Xây dựng checklist bàn giao chuẩn bao gồm:
    - Thông tin khách hàng (contact, timezone, communication preference)
    - Deal context (scope đã chốt, giá trị, timeline cam kết)
    - Tài liệu liên quan (proposal, MSA, SOW, meeting notes)
    - Kỳ vọng khách hàng (ẩn và hiện — những gì đã nói và những gì ngầm hiểu)
    - Ràng buộc kỹ thuật (tech stack, infra, integration requirements)
    - Risks & Red flags từ quá trình đàm phán
    - Người liên hệ phía client (decision maker, technical contact, admin)

  * *KR2 (Handover Template):*
    Tạo template chuẩn (Markdown) để Sale/BD điền khi bàn giao — đảm bảo không thiếu thông tin quan trọng nào.

  * *KR3 (Quy trình trong Handbook):*
    Viết quy trình hoàn chỉnh vào handbook `05-product-owner/`, bao gồm:
    - Ai chịu trách nhiệm bàn giao (Sale/BD lead)
    - Ai nhận bàn giao (PO hoặc Tech Lead)
    - Hình thức bàn giao (meeting ngắn 30 phút + tài liệu)
    - Thời điểm bàn giao (trong vòng 2 ngày sau khi chốt deal)
    - Criteria: khi nào coi là "bàn giao thành công"

  * *KR4 (Tích hợp Board):*
    Kết nối quy trình với Board SALE — khi card chuyển sang cột `Contract`, trigger reminder bàn giao cho Sale lead.

* **Timeline:**

  | Bước | Mô tả | Ai | Khi nào |
  |------|-------|----|---------|
  | 1 | Anderson thiết kế quy trình & checklist | Anderson | Tuần 39 |
  | 2 | Viết handbook + template | Anderson + AI | Tuần 39-40 |
  | 3 | Pilot với 1-2 dự án thật | Sale + PO | Tuần 40+ |
  | 4 | Iterate dựa trên feedback | Team | Ongoing |

* **Liên kết:**
  * Handbook kick-off: [`po-kick-off/`](../../handbook/05-product-owner/po-kick-off/)
  * Handbook handover (client): [`po-handover/`](../../handbook/05-product-owner/po-handover/)
  * Board SALE: [GitHub Project #5](https://github.com/orgs/Cyberk-Official/projects/5)
  * Skill create-lead: [`proposal/skills/create-lead/`](../../proposal/skills/create-lead/)
