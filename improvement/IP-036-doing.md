---
type: improvement-plan
tags: [cyberk-way, crm, database, clients, bd, company-value, data-asset]
status: todo
priority: high
created: 2026-08-06
---

#### Cải tiến 36 (IP-036): Xây dựng Customer Intelligence Database — Tài sản Dữ liệu Khách hàng Cyberk

* **Mục tiêu:** Xây dựng hệ thống database khách hàng toàn diện bao gồm: hồ sơ khách hàng tiềm năng, lịch sử bidding, lịch sử tiếp cận và tương tác — biến dữ liệu khách hàng thành **tài sản có giá trị định lượng được của công ty**.

* **Lý do (Tại sao):**
  Dữ liệu khách hàng là **moat** (hào phòng thủ) của Cyberk — thứ đối thủ không thể copy ngay lập tức. Một công ty có Customer Intelligence tốt:
  - **Rút ngắn chu kỳ bán hàng**: Không phải bắt đầu từ zero với mỗi lead mới.
  - **Tăng tỷ lệ win rate bidding**: Hiểu lịch sử, pain point, budget cycle của khách.
  - **Tạo giá trị tài sản khi exit/M&A**: Buyer trả premium cho công ty có data sạch, structured.
  - **Phục vụ chiến lược S-006 (Cyberk 4M)**: Database khách hàng là 1 trong các tài sản quan trọng nhất khi định giá công ty.

* **Key Results (Kết quả cần đạt):**
  * *KR1 (Data Architecture — Kiến trúc dữ liệu):*
    Thiết kế và triển khai schema database khách hàng gồm các entity:
    - **Company Profile**: Tên, ngành, quy mô, địa lý, tech stack, ngân sách ước tính, nguồn (referral/inbound/outbound).
    - **Contact Profile**: Người phụ trách từng bên — role, email, LinkedIn, lịch sử tương tác cá nhân.
    - **Opportunity / Bidding Log**: Từng deal — ngày tiếp cận, scope, budget, trạng thái (won/lost/pending), lý do thắng/thua.
    - **Interaction Timeline**: Chronological log mọi touchpoint (email, call, meeting, demo, proposal).
    - **Potential Score**: Điểm tiềm năng tự động dựa trên fit (ngành, size, tech alignment với Cyberk).

  * *KR2 (Data Migration — Nhập dữ liệu lịch sử):*
    Migrate toàn bộ dữ liệu lịch sử từ các nguồn hiện tại vào database:
    - `clients/` folder (potential, strategic, ended, losed).
    - `bootstrap/bidding/` — lịch sử proposals và bidding.
    - Email/Telegram — extract deal conversations.
    - Đặt mục tiêu: **≥ 80% khách hàng đã từng tiếp cận trong 2 năm qua được nhập đầy đủ**.

  * *KR3 (Living Database — Vận hành ongoing):*
    Xây dựng quy trình cập nhật database liên tục:
    - SOP: Mỗi touchpoint với khách hàng → log vào database trong vòng 24h.
    - Weekly review: BD team review pipeline và update status.
    - Automated reminders: Nhắc follow-up khách hàng chưa liên hệ > 30 ngày.

  * *KR4 (Reporting & Intelligence):*
    Xây dựng bộ báo cáo từ database:
    - **Pipeline Report**: Tổng giá trị pipeline, win rate theo ngành/nguồn.
    - **Client Heatmap**: Phân loại khách theo potential score và engagement level.
    - **Bidding Analysis**: Lý do win/loss theo từng loại dự án.
    - Tích hợp vào **Cyberk Dashboard** (liên kết với IP Dashboard).

* **Data Sources (Nguồn dữ liệu):**
  | Nguồn | Loại dữ liệu | Ưu tiên |
  |-------|-------------|---------|
  | `clients/potential/` | Hồ sơ khách tiềm năng hiện tại | P0 |
  | `clients/strategic/` | Khách hàng chiến lược | P0 |
  | `bootstrap/bidding/` | Lịch sử proposals | P0 |
  | `clients/ended/` | Khách đã kết thúc | P1 |
  | `clients/losed/` | Deal đã thua | P1 — học từ thất bại |
  | Email / Telegram | Touchpoint history | P2 |
  | LinkedIn Sales Nav | Profile enrichment | P2 |

* **Tech Stack khuyến nghị:**
  - **Short-term**: Structured Markdown trong `clients/` + `bootstrap/` có metadata frontmatter chuẩn hóa.
  - **Mid-term**: Notion Database hoặc Lark Base (Bitable) — dễ dùng, visual, có filter/sort.
  - **Long-term**: PostgreSQL + dashboard tích hợp vào Cyberk internal tool.

* **Open Questions (Câu hỏi mở & Thảo luận):**
  * *Câu hỏi 1 (Tool):* Dùng Lark Base, Notion, hay tự build? → *Khuyến nghị Lark Base trước vì đã có Lark Super Admin.*
  * *Câu hỏi 2 (Ownership):* Ai là người chủ sở hữu database này? BD Lead hay CEO? → *Cần assign 1 người DRI (Directly Responsible Individual).*
  * *Câu hỏi 3 (Privacy):* Chính sách bảo mật dữ liệu khách hàng — ai được xem toàn bộ, ai chỉ xem phần mình phụ trách?
  * *Câu hỏi 4 (Potential Score):* Tiêu chí tính điểm tiềm năng khách hàng là gì? (Ngành, budget, geography, tech fit?)

* **Risks (Rủi ro & Biện pháp):**
  * *Rủi ro 1:* **Dữ liệu lịch sử phân tán, khó consolidate** — mỗi người lưu theo cách riêng. → *Mitigation:* Assign 1 sprint 2 tuần để data cleanup tập trung.
  * *Rủi ro 2:* **Không duy trì được thói quen log** — database chết dần sau vài tuần. → *Mitigation:* Build vào workflow daily (NEO bot nhắc log, SOP check-in hàng tuần).
  * *Rủi ro 3:* **Chọn sai tool, phải migrate sau** — mất công lần 2. → *Mitigation:* Chuẩn hóa schema data trước, tool là thứ yếu — schema đúng thì migrate dễ.

* **Dependencies (Phụ thuộc):**
  * `clients/` — Source data chính.
  * `bootstrap/bidding/` — Lịch sử bidding.
  * IP Dashboard (liên kết với bộ công cụ và dashboard của Cyberk).
  * S-006 (Cyberk 4M) — Database này là 1 asset quan trọng khi exit.

* **Timeline dự kiến:**
  | Giai đoạn | Nội dung | Deadline |
  |-----------|----------|----------|
  | Phase 1 | Design schema + chọn tool | T+1 tuần |
  | Phase 2 | Migrate dữ liệu lịch sử | T+3 tuần |
  | Phase 3 | SOP + quy trình vận hành ongoing | T+4 tuần |
  | Phase 4 | Dashboard & reporting tích hợp | T+6 tuần |

* **Status:** `todo`
* **Thực tế (Ghi chú/Dấu vết):**
  * 2026-08-06: Khởi tạo IP theo định hướng Tiên Tôn Anderson — coi Customer Intelligence Database là tài sản cốt lõi phục vụ S-006 (Cyberk 4M).

---
