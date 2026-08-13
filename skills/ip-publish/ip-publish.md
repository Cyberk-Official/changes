---
type: workflow
tags: [cyberk-way]
description: Quy trình duyệt và đẩy từng task từ plan.csv lên GitHub Project (IP Publish) — review 1 by 1 và cập nhật trạng thái trong plan.csv.
---

# Quy trình Đẩy Task lên GitHub (IP Publish)

> Workflow này thực hiện việc **duyệt (review)** và **đẩy (publish)** các task từ file `plans/IP-[XXX]/plan.csv` lên GitHub Project.
> **Đặc điểm cốt lõi:** Duyệt từng task một (1 by 1) với CEO/User trước khi khởi tạo issue trên GitHub, sau đó cập nhật trực tiếp trạng thái trong `plan.csv`.
> **Điều kiện tiên quyết:** IP đã hoàn thành giai đoạn planning và có file `plans/IP-[XXX]/plan.csv` (từ `skills/ip-planning/ip-planning.md`).

---

## Hệ thống file & công cụ liên quan

| Nguồn | Vai trò |
|-------|---------|
| `plans/IP-[XXX]/plan.csv` | File chứa danh sách task chờ publish |
| GitHub CLI (`gh`) | Công cụ tương tác tạo issue và add item vào project |
| GitHub Project | https://github.com/orgs/Cyberk-Official/projects/1 (hoặc Project được chỉ định) |

---

## Cấu trúc cột trong plan.csv

Để hỗ trợ truy vết việc publish, `plan.csv` hỗ trợ các cột chuẩn:

```csv
title,assignees,status,labels,milestone,type,priority,start_date,target_date,estimate,body,github_url,publish_status
```

- `publish_status`: `pending` (chưa đẩy), `published` (đã đẩy lên GitHub), `skipped` (bỏ qua).
- `github_url`: Đường dẫn tới GitHub Issue tương ứng sau khi khởi tạo thành công.

---

## Các bước thực hiện

### Bước 1 — Kiểm tra Auth & File Input

1. Xác nhận `gh` CLI đã đăng nhập và đủ quyền:
   ```bash
   gh auth status
   ```
2. Đọc file `plans/IP-[XXX]/plan.csv` và lọc các task có `publish_status != published` (hoặc `status != published`).

---

### Bước 2 — Duyệt từng Task (Review 1 by 1)

Với mỗi dòng task trong `plan.csv`:

1. **Hiển thị thông tin task cho User review:**
   - **Tiêu đề (`title`):** ...
   - **Ưu tiên (`priority`):** ...
   - **Start Date → Target Date:** YYYY-MM-DD → YYYY-MM-DD
   - **Estimate:** X giờ
   - **Nội dung / Checklist (`body`):** ...
2. **Xác nhận với User:** Đợi phản hồi chấp thuận từ User (hoặc sửa đổi chi tiết theo yêu cầu).

---

### Bước 3 — Đẩy Task lên GitHub Project (Publish)

Sau khi User đồng ý đẩy task hiện tại:

1. **Tạo GitHub Issue:**
   ```bash
   gh issue create \
     --repo Cyberk-Official/changes \
     --title "<TITLE>" \
     --body "<BODY>"
   ```
   *Lưu lại URL của issue tạo ra.*

2. **Thêm Issue vào GitHub Project:**
   ```bash
   gh project item-add 1 --owner Cyberk-Official --url "<ISSUE_URL>" --format json
   ```
   *Lấy `item_id` từ kết quả.*

3. **Cập nhật các custom fields (Priority, Start Date, Target Date, Estimate):**
   ```bash
   # Set Start Date
   gh project item-edit --id <ITEM_ID> --project-id PVT_kwDOEs-9rM4Bf_jl --field-id PVTF_lADOEs-9rM4Bf_jlzhaOapY --date "<START_DATE>"

   # Set Target Date
   gh project item-edit --id <ITEM_ID> --project-id PVT_kwDOEs-9rM4Bf_jl --field-id PVTF_lADOEs-9rM4Bf_jlzhaOapc --date "<TARGET_DATE>"

   # Set Estimate
   gh project item-edit --id <ITEM_ID> --project-id PVT_kwDOEs-9rM4Bf_jl --field-id PVTF_lADOEs-9rM4Bf_jlzhaOapU --number <ESTIMATE>
   ```

---

### Bước 4 — Cập nhật Trạng thái vào plan.csv

Ngay sau khi push thành công task đó:

1. Cập nhật dòng tương ứng trong `plans/IP-[XXX]/plan.csv`:
   - `publish_status` ➡️ `published`
   - `github_url` ➡️ `<ISSUE_URL>`
2. Thông báo ngắn cho User biết task vừa được đẩy thành công cùng link Issue.
3. Chuyển sang duyệt task tiếp theo cho tới khi hết file `plan.csv`.

---

## Báo cáo Hoàn thành

Sau khi đã duyệt và đẩy toàn bộ các task:
1. Đảm bảo tất cả các dòng trong `plan.csv` đều ở trạng thái `published`.
2. Báo cáo danh sách các GitHub Issue URL cho User.
