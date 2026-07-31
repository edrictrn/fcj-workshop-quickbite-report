---
title: "Worklog Tuần 8"
date: 2026-07-20
weight: 8
chapter: false
pre: " <b> 1.8. </b> "
---

### Mục tiêu tuần 8:

* Xây dựng hệ thống nhật ký thao tác (Operation Logs / Audit Trail) để ghi nhận mọi biến động quan trọng.
* Triển khai mô-đun Cấu hình Hệ thống động (System Configuration: Phí giao hàng, Thuế, Giờ mở cửa).
* Xây dựng giao diện Quản lý Cấu hình và Trình xem Logs dành cho Admin.

### Các công việc cần triển khai trong tuần này:
| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --- | --- | --- | --- |
| 2 | - Research mô hình Audit Logging trong ứng dụng Web <br> - **Thiết kế Audit Log Schema:** <br>&emsp; + Định nghĩa Model `OperationLog` lưu thông tin: action, user_id, details, timestamp <br>&emsp; + Xây dựng Helper Utility `log_utils.py` để ghi log tự động | 20/07/2026 | 20/07/2026 | - `backend/log_utils.py` <br> - `backend/models/system.py` |
| 3 | - **Gắn Audit Logger vào các Router:** <br>&emsp; + Tự động ghi log khi có thao tác: Đổi trạng thái đơn hàng, Cập nhật menu, Đổi cấu hình hệ thống <br>&emsp; + Xây dựng API `GET /logs` để truy vấn danh sách log | 21/07/2026 | 21/07/2026 | - `backend/routers/logs.py` |
| 4 | - **Phát triển Dynamic System Settings (`routers/settings.py`):** <br>&emsp; + Xây dựng API đọc/ghi cấu hình hệ thống (phí ship, thuế VAT, giờ đóng/mở cửa) <br>&emsp; + Đảm bảo tính toán đúng phí ship và thuế khi khách hàng tạo đơn mới | 22/07/2026 | 22/07/2026 | - `backend/routers/settings.py` <br> - `backend/settings_utils.py` |
| 5 | - **Tích hợp Frontend UI:** <br>&emsp; + Xây dựng trang `LogsPage.tsx` xem lịch sử thao tác hệ thống <br>&emsp; + Xây dựng trang `SettingsPage.tsx` cho phép Admin điều chỉnh phí ship và cấu hình vận hành | 23/07/2026 | 23/07/2026 | - `frontend/src/pages/admin/LogsPage.tsx` <br> - `frontend/src/pages/admin/SettingsPage.tsx` |
| 6 | - **Kiểm thử Luồng Vận Hành:** <br>&emsp; + Thử thay đổi phí giao hàng trên SettingsPage và kiểm tra đơn hàng mới có áp dụng giá mới hay không <br>&emsp; + Kiểm tra log ghi lại chính xác user và hành động vừa thực hiện | 24/07/2026 | 24/07/2026 | - Mã nguồn QuickBite |


### Kết quả đạt được tuần 8:

* **An Toàn & Vận Hành Hệ Thống:**
  * Hoàn thiện tiện ích `log_utils.py` giúp tự động hóa việc ghi vết mọi hành động quản trị trên hệ thống (Audit Trail).
  * Đảm bảo tính minh bạch và truy vết sự cố hiệu quả khi vận hành thực tế.

* **Phát Triển Dự Án QuickBite:**
  * Xây dựng xong hệ thống Cấu hình Động (`settings_utils.py`), giúp Admin tùy chỉnh phí ship, thuế và trạng thái đóng/mở cửa mà không cần khởi động lại Server.
  * Tích hợp thành công giao diện `LogsPage.tsx` và `SettingsPage.tsx` trên React Frontend.