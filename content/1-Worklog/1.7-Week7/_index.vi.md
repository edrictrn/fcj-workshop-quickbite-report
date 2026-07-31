---
title: "Worklog Tuần 7"
date: 2026-07-13
weight: 7
chapter: false
pre: " <b> 1.7. </b> "
---

### Mục tiêu tuần 7:

* Thiết kế và khởi tạo các SQL Views trên PostgreSQL/SQLite phục vụ báo cáo kinh doanh.
* Xây dựng các API truy xuất chỉ số thống kê (Doanh thu, Đơn hàng, Top sản phẩm bán chạy).
* Triển khai tính năng xuất báo cáo định dạng CSV (CSV Export) từ Backend.
* Tích hợp trang Dashboard Quản trị (Admin Dashboard) trên giao diện React Frontend.

### Các công việc cần triển khai trong tuần này:
| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --- | --- | --- | --- |
| 2 | - Research giải pháp tối ưu truy vấn báo cáo bằng SQL Views <br> - **Tạo SQL Views:** <br>&emsp; + Viết script SQL tạo Views thống kê doanh thu theo ngày/tháng (`views_postgres.sql`) <br>&emsp; + Viết Views tổng hợp top món ăn bán chạy và trạng thái đơn hàng | 13/07/2026 | 13/07/2026 | - `backend/sql/views_postgres.sql` <br> - QuickBite README.md |
| 3 | - **Phát triển Reporting Router (`routers/reports.py`):** <br>&emsp; + Xây dựng endpoint `GET /reports/dashboard` lấy metrics tổng quan <br>&emsp; + Xây dựng các endpoint thống kê chi tiết cho Admin | 14/07/2026 | 14/07/2026 | - `backend/routers/reports.py` <br> - Tài liệu FastAPI |
| 4 | - **Triển khai CSV Export Service:** <br>&emsp; + Xây dựng endpoint `GET /reports/export/orders` xuất danh sách đơn hàng dạng CSV <br>&emsp; + Xây dựng endpoint `GET /reports/export/revenue` xuất báo cáo doanh thu | 15/07/2026 | 15/07/2026 | - `backend/routers/reports.py` |
| 5 | - **Tích hợp Admin Dashboard (Frontend):** <br>&emsp; + Kết nối các thẻ chỉ số (Metric Cards) trên React với API Reports <br>&emsp; + Thêm nút bấm Download CSV cho Admin trên giao diện | 16/07/2026 | 16/07/2026 | - `frontend/src/pages/admin/ReportPage.tsx` <br> - `frontend/src/components/MetricCard.tsx` |
| 6 | - **Kiểm thử & Xác minh Data:** <br>&emsp; + Seed dữ liệu mẫu (`seed_postgres.sql`) và kiểm tra độ chính xác của các chỉ số báo cáo <br>&emsp; + Kiểm tra định dạng file CSV xuất ra trên Excel/Google Sheets | 17/07/2026 | 17/07/2026 | - `backend/sql/seed_postgres.sql` |


### Kết quả đạt được tuần 7:

* **Nền Tảng Cơ Sở Dữ Liệu:**
  * Đã định nghĩa và thực thi thành công các SQL Views trên Amazon RDS PostgreSQL giúp tối ưu hóa hiệu năng truy vấn báo cáo.
  * Đồng bộ hóa cấu trúc Views giữa SQLite local và PostgreSQL cloud.

* **Phát Triển Dự Án QuickBite:**
  * Hoàn thiện Router Báo cáo (`routers/reports.py`) hỗ trợ lấy dữ liệu Dashboard và tải file báo cáo CSV.
  * Tích hợp thành công giao diện Admin Dashboard và trang Báo cáo (`ReportPage.tsx`) trên React Frontend, cho phép quản trị viên theo dõi doanh thu và xuất báo cáo công việc nhanh chóng.