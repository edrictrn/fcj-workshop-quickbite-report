---
title: "Worklog Tuần 1"
date: 2026-06-01
weight: 1
chapter: false
pre: " <b> 1.1. </b> "
---

### Mục tiêu tuần 1:

* Kết nối, làm quen với các thành viên trong First Cloud AI Journey (FCAJ).
* Hiểu dịch vụ AWS cơ bản, cách dùng AWS Management Console & AWS CLI.
* Thiết lập môi trường phát triển cục bộ, tái cấu trúc kiến trúc cốt lõi của dự án QuickBite, đồng thời triển khai luồng Xác thực JWT & Phân quyền dựa trên vai trò (RBAC).

### Các công việc cần triển khai trong tuần này:
| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --- | --- | --- | --- |
| 2 | - Làm quen với các thành viên FCAJ <br> - Đọc và lưu ý các nội quy, quy định tại đơn vị thực tập <br> - Rà soát cấu trúc thư mục QuickBite và xác định phạm vi dự án | 01/06/2026 | 01/06/2026 | Nội quy nội bộ <br> QuickBite README.md |
| 3 | - Tìm hiểu AWS và các loại dịch vụ <br>&emsp; + Compute <br>&emsp; + Storage <br>&emsp; + Networking <br>&emsp; + Database <br>&emsp; + ... <br> - **Tái cấu trúc Backend Core:** <br>&emsp; + Tổ chức lại thư mục `backend/` theo Kiến trúc phân tầng <br>&emsp; + Triển khai Pydantic `BaseSettings` để quản lý biến môi trường `.env` | 02/06/2026 | 02/06/2026 | <https://cloudjourney.awsstudygroup.com/> <br> Tài liệu FastAPI / Pydantic |
| 4 | - Tạo AWS Free Tier account <br> - Tìm hiểu AWS Console & AWS CLI <br> - **Thực hành AWS:** <br>&emsp; + Tạo AWS account <br>&emsp; + Cài AWS CLI & cấu hình <br>&emsp; + Cách sử dụng AWS CLI <br> - **Xác thực & Phân quyền:** <br>&emsp; + Tái cấu trúc luồng xác thực JWT <br>&emsp; + Triển khai dependency phân quyền RBAC cho 4 vai trò (`Admin`, `Customer`, `Kitchen`, `Delivery`) | 03/06/2026 | 03/06/2026 | <https://cloudjourney.awsstudygroup.com/> <br> Thư viện `python-jose` / `passlib` |
| 5 | - Tìm hiểu EC2 cơ bản: <br>&emsp; + Instance types <br>&emsp; + AMI <br>&emsp; + EBS <br>&emsp; + ... <br> - Các cách remote SSH vào EC2 <br> - Tìm hiểu Elastic IP <br> - **Tích hợp Frontend:** <br>&emsp; + Cấu hình URL API cơ sở trong file `.env.local` của React Vite <br>&emsp; + Tích hợp dịch vụ xác thực Axios cho Đăng nhập/Đăng ký | 04/06/2026 | 05/06/2026 | <https://cloudjourney.awsstudygroup.com/> <br> Tài liệu React / Vite |
| 6 | - **Thực hành AWS:** <br>&emsp; + Tạo EC2 instance <br>&emsp; + Kết nối SSH <br>&emsp; + Gắn EBS volume <br> - **Kiểm thử & Xác minh:** <br>&emsp; + Kiểm tra các endpoint trên tài liệu OpenAPI `/docs` <br>&emsp; + Kiểm thử bảo mật tuyến đường RBAC (trả về lỗi 403 Forbidden đối với vai trò không có quyền) | 05/06/2026 | 05/06/2026 | <https://cloudjourney.awsstudygroup.com/> <br> Giao diện FastAPI Swagger UI |


### Kết quả đạt được tuần 1:

* Hiểu AWS là gì và nắm được các nhóm dịch vụ cơ bản:
  * Compute
  * Storage
  * Networking
  * Database
  * ...

* Đã tạo và cấu hình AWS Free Tier account thành công.

* Làm quen với AWS Management Console và biết cách tìm, truy cập, sử dụng dịch vụ từ giao diện web.

* Cài đặt và cấu hình AWS CLI trên máy tính bao gồm:
  * Access Key
  * Secret Key
  * Region mặc định
  * ...

* Sử dụng AWS CLI để thực hiện các thao tác cơ bản như:
  * Kiểm tra thông tin tài khoản & cấu hình
  * Lấy danh sách region
  * Xem dịch vụ EC2
  * Tạo và quản lý key pair
  * Kiểm tra thông tin dịch vụ đang chạy
  * ...

* Có khả năng kết nối giữa giao diện web và CLI để quản lý tài nguyên AWS song song.

* Đã dọn dẹp và chuẩn hóa lại cấu trúc mã nguồn `backend/` theo Kiến trúc phân tầng mô-đun (`core/`, `models/`, `schemas/`, `routers/`, `services/`).

* Cấu hình quản lý biến môi trường an toàn và chuẩn hóa bằng Pydantic `BaseSettings` (`config.py`).

* Hoàn thành và xác minh luồng Xác thực JWT kết hợp Phân quyền RBAC, hỗ trợ đầy đủ 4 vai trò hệ thống (`Admin`, `Customer`, `Kitchen`, `Delivery`).

* Tích hợp thành công giao diện React (Vite) Frontend với các API FastAPI Backend, đảm bảo duy trì trạng thái đăng nhập và bảo vệ các tuyến đường riêng tư.  