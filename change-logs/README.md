# Change Logs — CyberkFi

**Folder:** `changes/change-logs/`

---

## 🎯 Mục đích

Lưu trữ nhật ký thay đổi và bài học rút ra từ các Improvement Plans (IPs).

**Thay thế cho:** `diary/` (cũ)

---

## 📁 Cấu trúc

### 1. Change Log theo IP

**Format:** `IP-[XXX].md`

```markdown
# Change Log — IP-[XXX]

**Tên IP:** [Tên đầy đủ]  
**Ngày bắt đầu:** YYYY-MM-DD  
**Ngày kết thúc:** YYYY-MM-DD  
**Status:** Hoàn thành / Thất bại / Huỷ

---

## 📝 Timeline

### YYYY-MM-DD — Khởi tạo
- [Ghi chú sự kiện]

### YYYY-MM-DD — Cập nhật
- [Ghi chú sự kiện]

### YYYY-MM-DD — Đóng IP
- [Lý do đóng]
- [Bài học rút ra]

---

## 💡 Lessons Learned

### ✅ Làm tốt
- [Điểm 1]
- [Điểm 2]

### ⚠️ Cần cải thiện
- [Điểm 1]
- [Điểm 2]

### 🔑 Bài học chính
- [Bài học 1]
- [Bài học 2]
```

---

## 📋 Khi nào ghi Change Log?

| Sự kiện | Action |
|---------|--------|
| IP khởi tạo | Tạo file `IP-[XXX].md` |
| Có thay đổi lớn | Cập nhật timeline |
| Gặp blocker | Ghi nhận + cách xử lý |
| IP đóng | Viết Lessons Learned |

---

## 🔗 Liên kết

- **IP files:** `improvement/IP-[XXX]-doing.md`
- **Archive:** `improvement/archive/`
- **Tasks:** `tasks/IP-[XXX]/`

---

## 📝 Ví dụ

Xem `IP-001.md` (sẽ tạo sau khi có IP hoàn thành đầu tiên)

---

**Owner:** TBD  
**Created:** 2026-04-08  
**Replaces:** `diary/`
