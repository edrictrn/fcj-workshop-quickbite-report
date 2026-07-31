---
title: "Worklog Tuần 9"
date: 2026-07-27
weight: 9
chapter: false
pre: " <b> 1.9. </b> "
---

### Mục tiêu tuần 9:

* Tích hợp Amazon CloudWatch để thu thập Logs, Metrics và thiết lập cảnh báo tự động.
* Củng cố và kiểm thử chi tiết endpoint Health Check (`GET /health`).
* Bảo mật hạ tầng Cloud: Quản lý biến môi trường an toàn, thiết lập CORS và Security Groups.
* Tiến hành đánh giá hiệu năng và giới hạn truy cập (Rate Limiting).

### Các công việc cần triển khai trong tuần này:
| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --- | --- | --- | --- |
| 2 | - **Tích hợp AWS CloudWatch Logging:** <br>&emsp; + Cấu hình CloudWatch Agent trên EC2 instance để đẩy application logs từ FastAPI <br>&emsp; + Tạo Log Groups và Log Streams riêng biệt cho môi trường Production | 27/07/2026 | 27/07/2026 | - `docs/aws-deployment.md` <br> - AWS CloudWatch Docs |
| 3 | - **Cấu hình CloudWatch Alarms & Metrics:** <br>&emsp; + Tạo Metric Filter để theo dõi tần suất lỗi (5xx Error Rate, 4xx Rate) <br>&emsp; + Cấu hình CPU Alarm ở ngưỡng 70% trong hai chu kỳ 300 giây, gửi trạng thái Alarm/OK qua Amazon SNS | 28/07/2026 | 28/07/2026 | - Tài liệu AWS CloudWatch |
| 4 | - **Tối ưu Endpoint Health Check (`main.py`):** <br>&emsp; + Nâng cấp endpoint `GET /health` để kiểm tra kết nối tới RDS PostgreSQL và S3 bucket <br>&emsp; + Tích hợp API health check với ALB Target Group Health Check | 29/07/2026 | 29/07/2026 | - `backend/main.py` <br> - QuickBite README.md |
| 5 | - **Security Hardening & Rate Limiting:** <br>&emsp; + Áp dụng module `rate_limit.py` để ngăn chặn tấn công Brute-force vào các endpoint Auth <br>&emsp; + Giới hạn cấu hình CORS gốc (`CORS Origins`) chỉ chấp nhận domain CloudFront/S3 Frontend | 30/07/2026 | 30/07/2026 | - `backend/rate_limit.py` <br> - `backend/main.py` |
| 6 | - **Kiểm thử Giám sát & Cảnh báo:** <br>&emsp; + Thử nghiệm mô phỏng lỗi server để kiểm tra CloudWatch Alarm có gửi thông báo cảnh báo hay không <br>&emsp; + Kiểm tra độ ổn định của API dưới tải lớn | 31/07/2026 | 31/07/2026 | - QuickBite Codebase |


### Kết quả đạt được tuần 9:

* **Nền Tảng Điện Toán Đám Mây AWS:**
  * Tích hợp thành công Amazon CloudWatch cho toàn bộ hệ thống logs trên EC2 và thiết lập Alarms cảnh báo sự cố tự động.
  * Cấu hình an toàn cho AWS Security Groups và phân quyền IAM bám sát nguyên tắc tối thiểu quyền (Least Privilege).

* **Phát Triển Dự Án QuickBite:**
  * Nâng cấp endpoint Health Check (`/health`) theo chuẩn Cloud Monitoring.
  * Áp dụng Rate Limiting (`rate_limit.py`) bảo vệ các API quan trọng và tối ưu cấu hình bảo mật CORS trên Backend.