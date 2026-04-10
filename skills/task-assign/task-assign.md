---
type: workflow
tags: [cyberk-way, telegram, automation]
description: Trợ lý gửi tài liệu, thông tin qua Telegram. Không giao việc, chỉ chuyển tài liệu đến đúng người.
version: 1.2
owner: TBD
last-reviewed: 2026-04-08
---

# Workflow: Trợ lý Gửi Tài liệu

> **Vai trò:** Trợ lý của team, **KHÔNG PHẢI** người giao việc.
> 
> **Nhiệm vụ:** Gửi tài liệu, thông tin, hướng dẫn đến đúng người cần nhận.

> [!IMPORTANT]
> **Tư duy đúng:**
> - ❌ "Giao việc cho DEV team"
> - ✅ "Gửi tài liệu cho DEV team"
> 
> NEO mang thông tin đến, không ra lệnh.

---

## Khi nào workflow thành công

- [ ] Tài liệu được gửi đúng người cần nhận
- [ ] Message format rõ ràng, dễ đọc
- [ ] GitHub links click được, tài liệu tham chiếu đầy đủ
- [ ] Buttons reply giúp team phản hồi nhanh (✅ Xong, 🔄 Đang làm, 🚫 Blocked, ❓ Hỏi)

---

## Hệ thống file liên quan

| File / Folder | Vai trò |
|---------------|---------|
| `changes/tasks/IP-[XXX]/` | Folder chứa task files |
| `changes/tasks/IP-[XXX]-[DEPT].md` | File task chi tiết (tài liệu cần gửi) |
| `tools/telegram-notify/src/channels.json` | Config channel Telegram |
| `NEO/.env` | Telegram bot token |
| `scheduler.csv` | Lịch gửi tài liệu |
| `skills/task-assign/scripts/` | Scripts send.ts, follow.ts |

---

## 1. Gửi tài liệu (send)

> **Trước đây gọi là:** `assign.ts` (giao việc)  
> **Bây giờ:** Vẫn dùng script đó, nhưng **tư duy** là "gửi tài liệu"

### Khi nào dùng

| Tình huống | Command |
|------------|---------|
| Gửi tài liệu task cho department | `bun run assign.ts IP-027-DES DES` |
| Xem trước không gửi | `bun run assign.ts IP-027-DEV DEV --dry-run` |

### Command

```bash
cd /Users/anderson/Desktop/works/changes/skills/task-assign/scripts
bun run assign.ts <TASK_ID> <CHANNEL> [--dry-run]
```

### Ví dụ

```bash
# Gửi tài liệu cho Design team
bun run assign.ts IP-027-DES DES

# Gửi tài liệu cho Dev team (xem trước)
bun run assign.ts IP-023-DEV DEV --dry-run
```

### Script tự động xử lý

1. ✅ Tìm file task từ ID (`tasks/IP-[XXX]/[TASK_ID].md`)
2. ✅ Bỏ frontmatter (tags, metadata)
3. ✅ Format MD → Telegram:
   - `# H1` → 📌 **Bold**
   - `## H2` → ▸ **Bold**
   - `- [ ]` → ☐
   - `- [x]` → ☑
   - `- ` → •
   - Strip `**`, `*`, backticks
4. ✅ Replace relative links → GitHub URLs (click được)
5. ✅ Gửi 1 message + inline buttons

> **Không cần AI soạn tin nhắn** — script format sẵn từ file MD.

### Ngôn từ nên dùng

| ❌ Tránh | ✅ Nên dùng |
|----------|-------------|
| "Giao việc" | "Gửi tài liệu" |
| "Assign task" | "Chuyển thông tin" |
| "Bảo làm" | "Hỗ trợ" |
| "Yêu cầu hoàn thành" | "Mong nhận kết quả" |

---

## 2. Hỗ trợ theo dõi (follow)

> **Tư duy:** NEO hỏi thăm tiến độ để **hỗ trợ**, không phải để **giám sát**

### Khi nào dùng

| Tình huống | Command |
|------------|---------|
| Hỏi thăm 1 task cụ thể | `bun run follow.ts IP-027-QA QA` |
| Hỏi thăm TẤT CẢ task của 1 IP | `bun run follow.ts IP-027` |
| Mid-point check (giữa chừng) | `bun run follow.ts IP-027` |
| Thu kết quả deadline | `bun run follow.ts IP-027` |
| Xem trước không gửi | `bun run follow.ts IP-027 --dry-run` |

### Command

```bash
cd /Users/anderson/Desktop/works/changes/skills/task-assign/scripts
bun run follow.ts <TASK_ID|IP_ID> [CHANNEL] [--dry-run]
```

### Ví dụ

```bash
# Hỏi thăm 1 task cụ thể → gửi vào channel chỉ định
bun run follow.ts IP-027-QA QA

# Hỏi thăm TẤT CẢ task của IP-027 → tự gửi đúng channel mỗi department
bun run follow.ts IP-027

# Xem trước không gửi
bun run follow.ts IP-027 --dry-run
```

### Script tự động xử lý

1. ✅ Tìm tất cả task files của IP (hoặc 1 task cụ thể)
2. ✅ Đọc frontmatter: `assignee`, `status`, `department`
3. ✅ Đếm checklist progress (`done/total`)
4. ✅ Soạn tin nhắn hỏi thăm thân thiện, kèm status + progress
5. ✅ Gửi vào đúng channel theo department (hoặc channel override)
6. ✅ Kèm inline buttons (✅ Xong, 🔄 Đang làm, 🚫 Blocked, ❓ Hỏi)

### Ngôn từ nên dùng

| ❌ Tránh | ✅ Nên dùng |
|----------|-------------|
| "Kiểm tra tiến độ" | "Hỏi thăm tiến độ" |
| "Follow-up" | "Hỗ trợ" |
| "Deadline đã qua" | "Mong nhận kết quả" |
| "Tại sao chưa xong?" | "Có cần hỗ trợ gì không?" |

---

## Channels

**Config:** `tools/telegram-notify/src/channels.json`

| Key | Group |
|-----|-------|
| `DEV` | Cyberk Dev Lead |
| `DES` | CyberK's Design Team |
| `QA` | Cyberk QA |
| `MKT` | Cyberk Marketing |
| `BD` | Cyberk BD |
| `C-LEVEL` | Cyberk - Cải Tiến |
| `LEADERS` | All leaders (fallback) |
| `SANDBOX` | Testing |

---

## Quy tắc

| # | Quy tắc |
|---|---------|
| 1 | Nội dung = file MD nguyên văn, đã format cho Telegram |
| 2 | Tài liệu tham chiếu = GitHub links inline (click được) |
| 3 | 1 message duy nhất per task |
| 4 | Callback format: `fu:[TASK_ID]:[done|doing|blocked|question]` |
| 5 | Luôn `--dry-run` trước khi gửi thật nếu chưa chắc |
| 6 | **Ngôn từ**: Hỏi thăm, hỗ trợ — không ra lệnh |

---

## Checklist sử dụng

### Gửi tài liệu (send)

```markdown
- [ ] Task file đã tạo (`tasks/IP-[XXX]/[TASK_ID].md`)
- [ ] Frontmatter đầy đủ (department, assignee, status, deadline)
- [ ] Checklist việc rõ ràng
- [ ] Chạy `--dry-run` trước
- [ ] Chạy thật: `bun run assign.ts IP-XXX-XXX XXX`
- [ ] Confirm message gửi thành công
```

### Hỗ trợ theo dõi (follow)

```markdown
- [ ] Xác định cần hỏi thăm 1 task hay toàn bộ IP
- [ ] Chạy `--dry-run` trước
- [ ] Chạy thật: `bun run follow.ts IP-XXX [CHANNEL]`
- [ ] Thu thập callbacks từ Telegram
- [ ] Cập nhật status tasks dựa trên reactions
- [ ] Nếu blocked → hỏi "Có cần hỗ trợ gì không?"
```

### Follow-up (follow)

```markdown
- [ ] Xác định cần follow 1 task hay toàn bộ IP
- [ ] Chạy `--dry-run` trước
- [ ] Chạy thật: `bun run follow.ts IP-XXX [CHANNEL]`
- [ ] Thu thập callbacks từ Telegram
- [ ] Cập nhật status tasks dựa trên reactions
```

---

## Xử lý lỗi

| Lỗi | Nguyên nhân | Cách fix |
|-----|-------------|----------|
| `Channel "XXX" not found` | Channel không có trong `channels.json` | Check key, add nếu thiếu |
| `Task file not found` | File task không tồn tại | Check ID, tạo file task trước |
| `TELEGRAM_BOT_TOKEN not found` | Thiếu token trong `.env` | Check `NEO/.env` |
| Message không gửi được | Bot token sai / chat ID sai | Check permissions, invite bot vào channel |

---

## 🔗 Liên kết với skills khác

| Workflow | Mối quan hệ |
|----------|-------------|
| [`ip-execute`](../ip-execute/ip-execute.md) | Sau khi tạo tasks → NEO gửi tài liệu cho team |
| [`ip-archive`](../ip-archive/ip-archive.md) | Hỏi thăm trong quá trình thực thi → archive khi xong |
| `scheduler.csv` | Lịch gửi tài liệu, hỏi thăm được ghi vào đây |

---

## Tóm tắt: NEO là ai?

| ❌ Không phải | ✅ Là |
|--------------|------|
| Người giao việc | Trợ lý gửi tài liệu |
| Người giám sát | Người hỗ trợ |
| Người kiểm tra | Người hỏi thăm |
| Người ra lệnh | Người kết nối |

> **NEO mang thông tin đến đúng người, vào đúng lúc, với thái độ hỗ trợ.**

---

**Created:** 2026-04-08  
**Replaces:** `changes/neo-task-assign/SKILL.md` (legacy)
