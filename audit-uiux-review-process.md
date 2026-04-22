# Quy trình review UI/UX trên Figma (CRM Mobile cho RM Retail — QHKH Cá nhân)

## 1) Chuẩn bị (15–30 phút)
- **Chốt bối cảnh**:
  - Nền tảng: **Mobile app (iOS/Android)**
  - Mục tiêu review: **Flow + UI + UX** (không review backend/logic nghiệp vụ ngoài phạm vi UI)
  - Đối tượng: **RM Retail / QHKH Cá nhân**
  - Điều kiện thực tế: **di chuyển nhiều**, có thể **mất mạng**, thao tác nhanh khi đứng/đi, một tay (thumb zone)
- **Chốt scope**:
  - Chọn **1 flow** hoặc **1 section** để audit sâu (tránh đọc cả file Figma).
  - Xác định các màn trong flow: list → detail → action/create/edit → confirm/result → error/offline (nếu có).
- **Chọn màn hình đại diện (3–7 màn/flow)**:
  - Ví dụ: Danh sách KH/Lead → Chi tiết → Thêm hoạt động/Note → Lưu thành công/thất bại → Trạng thái offline & đồng bộ.
- **Chọn người review**: 1 UX + 1 PO/BA + 1 RM SME (RM Retail/Branch SME) (nếu có) để bắt lỗi nghiệp vụ & thuật ngữ.

## 2) Vòng 1 — Review theo P0 (Must) để “không kẹt flow”
Mục tiêu: bắt các lỗi **Blocker/High**, đặc biệt thiếu states, form validation, điều hướng, tuân thủ.

- Với mỗi màn hình/frame:
  - Chạy checklist P0 trong [`audit-uiux-checklist.md`](./audit-uiux-checklist.md)
  - Ghi issue theo template issue log của dự án (hoặc tạo bảng log theo các cột: Flow/Screen/Criteria/P-Level/Severity/Score/Summary/Evidence/Figma link/Owner/Status).
  - **Link Figma**: dán link node/frame; nếu có nhiều node liên quan, link node chính + ghi thêm trong Notes.
- **Quy tắc kết luận**: nếu có ≥1 issue P0 mức S0/S1 → màn hình/flow **Fail** (cần sửa trước khi review tiếp).

## 3) Vòng 2 — Review consistency + P1/P2 (tối ưu tốc độ & độ rõ)
Mục tiêu: tối ưu “scan-ability”, hiệu suất thao tác **trên mobile**, tính nhất quán component/copy.

- Review theo cụm:
  - **Copy & thuật ngữ**: tên đối tượng, KPI definition, label CTA
  - **Visual consistency**: grid/type/spacing, component states
  - **Edge cases**: empty/no results/loading/error/permission
- Đảm bảo không có “regression” tạo ra P0 mới sau khi chỉnh UI.

## 4) Triage & ưu tiên sửa (để chạy sprint hiệu quả)
- **P0 + S0/S1**: sửa ngay (không pass review).
- **P0 + S2**: gom thành 1–2 PR/iteration (tuỳ nguồn lực).
- **P1**: ưu tiên theo tần suất dùng (RM Retail dùng mỗi ngày) và tác động KPI (time saved, error reduced).
- **P2**: chỉ làm nếu không ảnh hưởng timeline.

## 5) Definition of Done (DoD) cho “ready to implement”
- Không còn issue **P0 S0/S1**.
- Có đủ state: **loading/error/empty/no results/permission** cho các màn hình có data/network.
- Các hành động rủi ro có **confirm + wording rõ hậu quả**.
- KPI có **scope thời gian + định nghĩa + drill-down** (nếu scope sản phẩm).

