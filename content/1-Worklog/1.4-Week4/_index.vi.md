---
title: "Worklog Tuần 4"
date: 2026-06-22
weight: 4
chapter: false
pre: " <b> 1.4. </b> "
---

### Mục tiêu tuần 4:

* Khởi tạo một Amazon RDS (PostgreSQL) instance ban đầu để xác nhận ứng dụng chạy đúng với database thật trên cloud.
* Cấu hình lưu trữ hình ảnh thực đơn trên Amazon S3, private ngay từ đầu thay vì bucket public.
* Triển khai upload ảnh qua trung gian backend để credentials của object storage không bao giờ lộ ra trình duyệt.
* Chuyển đổi dữ liệu (migration) toàn bộ sơ đồ bảng và dữ liệu mẫu từ local lên Amazon RDS.

### Các công việc cần triển khai trong tuần này:
| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --- | --- | --- | --- |
| 2 | - Tìm hiểu Kiến trúc Cloud Database & Security Groups cho Amazon RDS <br> - **Khởi tạo RDS:** <br>&emsp; + Tạo một Amazon RDS PostgreSQL instance đầu tiên để kiểm tra kết nối <br>&emsp; + Cấu hình VPC Subnet Groups và Inbound Security Rules (chỉ mở TCP 5432 cho tầng app) | 22/06/2026 | 22/06/2026 | - <https://cloudjourney.awsstudygroup.com/> <br> - Tài liệu AWS RDS |
| 3 | - **Chuyển đổi dữ liệu lên Cloud:** <br>&emsp; + Cấu hình kết nối Database trong FastAPI tới Endpoint của Amazon RDS <br>&emsp; + Chạy Alembic migrations để đồng bộ cấu trúc bảng và seed data lên RDS | 23/06/2026 | 23/06/2026 | - Tài liệu Alembic <br> - QuickBite README.md |
| 4 | - Tìm hiểu S3 Block Public Access, bucket policy, và lý do upload trực tiếp từ client làm tăng bề mặt tấn công <br> - **Khởi tạo S3 Storage:** <br>&emsp; + Tạo S3 Bucket private lưu trữ hình ảnh thực đơn, bật Block Public Access <br>&emsp; + Xác nhận không có bucket policy hay ACL nào cấp quyền public read/write | 24/06/2026 | 24/06/2026 | - Tài liệu AWS S3 <br> - QuickBite README.md |
| 5 | - **Upload Ảnh Qua Trung Gian Backend:** <br>&emsp; + Tích hợp SDK `boto3` vào FastAPI Backend <br>&emsp; + Viết endpoint `POST /menu/{id}/image` để backend kiểm tra loại/kích thước rồi tự ghi object vào bucket private bằng quyền IAM của chính nó | 25/06/2026 | 25/06/2026 | - Tài liệu Boto3 <br> - Tài liệu FastAPI |
| 6 | - **Kiểm thử & Xác minh:** <br>&emsp; + Kiểm thử luồng upload ảnh từ React Frontend qua endpoint FastAPI vào bucket private <br>&emsp; + Xác nhận object không thể truy cập qua URL S3 công khai <br>&emsp; + Kiểm tra trạng thái kết nối tới RDS qua Health Check API | 26/06/2026 | 26/06/2026 | - Mã nguồn QuickBite |


### Kết quả đạt được tuần 4:

* **Nền Tảng Điện Toán Đám Mây AWS:**
  * Khởi tạo và cấu hình thành công một Amazon RDS PostgreSQL instance đầu tiên với Security Group giới hạn chặt, làm bước đệm cho RDS Multi-AZ được dựng sau này bằng Terraform.
  * Tạo S3 Bucket private cho hình ảnh thực đơn với Block Public Access, không dùng public ACL hay bucket policy công khai ngay từ đầu.
  * Hiểu vì sao mô hình upload trực tiếp từ client lên S3 (Presigned URL) không phù hợp ở đây, và thay vào đó QuickBite định tuyến upload qua backend để quyền truy cập storage luôn nằm ở phía server.

* **Phát Triển Dự Án QuickBite:**
  * Đồng bộ thành công toàn bộ cấu trúc cơ sở dữ liệu local lên Amazon RDS bằng Alembic.
  * Tích hợp thư viện `boto3` vào FastAPI để backend tự upload ảnh đã kiểm tra hợp lệ vào bucket private.
  * Kết nối trang quản lý thực đơn trên React Frontend với endpoint upload mới; ảnh được trả về qua API thay vì URL S3 công khai.
  * Xác minh tính toàn vẹn và độ tin cậy của dữ liệu chạy trên cả Amazon RDS và Amazon S3.
