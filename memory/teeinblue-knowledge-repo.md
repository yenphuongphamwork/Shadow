---
name: teeinblue-knowledge-repo
description: Domain knowledge base repo for Teeinblue — consult it for any task touching Teeinblue product/customers/market/features/history/support
metadata: 
  node_type: memory
  type: reference
  originSessionId: 12a24032-5a00-438d-86c3-d8ba57dc88a0
  modified: 2026-09-14T09:46:24.310Z
---

Repo: https://github.com/ownego/teeinblue-knowledge, cloned locally at `~/github/teeinblue-knowledge` (see [[github-repo-convention]]).

Đây là knowledge base chung của team Teeinblue, dùng để AI agent đọc hiểu context trước khi làm việc liên quan đến Teeinblue.

**Cấu trúc:**
- `knowledge/01-product.md` — sản phẩm
- `knowledge/02-customers.md` — khách hàng
- `knowledge/03-market-pod.md` — thị trường POD
- `knowledge/04-features-setup.md` — bản đồ feature & setup (từ help center public)
- `knowledge/05-history.md` — lịch sử & quyết định lớn (timeline, thắng/thua)
- `knowledge/06-support-internal.md` — bản đồ Internal Support Doc (vận hành, debug, chính sách data) — nội bộ
- `knowledge/07-terms.md` — thuật ngữ
- `cases/` — case do team đóng góp: vấn đề → bối cảnh → cách giải → kết quả

Ký hiệu: ✅ public · 🟪 nội bộ · ❓ giả thuyết chờ xác nhận.

**Khi nào cần đọc/dùng repo này:** bất kỳ task nào cần domain knowledge về Teeinblue — trả lời câu hỏi về sản phẩm/feature, phân tích khách hàng, viết report thị trường POD, debug support issue, hoặc bất cứ khi nào cần hiểu bối cảnh/lịch sử quyết định của Teeinblue trước khi làm. Đọc theo thứ tự 01→06 rồi tìm case tương tự trong `cases/`.

**Quy tắc đóng góp (nếu sửa/PR vào repo):** không commit thẳng vào main, phải qua PR + PO (Trang) approve. Không đưa số liệu doanh thu/tiền, tên cá nhân người liên hệ phía khách (dùng vai trò thay tên), tên store bị tố vi phạm, nhận xét cá nhân về thành viên nội bộ, credentials, thông tin cá nhân của buyer, hay quyết định/đánh giá nội bộ của PO.

Liên quan: [[teeinblue-personalization-report-project]], [[teeinblue-scorecard-infographic]], [[tib-shopify-theme-reference]].
