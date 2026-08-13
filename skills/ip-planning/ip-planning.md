---
type: workflow
tags: [cyberk-way]
description: Lập kế hoạch chi tiết cho IP (IP Planning) — bổ sung execution plan vào IP và xuất file plans/IP-[XXX]/plan.csv.
---

# Quy trình Lập Kế hoạch IP (IP Planning)

> Workflow này tập trung vào **lập kế hoạch (planning)** — từ IP đã được hoạch định ở `ip-create`,
> bổ sung bảng Execution Plan vào file IP và xuất ra file **`plan.csv`** chứa toàn bộ danh sách task chi tiết.
> **Phạm vi:** Workflow dừng lại ở việc tạo ra `plan.csv`, chưa đẩy tự động lên các hệ thống quản lý task hay thực thi.
> **Điều kiện:** IP đã được tạo qua `skills/ip-create/ip-create.md`.

---

## Hệ thống file liên quan

| File / Folder | Vai trò |
|---------------|---------|
| `improvement/IP-[XXX]-doing.md` | File IP (đã tạo ở giai đoạn hoạch định) |
| `improvement/kanban-board.md` | Cập nhật trạng thái IP → `doing` |
| `plans/IP-[XXX]/plan.csv` | **Plan dạng bảng** — sản phẩm đầu ra chính của workflow này |
| `scheduler.csv` | Lịch theo dõi tổng — assign, follow, review |

---

## Các bước thực hiện

### Bước 1 — Bổ sung Execution Plan vào file IP

1. Mở file IP (`improvement/IP-[XXX]-doing.md`).
2. Bổ sung mục **Execution Plan (Kế hoạch hành động theo bộ phận)** — bảng task chia theo bộ phận/đơn vị:

   | Task | Bộ phận | Mô tả | Deadline | Phụ thuộc | Trạng thái |
   |------|---------|-------|----------|-----------|------------|
   | IP-[XXX]-MKT | `MKT` | ... | YYYY-MM-DD | — | `todo` |
   | IP-[XXX]-DEV | `DEV` | ... | YYYY-MM-DD | IP-[XXX]-MKT | `todo` |

3. Quy tắc:
   - Mã task: `IP-[XXX]-[BỘ_PHẬN]` (ví dụ: IP-037-DEV, IP-037-QA).
   - Deadline phải tuân thứ tự phụ thuộc.

---

### Bước 2 — Tạo file plan.csv (Sản phẩm đầu ra chính)

> Toàn bộ các task trong Execution Plan được chi tiết hóa và xuất ra **1 file CSV duy nhất** tại `plans/IP-[XXX]/plan.csv`.

1. Tạo folder `plans/IP-[XXX]/` nếu chưa có.
2. Tạo file `plans/IP-[XXX]/plan.csv`.
3. Cấu trúc các **cột trong `plan.csv`** (dựa trên chuẩn GitHub Project fields):

   ```csv
   title,assignees,status,labels,milestone,week,type,priority,start_date,target_date,estimate,body
   ```

   | Cột | Yêu cầu | Ý nghĩa | Giá trị mẫu |
   |-----|---------|---------|-------------|
   | `title` | **BẮT BUỘC** | Tên task rõ ràng | `[IP-037-DEV] Setup Project Board — Dev Team` |
   | `assignees` | **BẮT BUỘC** | **GitHub ID cụ thể** của member | `cyberk-io`, `anderson-cyberk` |
   | `status` | **BẮT BUỘC** | Trạng thái ban đầu (**Mặc định: `Backlog`**) | `Backlog` / `In Progress` / `Done` |
   | `labels` | **BẮT BUỘC** | Nhãn phân loại task | `operations`, `governance`, `dev` |
   | `milestone` | **BẮT BUỘC** | **Chính là tên IP** (ví dụ: `IP-037`) | `IP-037` |
   | `week` | **BẮT BUỘC** | **Số tuần thực hiện trong năm** (ví dụ: `33`, `34`, `35`) | `33` |
   | `type` | Khuyên dùng | Loại công việc | `Task` / `Bug` / `Feature` |
   | `priority` | **BẮT BUỘC** | Mức độ ưu tiên | `High` / `Medium` / `Low` |
   | `start_date` | **BẮT BUỘC** | Ngày bắt đầu | `YYYY-MM-DD` |
   | `target_date` | **BẮT BUỘC** | Deadline | `YYYY-MM-DD` |
   | `estimate` | **BẮT BUỘC** | Ước tính giờ công | `3` (giờ) |
   | `body` | **BẮT BUỘC** | Mô tả chi tiết & Checklist | Nội dung Markdown (mục tiêu, việc cần làm, lưu ý) |

   > [!IMPORTANT]
   > Các trường **`assignees`**, **`target_date` (deadline)**, **`labels`**, **`milestone`**, và **`week`** là **BẮT BUỘC TUÂN THỦ**.
   > Trong đó:
   > - **`assignees`**: Phải là **GitHub ID chính xác** của thành viên thuộc `Cyberk-Official` (không dùng tên chung chung).
   > - **`status`**: Mặc định khởi tạo là **`Backlog`**.
   > - **`milestone`**: Phải được gán đúng mã/tên IP (ví dụ: `IP-037`).
   > - **`week`**: Phải xác định số tuần thực hiện (ví dụ: `33`, `34`, `35`).

### Danh sách GitHub Assignees Khả Dụng (`Cyberk-Official`)

Khi lập kế hoạch (planning), chọn **chính xác GitHub ID** từ bảng danh sách bên dưới để assign:

| Tên Nhân Sự / Vai Trò | GitHub ID chuẩn | Ghi Chú |
|-----------------------|-----------------|---------|
| **Anna** | `anna-cyberk` | Quản lý thông báo, phối hợp chung |
| **Anderson** (CEO) | `anderson-cyberk` | Quản trị, điều hành, duyệt IP/PRD |
| **Hùng DN** | `hungdn-cyberk` | Team Lead / Dev |
| **Trường LX** | `truonglx-cyberk` | Team Lead / Tech |

### Danh sách GitHub Organizations (`Cyberk-Ecosystem`)

| GitHub Org | Vai Trò & Mục Đích Sử Dụng | Trang Thái |
|------------|----------------------------|------------|
| **`Cyberk-Official`** | **Organization chính thức** — Quản trị, Vận hành, Board Leaders, Media, Design, QA | 🟢 Active |
| **`cyberk-dev`** | **Monorepo & Technical Projects** — Koto, Relmo, Atlantis, Ghola, Skin Agent, Atlas... | 🟢 Active |
| **`CyberkFi`** | CEO Workspace & Company Core Architecture | 🟢 Active |
| **`Asimov-Syntax`** | Hệ sinh thái Asimov Platform & Specs | 🟢 Active |
| **`Cyberk-vn`** | Lịch sử dự án công ty (Đã lưu trữ / Archived) | 🟡 Archived |
| **`coinseeker-co`** | Dự án Coinseeker & Oracler Master | 🟢 Active |
| **`helilabs2-0`** | Dự án HELIX Platform | 🟢 Active |
| **`Asterix-Cyberk`** | Dự án Asterix | 🟢 Active |
| **`pay-crypt`**, **`Amaterasu-DN404`**, **`cyberk-lab`**, **`Liberian-Book`** | Sub-orgs / Special research labs | ⚪ Standby |

4. **Ví dụ mẫu `plan.csv` chuẩn hóa:**

   ```csv
   title,assignees,status,labels,milestone,week,type,priority,start_date,target_date,estimate,body
   "[IP-037] Họp Kick-off Leaders",anderson-cyberk,Backlog,operations,IP-037,33,Task,High,2026-08-11,2026-08-11,1,"## Mục tiêu\nAlign toàn bộ leaders về IP-037."
   "[IP-037] Gửi thông báo Telegram W33-W36",anna-cyberk,Backlog,operations,IP-037,33,Task,High,2026-08-11,2026-09-01,2,"## Mục tiêu\nGửi thông báo Telegram mỗi thứ 2 hàng tuần."
   ```

---

### Bước 3 — Cập nhật Scheduler & Kanban Board

1. Cập nhật **Status** trong file IP (`IP-[XXX]-doing.md`) → `doing`.
2. Cập nhật **Kanban Board** (`improvement/kanban-board.md`) → chuyển IP sang cột **Doing**.
3. Bổ sung các mốc assign/follow/review vào `scheduler.csv`.

---

> [!NOTE]
> **ĐẾN ĐÂY LÀ HOÀN THÀNH QUY TRÌNH IP PLANNING.**
> File `plans/IP-[XXX]/plan.csv` đã sẵn sàng để chuyển giao hoặc import/push lên các hệ thống quản lý công việc (như GitHub Projects, Lark Base, v.v.) ở các bước sau.
