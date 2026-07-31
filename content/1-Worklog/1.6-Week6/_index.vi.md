---
title: "Worklog Tuần 6"
date: 2026-07-06
weight: 6
chapter: false
pre: " <b> 1.6. </b> "
---

### Mục tiêu tuần 6:

* Nghiên cứu kiến trúc AWS Serverless và Event-Driven: Amazon EventBridge, Amazon SQS, Amazon SNS, và AWS Lambda + Amazon SES cho email.
* Thiết kế (chưa triển khai) một luồng thông báo bất đồng bộ cho sự kiện `OrderCreated` và `OrderStatusChanged` của QuickBite.
* Đánh giá xem hệ thống demo hiện tại (EC2/RDS/S3/CloudWatch) có thực sự cần Lambda + SES hay không, hay Mailpit vẫn là lựa chọn phù hợp ở giai đoạn này.
* Ghi lại phần nghiên cứu thành một ghi chú thiết kế nội bộ, đề xuất kiến trúc cho tương lai.

### Các công việc cần triển khai trong tuần này:
| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --- | --- | --- | --- |
| 2 | - Tìm hiểu khái niệm Serverless, mô hình thực thi AWS Lambda và IAM execution role <br> - **Nghiên cứu Amazon SES:** <br>&emsp; + Đọc về SES Sandbox, xác thực sender identity và sending policy <br>&emsp; + So sánh SES với Mailpit cho quy mô demo một môi trường duy nhất hiện tại của QuickBite | 06/07/2026 | 06/07/2026 | - <https://cloudjourney.awsstudygroup.com/> <br> - Tài liệu AWS SES |
| 3 | - **Nghiên cứu Event-Driven Pattern:** <br>&emsp; + Tìm hiểu EventBridge (định tuyến theo rule), SQS (durable queue) và SNS (fan-out) <br>&emsp; + Phác thảo luồng `OrderCreated` → EventBridge → SQS → Lambda → SES như một bài tập thiết kế | 07/07/2026 | 07/07/2026 | - Tài liệu AWS Lambda <br> - Tài liệu AWS EventBridge |
| 4 | - **Các Vấn Đề Thiết Kế Cần Ghi Nhận:** <br>&emsp; + Phân tích retry/backoff, idempotency, thứ tự xử lý event, dead-letter queue và versioning schema cho luồng đề xuất <br>&emsp; + Kết luận đây là hạng mục cho roadmap tương lai, chưa cần thiết cho bản demo năng lực cố định hiện tại | 08/07/2026 | 08/07/2026 | - Tài liệu AWS EventBridge DLQ |
| 5 | - **Viết Ghi Chú Thiết Kế:** <br>&emsp; + Soạn ghi chú ngắn về event-driven architecture, giải thích mô hình này có thể tách email, báo cáo và thông báo khỏi request tạo đơn như thế nào <br>&emsp; + Nêu rõ EventBridge, SQS, Lambda và SES **chưa được triển khai** trong bản demo QuickBite | 09/07/2026 | 09/07/2026 | - QuickBite README.md |
| 6 | - **Rà soát & Hoàn thiện:** <br>&emsp; + Rà soát ghi chú thiết kế bằng cả tiếng Anh và tiếng Việt <br>&emsp; + Xác nhận hệ thống thực tế vẫn dùng Mailpit cho email local/demo, giữ đúng tính trung thực của báo cáo | 10/07/2026 | 10/07/2026 | - Bản nháp ghi chú thiết kế |


### Kết quả đạt được tuần 6:

* **Nền Tảng Điện Toán Đám Mây AWS:**
  * Nghiên cứu các khái niệm Serverless và event-driven (EventBridge, SQS, SNS, Lambda, SES) và cách chúng có thể tách các tác vụ phụ khỏi request tạo đơn hàng.
  * Phân tích trên giấy các phần khó của thiết kế bất đồng bộ: retry, idempotency, thứ tự xử lý, dead-letter queue và versioning schema.
  * Kết luận Lambda + SES là **hạng mục cho roadmap tương lai** của QuickBite, chưa cần thiết cho bản demo một môi trường hiện tại; Mailpit vẫn là công cụ mô phỏng email đã triển khai cho đơn hàng và cập nhật trạng thái.

* **Phát Triển Dự Án QuickBite:**
  * Ghi lại đề xuất thiết kế `OrderCreated → EventBridge → SQS → Lambda → SES` như một hạng mục roadmap tương lai, bằng cả tiếng Anh và tiếng Việt.
  * Giữ đúng tính trung thực của báo cáo: chưa có Lambda function hay SES sender identity nào thực sự được tạo cho bản demo này.
