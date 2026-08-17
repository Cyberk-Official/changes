---
type: improvement-plan
tags: [operations, governance, policy, professionalism, cyberk-way]
status: todo
priority: high
created: 2026-08-17
owner: Anderson (CEO)
---

#### Cải tiến 39 (IP-039): Ra Quyết định bằng Văn bản — Written Decision-Making & Policy System

* **Mục tiêu:** Xây dựng hệ thống ra quyết định bằng văn bản chuyên nghiệp tại Cyberk. Mọi quyết định quan trọng, chính sách nội bộ (Policy) đều được ban hành chính thức qua Email, lưu trữ có hệ thống, và nhắc nhở qua Telegram. Biến Cyberk từ "nói miệng, chat Telegram" sang "ra văn bản, có truy vết".

* **Lý do (Tại sao):**
  * Hiện tại nhiều quyết định quan trọng chỉ được truyền đạt qua chat Telegram hoặc nói miệng trong cuộc họp, dẫn đến: không ai nhớ chính xác nội dung, không có bằng chứng pháp lý, nhân viên mới không biết quy định nào đang áp dụng.
  * Công ty đang trong giai đoạn chuyên nghiệp hóa ([IP-037](./IP-037-doing.md) Project-Based Governance, [IP-035](./IP-035-doing.md) Equity System). Hệ thống Policy bằng văn bản là nền tảng bắt buộc.
  * Folder `policy/` đã có 5 Policy soạn sẵn nhưng chưa có quy trình ban hành, phân phối, và tra cứu chính thức.
  * Tạo tiền đề pháp lý vững chắc: khi có tranh chấp lao động, Policy bằng văn bản là bằng chứng được công nhận.

* **Phân cấp truyền thông:**

  | Cấp | Kênh | Mục đích | Tính chất |
  |-----|------|----------|-----------|
  | 1 | **Email** | Ban hành quyết định chính thức | Văn bản gốc, có giá trị pháp lý |
  | 2 | **Telegram (Cyberk Official)** | Thông báo & nhắc nhở | Remind, tóm tắt, link tra cứu |

* **Key Results (Kết quả cần đạt):**

  * *KR1 (Policy Framework):*
    Hoàn thiện bộ khung Policy chuyên nghiệp:
    - Template chuẩn cho Policy (header, nội dung, hiệu lực, chữ ký).
    - Quy trình ban hành: Soạn thảo -> Review -> Phê duyệt -> Ban hành Email -> Remind Telegram.
    - Đánh số và phiên bản cho mỗi Policy.

  * *KR2 (Skill & Automation):*
    Hoàn thiện bộ skill AI để hỗ trợ ra quyết định bằng văn bản:
    - Skill soạn thảo Policy từ yêu cầu CEO.
    - Skill format Email ban hành chính thức.
    - Skill gửi remind qua Telegram (tích hợp NEO bot).

  * *KR3 (Current Policy Completion):*
    Hoàn thành và ban hành chính thức các Policy hiện có trong folder `policy/`:
    - `01-noi-quy-lao-dong` (Nội quy Lao động)
    - `02-quy-che-luong-thuong` (Quy chế Lương thưởng)
    - `03-tuyen-dung-thu-viec-danh-gia` (Tuyển dụng, Thử việc, Đánh giá)
    - `04-nghi-phep-va-wfh` (Nghỉ phép & WFH)
    - `05-chinh-sach-lam-them-gio` (Chính sách Làm thêm giờ)
    - Review nội dung, bổ sung ngày hiệu lực, chữ ký CEO.
    - Gửi Email ban hành chính thức cho toàn bộ nhân viên.

  * *KR4 (Policy Portal):*
    Xây dựng folder Policy có cấu trúc để mọi người dễ dàng tra cứu:
    - Tổ chức folder `policy/` theo danh mục rõ ràng.
    - README tổng hợp danh sách Policy với link trực tiếp.
    - Tích hợp vào Cyberk Librarian để tìm kiếm nhanh.
    - Cân nhắc: publish lên Gitbook hoặc static page để nhân viên tra cứu mọi lúc.

* **Execution Plan (Kế hoạch hành động):**

  | Tuần | Task | Người thực hiện | Mô tả |
  |------|------|-----------------|-------|
  | W34 | Setup Policy Framework | Anderson + Neo | Hoàn thiện template, quy trình ban hành, đánh số |
  | W34-35 | Review & Finalize Policies | Anderson | Rà soát 5 Policy hiện tại, bổ sung ngày hiệu lực |
  | W35 | Build Skill & Automation | Neo | Tạo skill soạn Policy, format Email, remind Telegram |
  | W35-36 | Ban hành chính thức | Anderson | Gửi Email ban hành 5 Policy, remind Telegram |
  | W36 | Policy Portal | Neo | Xây dựng README, cấu trúc folder, tích hợp Librarian |

* **Kick-off Actions (Việc cần làm ngay):**
  - [ ] Xác nhận template chuẩn cho Policy (header, footer, chữ ký).
  - [ ] Rà soát 5 Policy hiện tại trong folder `policy/` — xác nhận nội dung đã đủ chưa.
  - [ ] Xác định email công ty dùng để ban hành (sender, format, CC).
  - [ ] Tạo skill `policy-writer` trong folder `policy/skills/`.
  - [ ] Soạn email ban hành đầu tiên (pilot với Policy 01 - Nội quy Lao động).
  - [ ] Cập nhật NEO bot: thêm template remind Policy qua Telegram.

* **Người thực hiện:**
  | Vai trò | Người | Trách nhiệm |
  |---------|-------|-------------|
  | Phê duyệt | Anderson (CEO) | Review, ký, phê duyệt ban hành |
  | Soạn thảo | Neo (AI) | Soạn Policy, format Email, tạo skill |
  | Phân phối | Anna | Gửi Email chính thức, remind Telegram |
  | Tra cứu | All members | Đọc và tuân thủ Policy |

* **Risks (Rủi ro):**
  * *Rủi ro 1:* **Nhân viên không đọc Email** -> Mitigation: Kết hợp remind Telegram ngắn gọn kèm link. Yêu cầu xác nhận đã đọc (reply email hoặc reaction Telegram).
  * *Rủi ro 2:* **Policy quá nhiều, quá dài, nhân viên ngại đọc** -> Mitigation: Mỗi Policy có bản tóm tắt 5 điểm chính (TL;DR). Đăng remind từng phần nhỏ theo tuần.
  * *Rủi ro 3:* **Không duy trì được thói quen ban hành bằng văn bản** -> Mitigation: Mọi quyết định từ CEO/C-Level phải đi kèm văn bản. NEO bot nhắc nếu có quyết định chưa được văn bản hóa.

* **Dependencies:**
  * Folder `policy/` — đã có 5 Policy soạn sẵn.
  * `policy/skills/` — cần xây dựng skill soạn thảo Policy.
  * NEO Bot — Telegram remind.
  * Email công ty — kênh ban hành chính thức.
  * [IP-037](./IP-037-doing.md) — Governance framework tổng thể.
  * [IP-035](./IP-035-doing.md) — Equity System (Policy liên quan).

* **Status:** `todo`
* **Liên kết:**
  * **Chiến lược liên quan:** [IP-037](./IP-037-doing.md) (Project-Based Governance), [IP-035](./IP-035-doing.md) (Equity System)
  * **Folder Policy:** [policy/](../../policy/)
* **Thực tế (Ghi chú/Dấu vết):**
  * 2026-08-17: Khởi tạo IP-039 theo chỉ đạo CEO. Mục tiêu: chuyên nghiệp hóa quy trình ra quyết định bằng hệ thống Policy văn bản chính thức. Email là kênh ban hành chính, Telegram là kênh nhắc nhở. 5 Policy trong folder `policy/` cần được hoàn thiện và ban hành.

---
