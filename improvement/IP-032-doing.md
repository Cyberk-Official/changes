---
type: improvement-plan
tags: [cyberk-way, operations, data, ai-native, service]
status: todo
priority: high
created: 2026-04-08
---

#### Cải tiến 32 (IP-032): Xây dựng Team Data & Data Pipeline Service

* **Mục tiêu:** Dựng năng lực Data Pipeline cho Cyberk — từ phục vụ dự án nội bộ đến bán được dịch vụ ra ngoài. Team gọn 3 người là đủ.
* **Lý do (Tại sao):**
  * Data pipeline đang là điểm yếu. Relmo và SkinAgent đều bị chặn vì thiếu data — Trường đã raise trong họp 07/04.
  * Xu hướng AI-first — hầu hết dự án đều cần data pipeline. Đây vừa là nhu cầu nội bộ vừa là cơ hội kinh doanh mới.
  * CEO yêu cầu: "xây team Data nhanh". Không chờ thêm được.
* **Key Results (Kết quả cần đạt):**
  * *KR1 — Tháng 1 (04–05/2026):* Pipeline chạy được cho **Relmo** và **Visible Brand**. Hoàn thành capability page Data trên website.
  * *KR2 — Tháng 2 (05–06/2026):* Có **3 bài viết** marketing. Giới thiệu dịch vụ tới **toàn bộ khách hàng hiện tại**.
  * *KR3 — Tháng 3 (06–07/2026):* Có **khách hàng đầu tiên** dùng dịch vụ Data Pipeline.
* **Team:**
  * **Huy** — thiết kế kiến trúc pipeline, quy trình, chọn tech stack. Xây quy trình kiểm thử dữ liệu tự động (data validation/testing). Backup kỹ thuật khi cần.
  * **Nguyễn Bá Tú** — vận hành hàng ngày, triển khai & bảo trì pipeline trên các dự án.
  * **Nhi (DES)** — thiết kế capability page Data trên website.
  * **Anderson** — viết bài marketing, cập nhật website, giới thiệu dịch vụ tới khách, chốt deal.
* **Risks (Rủi ro & Biện pháp):**
  * *Tú là người vận hành duy nhất* — nếu bận thì bottleneck ngay. → Document hóa mọi thứ. Huy backup kỹ thuật.
  * *Dự án pilot thay đổi scope* — Relmo hoặc Visible Brand tạm dừng thì mất chỗ thực hành. → Thiết kế pipeline dạng framework tái sử dụng, có thể chuyển sang SkinAgent.
  * *Chưa ai hỏi mua dịch vụ data riêng lẻ* — khách chưa quen concept này. → Gắn data pipeline vào offering Product Build (dự án AI nào cũng kèm). Pitch riêng cho khách đã có nhu cầu sẵn.

* **Plans (Kế hoạch hành động):**
  1. **BST**: Cần kiến trúc data pipeline tái sử dụng được cho nhiều dự án + quy trình kiểm thử dữ liệu tự động. Anh Huy thiết kế, Tú vận hành.
  2. **DEV**: Tú triển khai pipeline cho Relmo và Visible Brand. Vận hành + document hóa đủ để người khác tiếp quản.
  3. **DES**: Thiết kế Figma mockup cho 1 trang capability "Data Pipeline" trên cyberk.io — desktop + mobile. Anderson sẽ gửi content trước.
  4. **CEO**: Viết 3 bài marketing, cập nhật website, giới thiệu dịch vụ tới khách hiện tại, chốt deal đầu tiên.

* **Kế hoạch triển khai:**

  | Task | Bộ phận | Mô tả | Deadline | Phụ thuộc | Trạng thái |
  |------|---------|-------|----------|-----------|------------|
  | IP-032-BST | `BST` | Kiến trúc pipeline + data validation — anh tự chọn hướng | 2026-04-25 | — | `todo` |
  | IP-032-DEV | `DEV` | Triển khai pipeline cho Relmo + Visible Brand, viết runbook | 2026-05-09 | IP-032-BST | `todo` |
  | IP-032-DES | `DES` | Figma mockup 1 trang capability Data — desktop + mobile | 2026-04-25 | — | `todo` |
  | IP-032-CEO | `CEO` | 3 bài viết + cập nhật web + pitch khách + chốt deal | 2026-07-08 | IP-032-DES, IP-032-DEV | `todo` |

* **Status:** `Đang thực hiện`
* **Thực tế (Ghi chú/Dấu vết):**
  * 2026-04-08: Khởi tạo IP từ kết luận MM ngày 07/04. CEO yêu cầu xây team Data nhanh.
  * 2026-04-08: Bổ sung Execution Plan, tạo task files, lập lịch scheduler.
