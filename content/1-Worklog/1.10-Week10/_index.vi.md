---
title: "Worklog Tuần 10"
date: 2026-08-03
weight: 10
chapter: false
pre: " <b> 1.10. </b> "
---

### Mục tiêu tuần 10:

* Thực hiện kiểm thử toàn trình End-to-End (E2E Local & Cloud) cho tất cả các luồng vai trò (`Customer`, `Kitchen`, `Delivery`, `Admin`).
* Rà soát quy trình `terraform destroy` và các tài nguyên nhạy cảm về chi phí, chưa tháo dỡ môi trường demo đang chạy.
* Quay video demo sản phẩm hoàn chỉnh và đóng gói tài liệu báo cáo dự án QuickBite.
* Hoàn thành và nộp bài tổng kết chương trình thực tập First Cloud AI Journey (FCAJ).

### Các công việc cần triển khai trong tuần này:
| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --- | --- | --- | --- |
| 2 | - **Kiểm thử Toàn trình End-to-End:** <br>&emsp; + Chạy script kiểm thử tự động `e2e_local.py` cho backend <br>&emsp; + Thực hiện test tay toàn bộ luồng: Khách đặt hàng -> Kitchen chế biến -> Delivery giao hàng -> Admin kiểm tra báo cáo | 03/08/2026 | 03/08/2026 | - `backend/scripts/e2e_local.py` <br> - `backend/tests/` |
| 3 | - **Rà soát Terraform Destroy & Tài nguyên Nhạy cảm về Chi phí:** <br>&emsp; + Xác nhận thứ tự destroy (main stack trước, bootstrap sau) và các cấu hình vòng đời cho môi trường demo (force_destroy, force_delete, tắt deletion protection) trong `docs/cleanup.md` <br>&emsp; + Kiểm tra AWS Cost Explorer cho các thành phần nhạy cảm về chi phí: NAT Gateway, RDS Multi-AZ, ALB, hai EC2 instance, CloudWatch Logs và lưu lượng CloudFront | 04/08/2026 | 04/08/2026 | - `docs/cleanup.md` <br> - AWS Cost Explorer |
| 4 | - **Hoàn thiện Tài liệu Kỹ thuật:** <br>&emsp; + Cập nhật đầy đủ file `README.md`, sơ đồ kiến trúc deployment và OpenAPI specification <br>&emsp; + Tổng hợp danh mục các API endpoints và tài khoản demo | 05/08/2026 | 05/08/2026 | - `README.md` <br> - `docs/deploy-walkthrough.md` |
| 5 | - **Quay Video Demo Sản Phẩm:** <br>&emsp; + Quay video kịch bản demo hệ thống QuickBite từ giao diện React Frontend đến AWS Backend <br>&emsp; + Thể hiện các tính năng: Đặt hàng, theo dõi qua `order_code`, email xác nhận qua Mailpit, Admin Dashboard và Export CSV | 06/08/2026 | 06/08/2026 | - Mã nguồn QuickBite |
| 6 | - **Nộp Bài & Đóng Hồ Sơ Thực Tập:** <br>&emsp; + Kiểm tra lại toàn bộ 10 Worklogs trên Hugo Markdown <br>&emsp; + Đóng gói mã nguồn, link video demo và nộp báo cáo cuối kỳ chương trình FCAJ | 07/08/2026 | 07/08/2026 | - Trang FCAJ Portal |


### Kết quả đạt được tuần 10:

* **Nền Tảng Điện Toán Đám Mây AWS:**
  * Rà soát và xác nhận kế hoạch `terraform destroy` cùng cấu hình vòng đời cho môi trường demo, giữ hệ thống chạy phục vụ demo cuối kỳ thay vì tháo dỡ sớm.
  * Xác minh mô hình triển khai Cloud-Native ổn định, sẵn sàng production cho QuickBite trên AWS thông qua lần chạy kiểm thử E2E.

* **Phát Triển Dự Án QuickBite:**
  * Kiểm thử thành công script `e2e_local.py` và hoàn thiện toàn bộ luồng nghiệp vụ end-to-end.
  * Hoàn tất video demo, bộ tài liệu triển khai (`docs/aws-deployment.md`, `docs/cleanup.md`) và nộp thành công báo cáo thực tập 10 tuần.
