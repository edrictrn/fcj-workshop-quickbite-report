---
title: "Worklog Tuần 3"
date: 2026-06-15
weight: 3
chapter: false
pre: " <b> 1.3. </b> "
---

### Mục tiêu tuần 3:

* Nắm vững kiến thức Containerization cơ bản với Docker và Docker Compose.
* Tìm hiểu Amazon ECR (Elastic Container Registry) và cách EC2 instance pull image đã version từ đó.
* Đóng gói toàn bộ ứng dụng QuickBite (FastAPI + React + PostgreSQL + Mailpit) chạy bằng Docker Compose.
* Thiết lập mô phỏng gửi email local bằng Mailpit cho sự kiện xác nhận đơn hàng và cập nhật trạng thái.

### Các công việc cần triển khai trong tuần này:
| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --- | --- | --- | --- |
| 2 | - Tìm hiểu Docker cơ bản: Images, Containers, Dockerfile, và Docker Compose <br> - **Docker hóa QuickBite:** <br>&emsp; + Viết `Dockerfile` cho FastAPI Backend và React Frontend <br>&emsp; + Thiết lập file `docker-compose.yml` cho môi trường phát triển local | 15/06/2026 | 15/06/2026 | - Tài liệu Docker <br> - QuickBite README.md |
| 3 | - **Mô phỏng Email Local:** <br>&emsp; + Thêm dịch vụ SMTP Mailpit vào `docker-compose.yml` <br>&emsp; + Viết service gửi email trong FastAPI cho sự kiện xác nhận đơn hàng và cập nhật trạng thái | 16/06/2026 | 16/06/2026 | - Tài liệu Mailpit <br> - QuickBite README.md |
| 4 | - Tìm hiểu Amazon ECR (Elastic Container Registry): repository, image tag và scan-on-push <br> - **Thực hành Versioning Image:** <br>&emsp; + Gắn tag phiên bản (semantic version) cho backend image <br>&emsp; + Ghi lại mô hình pull-based: mỗi EC2 xác thực qua IAM rồi tự pull image, thay vì chứa source code | 17/06/2026 | 17/06/2026 | - <https://cloudjourney.awsstudygroup.com/> <br> - Tài liệu AWS ECR |
| 5 | - **Docker Compose Networking:** <br>&emsp; + Cấu hình service discovery nội bộ giữa các container `frontend`, `backend`, `db`, `mailpit` <br>&emsp; + Thêm healthcheck để `backend` chờ `db` sẵn sàng trước khi chạy | 18/06/2026 | 18/06/2026 | - Tài liệu Docker Compose |
| 6 | - **Thực hành AWS & Kiểm thử:** <br>&emsp; + Build và đẩy Docker Image lên Amazon ECR <br>&emsp; + Chạy thử nghiệm toàn bộ hệ thống bằng `docker compose up --build` <br>&emsp; + Kiểm tra email gửi về giao diện Mailpit Web (`http://localhost:8025`) | 19/06/2026 | 19/06/2026 | - Tài liệu AWS CLI / ECR <br> - QuickBite README.md |


### Kết quả đạt được tuần 3:

* **Nền Tảng Điện Toán Đám Mây AWS:**
  * Thành thạo các khái niệm Container, viết thành công `Dockerfile` tối ưu cho cả Backend và Frontend.
  * Khởi tạo thành công repository trên Amazon ECR và đẩy Docker image đã version lên cloud bằng AWS CLI.
  * Hiểu mô hình pull-based sẽ dùng trong production: EC2 instance xác thực qua IAM role rồi tự pull image từ ECR thay vì chạy trực tiếp từ source code.

* **Phát Triển Dự Án QuickBite:**
  * Thiết lập hoàn chỉnh môi trường local đa dịch vụ bằng **Docker Compose** (`React` -> `FastAPI` -> `PostgreSQL` -> `Mailpit`).
  * Tích hợp thành công Mailpit để mô phỏng và kiểm thử tính năng gửi email tự động khi đơn hàng tạo mới hoặc thay đổi trạng thái.
  * Thêm healthcheck cho Docker Compose để backend chỉ nhận traffic sau khi database đã sẵn sàng.
