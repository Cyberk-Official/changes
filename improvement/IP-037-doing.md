---
type: improvement-plan
tags: [operations, project-management, dashboard, governance, performance, cyberk-way]
status: todo
priority: high
created: 2026-08-11
owner: Anna (announce), Brian (review)
---

#### Cải tiến 37 (IP-037): Quản lý Cyberk theo Dự án — Project-Based Governance

* **Mục tiêu:** Chuyển đổi mô hình quản trị Cyberk từ theo phòng ban sang **theo dự án** — mỗi dự án là một đơn vị đo lường hiệu suất độc lập. Tăng năng lực quản trị, tạo khả năng đo lường và truy vết hiệu suất của toàn công ty theo từng project.

* **Phạm vi áp dụng:**
  IP này áp dụng cho **toàn bộ các team và dự án** tại Cyberk, bao gồm:

  | Team | Mô tả |
  |------|--------|
  | 🛠️ **Dev** | Các dự án phát triển phần mềm, outsourcing, internal tools |
  | 🎬 **Media** | Các dự án sản xuất nội dung, video, marketing content |
  | 🎨 **Design** | Các dự án thiết kế UI/UX, branding, visual assets |
  | 🔍 **QA** | Các dự án kiểm thử, audit, bảo mật |

  > Mọi team lead của 4 bộ phận trên đều chịu trách nhiệm triển khai đầy đủ 4 KR trong phạm vi team mình.

* **Lý do (Tại sao):**
  Hiện tại Cyberk đang thiếu một lớp **visibility** đủ granular để trả lời các câu hỏi: *"Dự án X đang chạy thế nào? Team lead Y có đang track task đúng không? Member Z có deadlines rõ ràng không?"* Project-based governance giải quyết điều đó bằng cách:
  - **Truy vết hiệu suất thực tế**: Dashboard dự án = sự thật không thể tranh luận.
  - **Tăng accountability**: Mỗi task có deadline + assignee + estimate + label → không ai có thể "quên".
  - **Tạo nền tảng cho Personal KPI**: Dashboard cá nhân là input cho đánh giá nhân viên.
  - **Chuẩn bị cho scaling**: Khi công ty lớn hơn, governance theo project là bắt buộc.

* **Key Results (Kết quả cần đạt):**

  * *KR1 — Project Dashboard (Tuần 33):*
    **100% dự án của Cyberk có dashboard.**
    - Mỗi dự án có 1 GitHub Project Board hoặc tương đương đang hoạt động.
    - Dashboard hiển thị: Trạng thái task, burndown, blockers, upcoming deadlines.
    - **Owner:** Brian + Team Leads.
    - **Deadline:** Cuối Tuần 33 (≈ 2026-08-15).

  * *KR2 — Task Quality Standard:*
    **100% task được tạo ra có đủ 4 trường bắt buộc: Deadline · Assignee · Estimate · Label.**
    - Định nghĩa "hợp lệ": task thiếu bất kỳ 1 trong 4 trường = invalid task.
    - Áp dụng cho: GitHub Issues, Lark Tasks hoặc bất kỳ tool PM nào đang dùng.
    - **Metric đo lường:** % task hợp lệ / tổng task mới trong tuần.
    - **Owner:** Từng Team Lead chịu trách nhiệm cho team mình.

  * *KR3 — Weekly Sprint Dashboard:*
    **100% dự án có Weekly Dashboard (Sprint Dashboard).**
    - Mỗi tuần, Brian tổng hợp Sprint Report cho từng dự án: % completion, velocity, blockers.
    - Format: Markdown hoặc dashboard link gửi lên Telegram/Lark thứ 6 hàng tuần.
    - **Owner:** Brian.

  * *KR4 — Personal Dashboard:*
    **100% member có Personal Dashboard.**
    - Mỗi member có view cá nhân: task đang làm, task quá hạn, estimate vs. actual.
    - Cập nhật tự động từ Project Board.
    - **Owner:** Brian setup, member tự maintain.

* **Cấu hình Task chuẩn (GitHub Project Fields):**
  Dựa trên config đính kèm, các field bắt buộc:

  | Field | Bắt buộc | Ghi chú |
  |-------|----------|---------|
  | Title | ✅ | Tên task rõ ràng |
  | Assignees | ✅ | Phải có ≥ 1 người |
  | Status | ✅ | Todo / In Progress / Done |
  | Labels | ✅ | Phân loại: feature, bug, chore, design... |
  | Priority | ✅ | P0/P1/P2 |
  | Start date | ✅ | Ngày bắt đầu |
  | Target date | ✅ | **Deadline** |
  | Effort | ✅ | Độ phức tạp (S/M/L/XL) |
  | Estimate | ✅ | Giờ công ước tính |
  | Milestone | ✅ | Gắn mã IP/milestone đại diện (ví dụ: IP-037) |
  | Week | ✅ | Tuần thực hiện trong năm (ví dụ: Tuần 33, 34, 35) |
  | Type | Khuyến nghị | Task / Bug / Feature / Spike |

* **Execution Plan (Kế hoạch hành động tinh gọn):**

  | Task | Bộ phận | Người thực hiện | Mô tả | Deadline | Phụ thuộc | Trạng thái |
  |------|---------|-----------------|-------|----------|-----------|------------|
  | `[IP-037] Họp Kick-off Leaders` | `LEADERS` | `anderson` | Họp kick-off: align mục tiêu IP-037, phân công roles | 2026-08-11 | — | `todo` |
  | `[IP-037] Gửi thông báo Telegram W33-W36` | `ALL` | `anna` | Soạn & gửi 4 thông báo Telegram thứ 2 hàng tuần (09:00) | 2026-09-01 | Kick-off | `todo` |
  | `[IP-037] Setup Board Dashboard & Auto Report Telegram` | `LEADERS` | `anderson` | Setup board dashboard & tự động báo cáo nhóm Telegram thứ 5 | 2026-09-01 | Kick-off | `todo` |

* **Kế hoạch triển khai — 4 Tuần:**

  | Tuần | KR | Người thông báo | Nội dung thông báo (Thứ 2 - 09:00) |
  |------|----|----------------|-------------------------------------|
  | Tuần 33 | KR1 | Anna | 100% dự án phải có Project Dashboard — Brian + Team Leads setup ngay |
  | Tuần 34 | KR2 | Anna | 100% task mới từ hôm nay phải có đủ: Deadline + Assignee + Estimate + Label |
  | Tuần 35 | KR3 | Anna | 100% dự án phải có Weekly Sprint Dashboard — Brian tổng hợp mỗi thứ 6 |
  | Tuần 36 | KR4 | Anna | 100% member phải có Personal Dashboard — Brian setup, mỗi người tự xem |

  **Lịch cố định hàng tuần:**
  - **Thứ 2 (09:00):** Anna gửi thông báo key-result tuần đó lên Telegram ALL.
  - **Thứ 5:** Brian + Team Leads báo cáo tỉ lệ chuyển đổi của bộ phận. Nêu rõ member chưa hoàn thành.

* **Kick-off Actions (Việc cần làm ngay):**
  - [ ] Họp Leader để align về IP này và cách triển khai.
  - [ ] Anna soạn 4 thông báo Telegram (1 per KR) — gửi thứ 2 hàng tuần.
  - [ ] Brian kiểm kê danh sách dự án đang chạy → setup dashboard cho từng dự án.
  - [ ] Brian định nghĩa template Sprint Report chuẩn.
  - [ ] Team Leads audit task hiện tại → bổ sung các trường còn thiếu.
  - [ ] Thêm reminder NEO bot cho Anna (thứ 2) và Brian (thứ 5).

* **Người thực hiện:**
  | Vai trò | Người | Trách nhiệm |
  |---------|-------|------------|
  | Announce | Anna | Gửi thông báo thứ 2 hàng tuần theo KR |
  | Review | Brian | Báo cáo thứ 5, setup dashboard, sprint report |
  | Execute | Team Leads | Setup project board, đảm bảo task quality |
  | Oversight | Anderson (CEO) | Kiểm tra tổng thể, unblock nếu cần |

* **Risks (Rủi ro):**
  * *Rủi ro 1:* **Team Leads không có thời gian setup dashboard** → Mitigation: Brian hỗ trợ setup template cho từng dự án, chỉ cần Team Lead fill data.
  * *Rủi ro 2:* **Task cũ không có đủ trường** → Mitigation: Chỉ enforce cho task mới từ KR2 trở đi. Task cũ: "best effort".
  * *Rủi ro 3:* **Thói quen không bền** → Mitigation: NEO bot nhắc thứ 5 + báo cáo công khai tỉ lệ compliance hàng tuần — tạo áp lực peer accountability.

* **Dependencies:**
  * GitHub Projects (hoặc tool PM đang dùng) — phải xác nhận tool nào là chuẩn.
  * IP-033 (Chuẩn hoá Phương thức Vận hành) — IP này là bước tiếp theo sau IP-033.
  * Cyberk Dashboard — Personal & Project Dashboard có thể tích hợp.
  * NEO Bot — Telegram reminders cho Anna (thứ 2) và Brian (thứ 5).

* **Timeline:**
  | Giai đoạn | Nội dung | Deadline |
  |-----------|----------|----------|
  | Kick-off | Họp leader, align, assign roles | Tuần 33 (2026-08-11) |
  | KR1 | 100% dự án có dashboard | Cuối tuần 33 (2026-08-15) |
  | KR2 | 100% task có đủ 4 trường | Tuần 34 (2026-08-18) |
  | KR3 | 100% dự án có sprint weekly | Tuần 35 (2026-08-25) |
  | KR4 | 100% member có personal dashboard | Tuần 36 (2026-09-01) |
  | Review | Anderson review toàn bộ tỉ lệ đạt | Tuần 37 (2026-09-08) |

* **Status:** `doing`
* **Thực tế (Ghi chú/Dấu vết):**
  * 2026-08-11: Khởi tạo IP-037 theo yêu cầu của Tiên Tôn Anderson. Mục tiêu: chuyển đổi governance sang project-based management, tăng khả năng đo lường hiệu suất. Sẽ cần họp leader để kick-off.
  * 📌 **Lưu ý hỗ trợ:** Khi tạo board gặp khó khăn, hãy liên hệ với **Brian** hoặc **Anderson** để được hỗ trợ.
  * 🗓️ **Lưu ý triển khai:** Kế hoạch được chia làm **4 tuần với 4 key-result** để bộ máy không bị ngợp — mỗi tuần chỉ tập trung vào **1 item duy nhất**. Không chạy song song nhiều KR cùng lúc.
  * 🤖 **Cách triển khai:** Anna thông báo + kèm link Handbook → member **tự đọc và tự setup**, không cần training hay họp thêm. Brian dùng **AI + GitHub CLI** để tự động kiểm tra trạng thái board từng bộ phận và tạo báo cáo thứ 5 — không thu thập thủ công.

---
