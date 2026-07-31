---
title: "Worklog Tuần 2"
date: 2026-06-08
weight: 2
chapter: false
pre: " <b> 1.2. </b> "
---

### Mục tiêu tuần 2:

* Tìm hiểu và thực hành các dịch vụ Lưu trữ (Amazon S3) và Cơ sở dữ liệu (Amazon RDS) của AWS.
* Nắm bắt kiến thức cơ bản về Mạng AWS (VPC, Subnets, Security Groups).
* Thiết kế Database Schema cho dự án QuickBite và triển khai công cụ migration với Alembic.
* Hoàn thiện các API cốt lõi cho luồng xử lý đơn hàng (Khách hàng -> Bếp -> Giao hàng).

### Các công việc cần triển khai trong tuần này:
| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --- | --- | --- | --- |
| 2 | - Tìm hiểu Amazon S3: Buckets, Objects, Versioning, Permissions <br> - **Thiết kế DB QuickBite:** <br>&emsp; + Tối ưu sơ đồ ERD cho PostgreSQL/SQLite (Users, Items, Orders, System Config, Audit Logs) <br>&emsp; + Khởi tạo các model ORM với SQLAlchemy | 08/06/2026 | 08/06/2026 | - <https://cloudjourney.awsstudygroup.com/> <br> - Tài liệu SQLAlchemy |
| 3 | - **Thực hành AWS:** <br>&emsp; + Tạo S3 Bucket <br>&emsp; + Tải lên và quản lý file qua giao diện Console và AWS CLI <br> - **QuickBite DB Migration:** <br>&emsp; + Tích hợp Alembic để quản lý các phiên bản migration thay cho script thủ công | 09/06/2026 | 09/06/2026 | - <https://cloudjourney.awsstudygroup.com/> <br> - Tài liệu Alembic |
| 4 | - Tìm hiểu Amazon RDS: Các engine hỗ trợ, triển khai Multi-AZ, Backups <br> - **Logic nghiệp vụ QuickBite (Phần 1):** <br>&emsp; + Xây dựng API cho Khách hàng tạo đơn (Thanh toán COD / Mock Payment) <br>&emsp; + Xây dựng API xem và lọc danh sách thực đơn | 10/06/2026 | 10/06/2026 | - <https://cloudjourney.awsstudygroup.com/> <br> - Tài liệu FastAPI |
| 5 | - Tìm hiểu Amazon VPC cơ bản: Subnets (Public/Private), Route Tables, Security Groups <br> - **Logic nghiệp vụ QuickBite (Phần 2):** <br>&emsp; + Xây dựng API cho bộ phận Bếp (Kitchen) tiếp nhận đơn <br>&emsp; + Xây dựng API cho bộ phận Giao hàng (Delivery) cập nhật trạng thái | 11/06/2026 | 11/06/2026 | - <https://cloudjourney.awsstudygroup.com/> <br> - QuickBite README.md |
| 6 | - **Thực hành AWS:** <br>&emsp; + Khởi tạo Amazon RDS instance (PostgreSQL) <br>&emsp; + Kết nối với RDS thông qua database client ở máy local <br> - **Kiểm thử End-to-End QuickBite:** <br>&emsp; + Triển khai endpoint tra cứu đơn hàng công khai qua `order_code` <br>&emsp; + Kiểm thử toàn bộ luồng tạo và xử lý đơn hàng | 12/06/2026 | 12/06/2026 | - <https://cloudjourney.awsstudygroup.com/> <br> - Mã nguồn QuickBite |


### Kết quả đạt được tuần 2:

* **Nền Tảng Điện Toán Đám Mây AWS:**
  * Hiểu rõ các khái niệm về Amazon S3, tạo và quản lý thành công các S3 Buckets bằng cả AWS Console và CLI.
  * Nắm được kiến trúc của Amazon RDS và triển khai thành công một instance cơ sở dữ liệu PostgreSQL trên AWS.
  * Nắm được kiến thức cơ bản về Amazon VPC, bao gồm cách Security Groups và Subnets kiểm soát quyền truy cập vào cơ sở dữ liệu.

* **Phát Triển Dự Án QuickBite:**
  * Đã tối ưu hóa sơ đồ ERD và định nghĩa các model ORM (SQLAlchemy) cho các thực thể quan trọng (Users, Items, Orders, Config, Logs).
  * Thay thế file script tạo DB thủ công (`init_db_sqlite.py`) bằng **Alembic**, giúp quản lý phiên bản cấu trúc cơ sở dữ liệu một cách chuyên nghiệp.
  * Hoàn thiện API luồng đặt hàng cốt lõi, hỗ trợ tạo đơn hàng với thanh toán giả lập e-wallet (mock payment) và COD.
  * Hoàn thiện API cho quy trình vận hành dựa trên vai trò: `Kitchen` (chuẩn bị món) và `Delivery` (cập nhật trạng thái giao hàng).
  * Triển khai và kiểm thử thành công tính năng tra cứu đơn hàng công khai bằng mã `order_code` duy nhất.