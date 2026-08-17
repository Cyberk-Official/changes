---
type: improvement-plan
tags: [cyberk-way, marketing, self-media, new-media, culture, hr]
status: todo
priority: high
created: 2026-08-14
---

#### Cải tiến 38 (IP-038): Member Content Adoption — Chiến tranh Nhân dân trong Sản xuất Nội dung

* **Mục tiêu:** Thúc đẩy tối thiểu 50% member Cyberk bắt đầu sản xuất nội dung (dưới các hình thức: screencast, blog kỹ thuật, short video, voice-over...), biến mọi thành viên thành content contributor với sự đồng hành và hỗ trợ từ Team Media.
* **Lý do (Tại sao):** 
  * Tách ra từ [IP-034](./archived/IP-034-done.md) sau khi Team Media nòng cốt đã vận hành ổn định và đạt sản lượng chuẩn.
  * Hiện thực hóa chiến lược "Chiến tranh Nhân dân" (People's Content War): không dồn toàn bộ trách nhiệm lên team media mà phân tán lực lượng sang toàn bộ thành viên. Câu chuyện thực chiến từ chính các kỹ sư, QA, designer mang lại tính chân thực và xây dựng niềm tin vững chắc nhất.
  * Gắn kết với cơ chế Responsibility-Based Equity (RBE - [IP-035](./IP-035-doing.md) & [equity-strategy.md](./equity-strategy.md)) để tạo động lực và giá trị dài hạn cho member tham gia.

* **Key Results (Kết quả cần đạt):**
  * *KR1 (Member Content Adoption - KR Cốt lõi):* Tối thiểu 50% member công ty bắt đầu sản xuất nội dung (screencast, blog, video ngắn, voice-over...) trong vòng 8 tuần.
  * *KR2 (Media Enablement & Toolkit):* Team Media hoàn thiện bộ công cụ hỗ trợ member non-media trong 2 tuần:
    * Template kịch bản, cấu trúc chia sẻ chuẩn Cyberk.
    * Preset công cụ ghi hình chạy ngầm (OBS/Loom hotkey) và quy trình làm sạch dữ liệu nhạy cảm.
    * Quy trình nhận file thô (raw material) và hậu kỳ nhanh (edit, visual polish, caption).
  * *KR3 (Production Cadence):* Thiết lập và duy trì nhịp độ sản xuất ổn định: mỗi member tham gia đóng góp tối thiểu 1 nội dung / 2 tuần.
  * *KR4 (Equity & Recognition Alignment):* Đồng bộ hóa cơ chế ghi nhận đóng góp nội dung vào 20% Content Strategy Pool thuộc hệ thống RBE ([IP-035](./IP-035-doing.md)).

* **Open Questions (Câu hỏi mở & Thảo luận):**
  * *Câu hỏi 1 (Cách thu thập source thụ động):* Làm thế nào để Devs tự giác lưu lại source code/quay lỗi terminal mà không quên hoặc ảnh hưởng năng suất? -> *Thảo luận:* Trang bị công cụ record chạy ngầm gọn nhẹ (Loom/OBS hotkey), và quy định quy trình lọc bỏ thông tin nhạy cảm (.env, API key) trước khi lưu kho chung.
  * *Câu hỏi 2 (Năng lực member non-media):* Làm thế nào để member non-media (developer, QA, BD...) sản xuất nội dung chất lượng khi họ không có kỹ năng quay/dựng? -> *Thảo luận:* Team media cung cấp template, hướng dẫn step-by-step, và hỗ trợ hậu kỳ. Member chỉ cần cung cấp nguyên liệu thô (quay màn hình, kể chuyện, chia sẻ kinh nghiệm).
  * *Câu hỏi 3 (Động lực & Tránh hình thức):* Làm sao để việc làm content không trở thành gánh nặng hay đối phó? -> *Thảo luận:* Vận hành theo mô hình tự nguyện (opt-in) gắn với quyền lợi Equity RBE (IP-035), tôn trọng format thế mạnh của từng cá nhân (viết, code screencast, audio/voice-over).

* **Risks (Rủi ro & Biện pháp):**
  * *Rủi ro 1:* **Member phản kháng hoặc e ngại khi phải làm content** -- Không phải ai cũng muốn hoặc thoải mái xuất hiện trước camera. -> *Mitigation:* Kết hợp cơ chế equity (IP-035) để tạo skin in the game. Đa dạng hóa hình thức (screencast, voice-over, bài viết kỹ thuật) thay vì bắt buộc xuất hiện trực diện trước ống kính.
  * *Rủi ro 2:* **Nút cổ chai từ Tech Lead / Founder** -- Founder và Tech Lead quá bận rộn để duyệt nội dung kỹ thuật hoặc cung cấp nguyên liệu. -> *Mitigation:* Phân quyền kiểm duyệt nội dung kỹ thuật cho Tech Lead từng dự án; Media team chịu trách nhiệm visual và policy.
  * *Rủi ro 3:* **Rò rỉ dữ liệu hoặc mã nguồn nhạy cảm (Security Leak)** -- Member vô tình quay lộ API key, file .env, dữ liệu bí mật của khách hàng. -> *Mitigation:* Ban hành Security Sanitization Checklist; bắt buộc lọc dữ liệu trước khi gửi sang Media Team duyệt xuất bản.

* **Status:** `Chưa bắt đầu`
* **Liên kết:**
  * **IP Tiền thân:** [IP-034](./archived/IP-034-done.md) (Xây dựng Bộ phận Sản xuất Nội dung)
  * **Chiến lược liên quan:** [S-005](../strategy/S-005-doing/S-005-doing.md) (Self-Media), [IP-035](./IP-035-doing.md) (Hệ thống Equity RBE)
* **Thực tế (Ghi chú/Dấu vết):**
  * 2026-08-14: Tách từ IP-034 theo chỉ đạo của CEO: Team media nòng cốt đã vận hành thành công, tách riêng KR Member Content Adoption ("Chiến tranh Nhân dân") sang IP-038 để tập trung kích hoạt toàn thể member.
