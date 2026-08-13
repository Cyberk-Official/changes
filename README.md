---
type: readme
tags: [ceo]
---

# CEO Workspace - CyberkFi

Chào mừng đến với **CEO Workspace** - Trung tâm chỉ huy kỹ thuật số của CyberkFi.

Đây là nơi kết nối trực tiếp giữa CEO và đội ngũ AI Agents, đóng vai trò là **Source of Truth** (Nguồn sự thật duy nhất) cho mọi hoạt động điều hành, chiến lược và cải tiến của công ty.

## 🎯 Mục đích & Vai trò

Không gian làm việc này được thiết kế để phục vụ ba mục đích cốt lõi:

1.  **Hoạch định Chiến lược (Strategy Hub):** Nơi định hình tầm nhìn dài hạn và các mục tiêu then chốt (OKRs).
2.  **Vườn ươm Cải tiến (Innovation Lab):** Nơi cụ thể hóa chiến lược thành các kế hoạch hành động (Improvement Plans - IP).
3.  **Trung tâm Chỉ huy (Command Center):** Nơi điều phối nguồn lực, theo dõi tiến độ và lưu vết hoạt động.

## 🏗️ Cấu trúc Workspace

Workspace được tổ chức tinh gọn để tối ưu hóa sự tập trung:

*   **`strategy/`**: Tầm nhìn dài hạn.
    *   `S-XXX-doing.md`: File Chiến lược định hướng cho 1-3 năm.
    *   `strategies.md`: Index tất cả chiến lược.
*   **`improvement/`**: Trái tim của sự thay đổi.
    *   `kanban-board.md`: Bảng theo dõi trạng thái thực thi.
    *   `IP-XXX-doing.md`: File IP riêng lẻ.
    *   `archived/`: IP đã hoàn thành/thất bại.
*   **`plans/`**: Kế hoạch thực thi chi tiết (Plan Files & CSVs).
    *   `IP-XXX/plan.csv`: Danh sách task chi tiết dạng bảng chứa đầy đủ thông tin chuẩn bị publish.
*   **`skills/`**: Bộ não quy trình (SOPs).
    *   `st-create/`: Quy trình tạo chiến lược dài hạn.
    *   `ip-create/`: Quy trình khởi tạo Improvement Plan (IP).
    *   `ip-planning/`: Quy trình lập kế hoạch IP và xuất file `plans/IP-XXX/plan.csv`.
    *   `ip-publish/`: Quy trình duyệt 1 by 1 và đẩy task lên GitHub Project.
    *   `ip-archive/`: Quy trình đóng IP (Hoàn thành/Thất bại/Huỷ).
*   **`change-logs/`**: Nhật ký thay đổi và lessons learned.

## 🤖 Lực lượng Lao động (The Workforce)

*   **`AGENTS.md`**: **"Hiến pháp"** của Workspace.
    *   Quy định vai trò, trách nhiệm và kỹ năng của AI Agents.
    *   Mô tả chi tiết các quy trình cốt lõi mà Agent phải tuân thủ.

## 🚀 Luồng làm việc (Core Workflow)

1.  **Think Big (Strategy):** CEO & Agent xác định Chiến lược → `skills/st-create/st-create.md`.
2.  **Start Small (IP):** Cụ thể hóa thành IP → `skills/ip-create/ip-create.md`.
3.  **Plan Fast (Planning):** Lập kế hoạch IP & xuất CSV → `skills/ip-planning/ip-planning.md`.
4.  **Publish Tasks (Publishing):** Duyệt từng task 1 by 1 & đẩy lên GitHub → `skills/ip-publish/ip-publish.md`.
5.  **Track & Log (Logging):** Theo dõi tiến độ & lưu vết → `scheduler.csv` + `change-logs/`.

---
*CyberkFi - Where Human Vision meets AI Execution.*
