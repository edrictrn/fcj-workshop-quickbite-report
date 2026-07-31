---
title: "Worklog Tuần 5"
date: 2026-06-29
weight: 5
chapter: false
pre: " <b> 1.5. </b> "
---

### Mục tiêu tuần 5:

* Học nền tảng Terraform (provider, state, module) và thiết kế cấu trúc Infrastructure as Code cho QuickBite.
* Bootstrap Terraform backend: S3 state bucket có versioning/encryption, DynamoDB lock table và ECR repository.
* Xây dựng main Terraform stack (module network, data, app) để thay thế việc cấu hình AWS thủ công bằng một bản triển khai lặp lại được, chạy trên hai Availability Zone.
* Host React Frontend dạng static site trên Amazon S3, phân phối qua Amazon CloudFront.

### Các công việc cần triển khai trong tuần này:
| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --- | --- | --- | --- |
| 2 | - Tìm hiểu Terraform cơ bản: provider, resource, state và remote backend <br> - **Bootstrap Stack:** <br>&emsp; + Tạo S3 bucket có versioning và mã hóa AES-256 cho Terraform remote state <br>&emsp; + Tạo DynamoDB table tránh hai tiến trình cùng ghi state <br>&emsp; + Tạo ECR repository `quickbite-backend` có scan-on-push | 29/06/2026 | 29/06/2026 | - <https://cloudjourney.awsstudygroup.com/> <br> - Tài liệu Terraform |
| 3 | - **Network Module:** <br>&emsp; + Định nghĩa VPC với hai public subnet, hai private application subnet và hai isolated database subnet trên hai Availability Zone <br>&emsp; + Nối Security Group theo chuỗi: ALB-SG → App-SG:8000 → DB-SG:5432, cùng Internet Gateway và NAT Gateway | 30/06/2026 | 30/06/2026 | - Tài liệu Terraform AWS Provider <br> - QuickBite README.md |
| 4 | - **Data Module:** <br>&emsp; + Khởi tạo RDS PostgreSQL (db.t3.micro) encrypted, Multi-AZ trên các isolated subnet <br>&emsp; + Lưu `DATABASE_URL` và JWT secret trong Secrets Manager thay vì Terraform variables | 01/07/2026 | 01/07/2026 | - Tài liệu AWS RDS <br> - Tài liệu AWS Secrets Manager |
| 5 | - **App Module:** <br>&emsp; + Định nghĩa ALB, Target Group và health check `/health` <br>&emsp; + Định nghĩa Launch Template và Auto Scaling Group (min 2, desired 2, max 4) với target tracking CPU 60% <br>&emsp; + Tạo S3 bucket web và menu-images private cùng hai CloudFront distribution dùng Origin Access Control | 02/07/2026 | 02/07/2026 | - Tài liệu AWS CloudFront <br> - QuickBite README.md |
| 6 | - **Apply & Build Frontend:** <br>&emsp; + Chạy `terraform plan`/`apply` cho main stack và kiểm tra số lượng resource <br>&emsp; + Build React cho production với API base là CloudFront API domain rồi đồng bộ `dist/` lên S3 web bucket <br>&emsp; + Cấu hình SPA fallback (403/404 → `index.html`) | 03/07/2026 | 03/07/2026 | - Mã nguồn QuickBite |


### Kết quả đạt được tuần 5:

* **Nền Tảng Điện Toán Đám Mây AWS:**
  * Bootstrap xong Terraform backend: state bucket encrypted, DynamoDB lock table và ECR repository `quickbite-backend`.
  * Xây dựng network module (VPC, hai public/hai private/hai isolated subnet, IGW, NAT Gateway và Security Group chaining) và data module (RDS Multi-AZ và Secrets Manager).
  * Xây dựng app module: ALB với target group health check `/health`, Launch Template và Auto Scaling Group (min 2, desired 2, max 4, target tracking CPU 60%), S3 bucket private và hai CloudFront distribution dùng OAC.
  * Thay thế ý tưởng dùng một EC2 quản lý thủ công bằng một bản triển khai Terraform lặp lại được, chạy trên hai Availability Zone — `terraform apply` tạo đủ toàn bộ resource chỉ trong một lần chạy.

* **Phát Triển Dự Án QuickBite:**
  * Triển khai image FastAPI backend (đã push lên ECR ở Tuần 3) lên Auto Scaling Group và xác minh kết nối ổn định tới RDS Multi-AZ mới.
  * Build React cho production với API base là CloudFront API domain và đồng bộ static build lên S3 web bucket private, phân phối qua CloudFront.
  * Xác minh `GET /health` qua ALB target group phục vụ giám sát real-time trạng thái database và server.
  * Kiểm thử thành công toàn bộ luồng End-to-End (xem menu, đặt hàng, cập nhật trạng thái) trên các URL CloudFront thực tế.
