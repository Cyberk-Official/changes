---
type: improvement-plan
tags: [cyberk-way, operations, leadership, meeting, documentation]
status: todo
priority: high
created: 2026-06-13
---

#### Cải tiến 33 (IP-033): Chuẩn hoá Phương thức Vận hành cho các Dự án

* **Mục tiêu:** Tái cơ cấu cách thức vận hành dự án tại Cyberk — đưa leader ngồi gần team, thiết lập lịch họp dự án định kỳ có báo cáo, và viết lại tài liệu "Bí kíp phát triển dự án" làm kim chỉ nam cho toàn bộ nhân sự.
* **Lý do (Tại sao):**
  * Leader ngồi tầng khác gây ra khoảng cách vật lý với team — giảm khả năng nắm bắt vấn đề real-time, chậm ra quyết định.
  * Hiện chưa có lịch họp dự án cố định giữa Trường và Hương → dễ bỏ sót dự án, thiếu đồng bộ thông tin giữa hai leader chính.
  * Tài liệu "Bí kíp phát triển dự án" cũ đã lỗi thời, không phản ánh quy trình AI-native và Solo-dev hiện tại → nhân sự mới không có tài liệu chuẩn để onboard.
  * Cyberk đang scale — cần chuẩn hoá vận hành để dù ai quản lý cũng ra kết quả như nhau.

* **Key Results (Kết quả cần đạt):**
  * *KR1 — Chuyển chỗ ngồi:* Trường + Hương chuyển xuống tầng 1 ngồi gần khu phức tổ chức meeting để dễ quan sát. Hoàn thành trong tuần đầu tiên.
  * *KR2 — Lịch họp dự án:* Thiết lập lịch họp cố định giữa Trường + Hương cho từng dự án đang chạy (Trường tối thiểu 2 lần/tuần/dự án, Hương tối thiểu 1 lần/tuần/dự án). Mỗi buổi họp có meeting report gửi lên kênh tương ứng trong vòng 24h.
  * *KR3 — Báo cáo tuần:* Hằng tuần có 1 bản tổng hợp báo cáo tiến độ tất cả dự án (Weekly Project Status Report) lên nhóm leader.
  * *KR4 — Bí kíp phát triển dự án v2:* Viết lại hoàn toàn tài liệu, phản ánh đúng quy trình hiện tại: AI-native development, Solo-dev, 1-Day Sprint, review meeting 3-phase. Publish lên gitbook.

* **Plans (Kế hoạch hành động):**

  **Phase 1 — Tái bố trí không gian làm việc (Tuần 1)**
  1. Sắp xếp lại bàn làm việc tầng 1 — đảm bảo đủ chỗ cho Trường + Hương + thiết bị.
  2. Trường + Hương chuyển xuống tầng 1, ngồi gần khu dev/QA.
  3. Thông báo cho toàn công ty về thay đổi cơ cấu vật lý và lý do.

  **Phase 2 — Thiết lập hệ thống họp dự án (Tuần 1–2)**
  1. Liệt kê tất cả dự án đang active + người phụ trách (Trường/Hương).
  2. Lập lịch họp cố định cho từng dự án — gắn vào Google Calendar, share cho team.
  3. Định nghĩa cấu trúc meeting report chuẩn: Participants, Status, Blockers, Action Items, Next Steps.
  4. Chọn kênh gửi report (Telegram hoặc Slack channel tương ứng).
  5. Thiết lập template Weekly Project Status Report — tổng hợp từ các meeting report trong tuần.
  6. Giao trách nhiệm cụ thể: ai tổng hợp, ai review, ai gửi lên C-LEVEL.

  **Phase 3 — Viết lại "Bí kíp phát triển dự án" (Tuần 2–4)**
  1. Review tài liệu cũ — xác định phần nào còn giá trị, phần nào bỏ.
  2. Thu thập input từ Trường, Hương, và các senior dev về quy trình thực tế đang dùng.
  3. Viết lại theo cấu trúc mới, bao gồm các chương:
     - Tổng quan triết lý phát triển (AI-native, Solo-dev)
     - Quy trình kick-off dự án (liên kết IP-029)
     - 1-Day Sprint: cách hoạt động, bàn giao hàng ngày
     - Review Meeting 3-Phase: Review → Fix-bugs → Tổng kết (liên kết IP-031)
     - Công cụ và stack kỹ thuật chuẩn
     - Quy trình QA và kiểm thử
     - Bàn giao và đóng dự án
  4. Review nội bộ — Trường, Hương, Anderson approve.
  5. Publish lên gitbook (`gitbook/dev/bi-kip-phat-trien-du-an-v2.md`).

* **Phân công:**

  | Task | Người phụ trách | Mô tả | Deadline | Phụ thuộc | Trạng thái |
  |------|----------------|-------|----------|-----------|------------|
  | IP-033-T1 | `Trường + Hương` | Chuyển chỗ ngồi xuống tầng 1 | 2026-06-20 | — | `todo` |
  | IP-033-T2 | `Trường + Hương` | Lập lịch họp dự án + template meeting report | 2026-06-27 | IP-033-T1 | `todo` |
  | IP-033-T3 | `Trường` | Thiết lập Weekly Project Status Report | 2026-06-27 | IP-033-T2 | `todo` |
  | IP-033-T4 | `Trường + Hương + Anderson` | Viết lại Bí kíp phát triển dự án v2 | 2026-07-11 | IP-033-T2 | `todo` |
  | IP-033-T5 | `Anderson` | Review & publish lên gitbook | 2026-07-14 | IP-033-T4 | `todo` |

* **Risks (Rủi ro & Biện pháp):**
  * *Rủi ro 1:* **Kháng cự chuyển chỗ** — Leader quen ngồi tầng riêng, cảm thấy mất tập trung khi ngồi chung. → *Mitigation:* Giải thích rõ mục đích (proximity = tốc độ ra quyết định). Bố trí chỗ ngồi có không gian riêng tư hợp lý (vách ngăn, tai nghe chống ồn).
  * *Rủi ro 2:* **Họp nhiều → chiếm thời gian làm việc** — 2 meeting/tuần/dự án × nhiều dự án = lịch kín. → *Mitigation:* Time-box mỗi buổi họp 30 phút tối đa. Ưu tiên async update nếu không có blocker. Cho phép skip nếu dự án ổn định.
  * *Rủi ro 3:* **Tài liệu bí kíp viết xong nhưng không ai đọc** — trở thành "tài liệu ngăn kéo". → *Mitigation:* Bắt buộc đọc trong tuần onboard đầu tiên. Gắn quiz/checklist kiểm tra. Leader nhắc trong meeting khi nhân sự vi phạm quy trình.
  * *Rủi ro 4:* **Meeting report nửa vời** — ghi chép sơ sài, thiếu action items. → *Mitigation:* Dùng AI tự động ghi meeting minutes (liên kết IP-003). Template bắt buộc — không đủ field thì không submit được.

* **Liên kết với các IP khác:**
  * [[IP-003-doing]] — Tự động hóa Meeting Minutes
  * [[IP-012-doing]] — Tái cấu trúc Tổ chức theo Solo-Dev
  * [[IP-029-doing]] — Chuẩn hóa Quy trình Kick-off Dự án Mới
  * [[IP-031-doing]] — Tái thiết lại các cuộc họp công ty & 1-Day Sprint

* **Status:** `Chưa bắt đầu`
* **Thực tế (Ghi chú/Dấu vết):**
  * 2026-06-13: Khởi tạo IP từ yêu cầu CEO. Mục tiêu chuẩn hoá vận hành cho scale.
