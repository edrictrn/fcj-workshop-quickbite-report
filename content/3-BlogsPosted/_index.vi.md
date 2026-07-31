---
title: "Các bài blogs đã đăng"
date: 2026-07-30
weight: 3
chapter: false
pre: " <b> 3. </b> "
includeInReport: false
---
Phần này giới thiệu ba bài viết về AWS được em biên soạn trong quá trình phát triển QuickBite. Mỗi bài đều có phiên bản tiếng Việt và tiếng Anh.

### [Blog 1 - Tìm hiểu AWS Secrets Manager](3.1-Blog1/)
Bài viết trình bày cách AWS Secrets Manager thay thế việc lưu `DATABASE_URL`, JWT secret và API key trong file `.env`, bao gồm cơ chế mã hóa qua KMS, phân quyền qua IAM Role, các bước tạo và truy xuất secret, cùng chi phí và độ trễ cần cân nhắc. Nội dung liên hệ trực tiếp với cách QuickBite lưu `DATABASE_URL` và JWT secret trong Secrets Manager qua Terraform data module.

### [Blog 2 - Disaster Recovery trên AWS](3.2-Blog2/)
Bài viết giới thiệu RTO, RPO, Backup and Restore, Pilot Light, Warm Standby và Multi-site Active/Active. Nội dung được liên hệ với QuickBite thông qua backup RDS, bảo vệ dữ liệu S3, runbook phục hồi và sự khác nhau giữa một bản demo ngắn hạn với workload production.

### [Blog 3 - Amazon GuardDuty vs Amazon Inspector](3.3-Blog3/)
Bài viết so sánh Amazon GuardDuty (phát hiện mối đe dọa theo thời gian thực) và Amazon Inspector (quét lỗ hổng bảo mật), phân tích cơ chế hoạt động, phạm vi bảo vệ và thời điểm phát huy tác dụng của từng dịch vụ, kèm bài học về Defense-in-Depth và tổng hợp cảnh báo qua AWS Security Hub.
