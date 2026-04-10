---
type: workflow
tags: [cyberk-way]
description: Archive Improvement Plan (IP) — 3 trường hợp: Hoàn thành, Thất bại, hoặc Huỷ. AI hỏi CEO để đúc kết bài học trước khi archive.
version: 1.2
owner: TBD
last-reviewed: 2026-04-08
---

# Quy trình Archive Improvement Plan (IP)

> Workflow này áp dụng cho **3 trường hợp**:
> 1. ✅ **Hoàn thành** — IP đạt mục tiêu, archive bình thường
> 2. ❌ **Thất bại** — IP không đạt, cần phân tích nguyên nhân + bài học
> 3. ❌ **Huỷ** — IP bị cancel, cần lý do rõ ràng

> **QUAN TRỌNG:** AI cần **tương tác với CEO** để thu thập thông tin — không tự ý archive IP khi chưa đủ dữ liệu.

> [!IMPORTANT]
> **KHÔNG** archive IP khi:
> - Còn task đang `doing` hoặc `pending` trong scheduler.csv
> - Chưa hỏi CEO các câu hỏi bắt buộc (tùy trường hợp)
> - Chưa viết Lessons Learned vào file IP

---

## Khi nào workflow thành công

- [ ] AI đã hỏi đầy đủ các câu hỏi **phù hợp với trường hợp** (Hoàn thành/Thất bại/Huỷ)
- [ ] Tất cả tasks trong IP đã được đóng (done/cancelled)
- [ ] **Lessons Learned** đã được viết vào file IP (section riêng)
- [ ] File IP được di chuyển về `improvement/archive/`
- [ ] Kanban board được cập nhật

---

## 3 Trường hợp archive IP

### 1. ✅ Hoàn thành

**Điều kiện:**
- Tất cả KPIs đạt (hoặc >80%)
- Tất cả tasks completed
- CEO confirm "ổn"

**Câu hỏi AI cần hỏi:**
```
1. "Anh đánh giá thế nào về IP này? (1-10)"
2. "3 điều làm TỐT nhất?"
3. "3 điều có thể cải thiện?"
4. "Bài học rút ra cho IP sau?"
```

---

### 2. ❌ Thất bại

**Điều kiện:**
- KPIs không đạt (<50%)
- IP không mang lại kết quả mong đợi
- Cần phân tích nguyên nhân

**Câu hỏi AI cần hỏi (BẮT BUỘC):**
```
1. "Theo anh, tại sao IP này THẤT BẠI?"
2. "Nguyên nhân chính là gì? (khách quan + chủ quan)"
3. "Nếu làm lại, anh sẽ thay đổi điều gì?"
4. "Bài học rút ra để IP sau không lặp lại?"
5. "Có cần tạo IP mới để fix vấn đề này không?"
```

**AI phải đào sâu:**
- Nếu CEO nói chung chung → hỏi "Cụ thể là sao?"
- Nếu CEO đổ lỗi hoàn cảnh → hỏi "Phần mình kiểm soát được thì sao?"
- Nếu CEO không muốn nhắc lại → giải thích "Bài học này quan trọng cho team sau này"

---

### 3. ❌ Huỷ (Cancelled)

**Điều kiện:**
- IP chưa bắt đầu hoặc đang làm thì dừng
- Lý do: thay đổi ưu tiên, không còn phù hợp, resource thiếu...

**Câu hỏi AI cần hỏi (BẮT BUỘC):**
```
1. "Tại sao mình HUỶ IP này?"
2. "Lý do khách quan hay chủ quan?"
3. "IP này có để lại bài học/dở dang gì không?"
4. "Có cần tạo IP mới thay thế không?"
```

**Lý do huỷ thường gặp:**
- Priority thay đổi
- Resource không đủ
- Vấn đề đã được giải quyết bằng cách khác
- Ý tưởng không còn phù hợp

---

## Hệ thống file liên quan

| File / Folder | Vai trò |
|---------------|---------|
| `improvement/IP-[XXX]-doing.md` | File IP cần đóng |
| `improvement/kanban-board.md` | Cập nhật trạng thái → Done/Cancelled |
| `tasks/IP-[XXX]/` | Kiểm tra tất cả tasks đã closed |
| `scheduler.csv` | Đánh dấu tất cả lịch = `done` hoặc `cancelled` |
| `improvement/archive/` | Nơi lưu IP sau khi đóng |
| `change-logs/IP-[XXX].md` | Change log + Lessons Learned của IP |

---

## Điều kiện tiên quyết (Prerequisites)

Trước khi chạy workflow này, đảm bảo:

| Điều kiện | Cách kiểm tra |
|-----------|---------------|
| ✅ Tất cả tasks đã closed | Kiểm tra `tasks/IP-[XXX]/` — tất cả file có `status: done` hoặc `cancelled` |
| ✅ Không còn pending schedule | Mở `scheduler.csv`, search `IP-[XXX]` — không còn `status: pending` |
| ✅ Có số liệu KPIs thực tế | File IP có section "Kết quả thực tế" với số |
| ✅ CEO/Stakeholder đã duyệt kết quả | Có confirm qua Telegram/email |

---

## Các bước thực hiện

### Bước 0 — Xác định trường hợp + Hỏi CEO (Bắt buộc)

> **AI không được bỏ qua bước này.** Phải hỏi trước khi làm bất cứ gì.

1. **Hỏi CEO để xác định trường hợp:**
   ```
   🏁 [ARCHIVE IP-XXX]

   Để archive IP này, anh confirm giúp em:

   1. IP này thuộc trường hợp nào?
      ✅ Hoàn thành  /  ❌ Thất bại  /  ❌ Huỷ

   2. [Tùy trường hợp, AI gửi câu hỏi tương ứng]
   ```

2. **Gửi câu hỏi phù hợp:**

   **Nếu Hoàn thành:**
   ```
   1. Anh đánh giá thế nào về IP này? (1-10)
   2. 3 điều làm TỐT nhất?
   3. 3 điều có thể cải thiện?
   4. Bài học rút ra?
   ```

   **Nếu Thất bại:**
   ```
   1. Theo anh, tại sao IP này THẤT BẠI?
   2. Nguyên nhân chính (khách quan + chủ quan)?
   3. Nếu làm lại, anh sẽ thay đổi điều gì?
   4. Bài học để IP sau không lặp lại?
   5. Có cần tạo IP mới fix vấn đề không?
   ```

   **Nếu Huỷ:**
   ```
   1. Tại sao mình HUỶ IP này?
   2. Lý do khách quan hay chủ quan?
   3. Có bài học/dở dang gì không?
   4. Có cần IP mới thay thế không?
   ```

3. **Đợi CEO trả lời**
   - Nếu thiếu thông tin → hỏi lại
   - Nếu CEO bận → đề xuất "Em draft trước, anh confirm sau"

4. **Khi có đủ thông tin** → chuyển sang Bước 1

---

### Bước 1 — Kiểm tra điều kiện archive (Gate Check)

1. Mở file IP (`improvement/IP-[XXX]-doing.md`).
2. **Validation Checklist trước khi archive:**

   ```markdown
   ## Checklist trước khi archive IP
   - [ ] Tất cả tasks trong `tasks/IP-[XXX]/` đã closed
   - [ ] Không còn `pending` schedule trong scheduler.csv
   - [ ] CEO đã confirm trường hợp (Hoàn thành/Thất bại/Huỷ)
   - [ ] CEO đã trả lời các câu hỏi bắt buộc
   ```

3. Nếu có item chưa tick → **KHÔNG archive**, xử lý trước.

---

### Bước 2 — Viết Lessons Learned vào File IP

> **KHÔNG tạo post-mortem riêng** — Lessons Learned được viết TRỰC TIẾP vào file IP.

1. Mở `improvement/IP-[XXX]-doing.md`

2. Thêm section **Lessons Learned** (dưới section Key Results hoặc cuối file):

   **Format chung:**
   ```markdown
   ## 📚 Lessons Learned

   **Trường hợp:** Hoàn thành / Thất bại / Huỷ
   **Ngày đóng:** YYYY-MM-DD

   ### ✅ Điểm làm tốt
   - [Điểm 1]
   - [Điểm 2]
   - [Điểm 3]

   ### ⚠️ Điểm cần cải thiện
   - [Điểm 1]
   - [Điểm 2]
   - [Điểm 3]

   ### 💡 Bài học rút ra
   - [Bài học 1]
   - [Bài học 2]
   - [Bài học 3]
   ```

   **Nếu IP Thất bại** (thêm):
   ```markdown
   ### ❌ Nguyên nhân thất bại
   - Khách quan: [...]
   - Chủ quan: [...]

   ### 🔍 Nếu làm lại sẽ thay đổi
   - [Thay đổi 1]
   - [Thay đổi 2]
   - [Thay đổi 3]
   ```

   **Nếu IP Huỷ** (thêm):
   ```markdown
   ### ❌ Lý do huỷ
   [Mô tả lý do]

   ### 📝 Ghi chú
   [Có dở dang gì không, có cần IP thay thế không]
   ```

3. **AI draft trước** → Gửi CEO confirm:
   ```
   Em đã draft Lessons Learned trong file IP rồi.
   Anh xem qua confirm giúp em nha! (1 phút thôi)
   ```

4. CEO confirm → Lưu file

---

### Bước 3 — Cập nhật Status IP

1. Mở `improvement/IP-[XXX]-doing.md`
2. Cập nhật **Status** (ở phần đầu file):
   - `Hoàn thành` — nếu case 1
   - `Thất bại` — nếu case 2
   - `Đã huỷ` — nếu case 3
3. Cập nhật **Ngày đóng:** YYYY-MM-DD

---

### Bước 4 — Xử lý Tasks & Scheduler

1. **Kiểm tra tasks:**
   ```bash
   # Kiểm tra tất cả tasks trong folder
   ls tasks/IP-[XXX]/
   ```

2. **Đảm bảo tất cả tasks có status = done hoặc cancelled**
   - Nếu còn task `doing` → hoàn thành hoặc cancel
   - Nếu còn task `todo` chưa làm → đánh dấu `cancelled` + ghi lý do

3. **Cập nhật scheduler.csv:**
   - Mở `scheduler.csv`
   - Tìm tất cả dòng chứa `IP-[XXX]`
   - Đánh dấu `status = done` (nếu hoàn thành) hoặc `status = cancelled` (nếu IP dừng sớm)
   - Dòng `review` → thêm ghi chú kết quả

---

### Bước 5 — Cập nhật Kanban Board

1. Mở `improvement/kanban-board.md`
2. Tìm IP trong cột **Doing**
3. Xóa khỏi **Doing**, thêm vào:
   - Cột **Done** (nếu hoàn thành)
   - Cột **Cancelled** (nếu dừng sớm/thất bại)

   ```markdown
   - [x] **IP-027**: [Tên IP] — Completed YYYY-MM-DD
   ```

---

### Bước 6 — Archive File IP

1. Tạo folder (nếu chưa có): `improvement/archive/`
2. Di chuyển file IP:
   ```bash
   mv improvement/IP-[XXX]-doing.md improvement/archive/
   ```
3. Đổi tên file (optional): `IP-[XXX]-done.md` để dễ phân biệt

---

### Bước 7 — Tạo Change Log (Optional)

> Lessons Learned đã được viết vào file IP ở Bước 2.
> Bước này tạo change log riêng để dễ theo dõi lịch sử.

1. Nếu cần → tạo `change-logs/IP-[XXX].md`
2. Content: Timeline + Lessons Learned (tóm tắt từ file IP)
3. Tag để dễ search: `#process`, `#communication`, `#tooling`, v.v.

---

### Bước 8 — Thông báo Đóng IP

1. AI tự format và gửi (có thể hỏi CEO ai cần nhận):

   **Template message:**
   ```
   🏁 [ĐÓNG IP]

   IP-027: [Tên IP]
   Status: ✅ Hoàn thành / ❌ Thất bại / ❌ Huỷ

   📊 KPIs: X/Y đạt (Z%)
   ⏱️ Thời gian: DD/MM → DD/MM (N ngày)
   📚 Lessons: [3 điểm chính]

   Cảm ơn team! 🙌
   ```

2. Gửi đến channel phù hợp (`C-LEVEL`, `LEADERS`, hoặc channel cụ thể)

---

## Script liên quan (AI tự động hóa)

**Giao việc + Follow-up:** `skills/task-assign/scripts/`

```bash
# Giao task
bun run assign.ts IP-027-DES DES

# Follow-up
bun run follow.ts IP-027
```

**Future:** Script auto-close IP (chưa có)

---

## Xử lý异常情况 (Error Handling)

| Tình huống | Hành động | Escalate |
|------------|-----------|----------|
| Task còn `doing` nhưng assignee nghỉ/bỏ việc | Cancel task, ghi lý do, reassess KPIs | C-level |
| KPIs không đạt → cần phân tích sâu | Viết thêm section "Nguyên nhân thất bại" | Strategy Advisor |
| Stakeholder không confirm kết quả | Reminder qua Telegram, wait 3 days → escalate | CEO |
| IP cần pivot giữa chừng | Đóng IP hiện tại → tạo IP mới với hướng đi mới | CEO + Strategy Advisor |
| Assets/tasks bị thiếu | Liệt kê trong Lessons Learned, rút kinh nghiệm | — |
| CEO không trả lời câu hỏi | Reminder 1 lần, nếu vẫn không → escalate | CEO |

---

## Khi IP cần Pivot (Đổi hướng)

Nếu IP đang chạy nhưng cần đổi hướng hoàn toàn:

1. **Đóng IP hiện tại** theo workflow này (status = `Đã dừng (pivot)`)
2. **Viết Lessons Learned** — ghi rõ lý do pivot
3. **Tạo IP mới** với hướng đi mới (dùng `ip-create.md`)
4. **Link 2 IPs** trong cả 2 file:
   ```markdown
   **IP tiền thân:** [IP-026](../IP-026-doing.md) — pivot do [lý do]
   **IP kế tiếp:** [IP-028](../IP-028-doing.md) — pivot từ IP này
   ```

---

## Checklist tổng (Trước khi finish)

```markdown
## ✅ Checklist đóng IP
- [ ] **Bước 0:** Hỏi CEO — đã có đủ câu trả lời (đúng trường hợp)
- [ ] Bước 1: Gate check — tất cả conditions đạt
- [ ] Bước 2: Lessons Learned draft + CEO confirm
- [ ] Bước 3: File IP cập nhật status
- [ ] Bước 4: Tasks + scheduler đã closed
- [ ] Bước 5: Kanban board cập nhật
- [ ] Bước 6: File IP đã archive
- [ ] Bước 7: Lessons learned lưu (nếu có)
- [ ] Bước 8: Thông báo gửi team
```

---

## 📋 Quick Reference — AI Question Script

**Khi CEO nói:** "Đóng IP-027 đi em"

**AI trả lời:**
```
Dạ được anh! Để đóng IP-027, em cần anh confirm:

1. IP này thuộc trường hợp nào?
   ✅ Hoàn thành  /  ❌ Thất bại  /  ❌ Huỷ

[Tùy câu trả lời, em gửi tiếp các câu hỏi tương ứng]
```

**Nếu Hoàn thành:**
```
1. Anh đánh giá thế nào về IP này? (1-10)
2. 3 điều làm TỐT nhất?
3. 3 điều có thể cải thiện?
4. Bài học rút ra?
```

**Nếu Thất bại:**
```
1. Theo anh, tại sao IP này THẤT BẠI?
2. Nguyên nhân chính (khách quan + chủ quan)?
3. Nếu làm lại, anh sẽ thay đổi điều gì?
4. Bài học để IP sau không lặp lại?
```

**Nếu Huỷ:**
```
1. Tại sao mình HUỶ IP này?
2. Lý do khách quan hay chủ quan?
3. Có bài học/dở dang gì không?
```

**Sau khi có câu trả lời:**
```
Dạ em đã có đủ thông tin! Giờ em sẽ:
1. Viết Lessons Learned vào file IP (2 phút)
2. Update status + archive
3. Update kanban
4. Gửi thông báo team

Anh xem qua Lessons Learned em draft rồi confirm giúp em nha!
```

---

## Ví dụ thực tế

| IP | Tên | Status | Lessons Learned |
|----|-----|--------|-----------------|
| IP-001 | Seminar đầu tiên | ✅ Hoàn thành | Trong file `IP-001-done.md` |
| IP-015 | Marketing campaign Q1 | ❌ Thất bại | Trong file `IP-015-done.md` |
| IP-020 | Tool X internal | ❌ Huỷ | Trong file `IP-020-done.md` |

> *(Sẽ cập nhật link thực tế sau khi có)*

---

> **Next steps:** Sau khi đóng IP → Lessons learned được dùng để review định kỳ hằng tháng.
