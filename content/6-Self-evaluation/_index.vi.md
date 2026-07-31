---
title: "Tự đánh giá"
date: 2024-01-01
weight: 6
chapter: false
pre: " <b> 6. </b> "
---

#### Thông tin thực tập

| | |
|---|---|
| **Đơn vị** | Công ty TNHH Amazon Web Services Việt Nam |
| **Chương trình** | Workforce Bootcamp – First Cloud AI Journey |
| **Thời gian** | 01/06/2026 – 15/08/2026 (2 tháng) |
| **Hạn nộp project** | 31/07/2026 |
| **Người hướng dẫn** | Lữ Hoàn Thiện — Program Manager |
| **Liên hệ người hướng dẫn** | [thienlh@awsfcaj.com](mailto:thienlh@awsfcaj.com) · 0986 479 292 |

Trong thời gian tham gia chương trình Workforce Bootcamp – First Cloud AI Journey tại AWS Việt Nam, tôi đã tìm hiểu các dịch vụ cốt lõi của AWS và dùng chúng để thiết kế, xây dựng và triển khai **QuickBite**, một nền tảng đặt món ăn và quản lý nhà hàng full-stack — bao gồm backend FastAPI, frontend React + TypeScript, đóng gói Docker, và một bản triển khai thật trên AWS (EC2, RDS, S3, CloudFront, CloudWatch). Quá trình này cho tôi cơ hội thực hành những quyết định kiến trúc cloud mà trước đây tôi chỉ biết qua lý thuyết: mạng private-vs-public (security group của RDS), xử lý HTTPS/mixed-content (CloudFront reverse proxy), và dọn dẹp tài nguyên để kiểm soát chi phí.

Trong suốt chương trình, tôi cố gắng giữ kỷ luật hoàn thành từng giai đoạn — local, rồi Docker, rồi AWS — trước khi chuyển sang giai đoạn tiếp theo, và chủ động hỏi khi một khái niệm (như security group VPC hay cache behavior của CloudFront) chưa thật sự hiểu rõ thay vì đoán mò.

Để phản ánh khách quan giai đoạn này, tôi tự đánh giá bản thân theo các tiêu chí dưới đây. Đây là bản tự chấm nháp của tôi — bạn chỉnh lại bất kỳ dòng nào chưa đúng với cách bạn tự nhìn nhận.

| STT | Tiêu chí                            | Mô tả                                                                                            | Tốt | Khá | Trung bình |
| --- | ----------------------------------- | ------------------------------------------------------------------------------------------------ | --- | --- | ---------- |
| 1   | **Kiến thức và kỹ năng chuyên môn** | Hiểu biết về ngành, áp dụng kiến thức vào thực tế, kỹ năng sử dụng công cụ, chất lượng công việc | ✅   | ☐   | ☐          |
| 2   | **Khả năng học hỏi**                | Tiếp thu kiến thức mới, học hỏi nhanh                                                            | ✅   | ☐   | ☐          |
| 3   | **Chủ động**                        | Tự tìm hiểu, nhận nhiệm vụ mà không chờ chỉ dẫn                                                  | ☐   | ✅   | ☐          |
| 4   | **Tinh thần trách nhiệm**           | Hoàn thành công việc đúng hạn, đảm bảo chất lượng                                                | ✅   | ☐   | ☐          |
| 5   | **Kỷ luật**                         | Tuân thủ giờ giấc, nội quy, quy trình làm việc                                                   | ☐   | ✅   | ☐          |
| 6   | **Tính cầu tiến**                   | Sẵn sàng nhận feedback và cải thiện bản thân                                                     | ✅   | ☐   | ☐          |
| 7   | **Giao tiếp**                       | Trình bày ý tưởng, báo cáo công việc rõ ràng                                                     | ☐   | ✅   | ☐          |
| 8   | **Hợp tác nhóm**                    | Làm việc hiệu quả với đồng nghiệp, tham gia nhóm                                                 | ☐   | ✅   | ☐          |
| 9   | **Ứng xử chuyên nghiệp**            | Tôn trọng đồng nghiệp, đối tác, môi trường làm việc                                              | ✅   | ☐   | ☐          |
| 10  | **Tư duy giải quyết vấn đề**        | Nhận diện vấn đề, đề xuất giải pháp, sáng tạo                                                    | ☐   | ✅   | ☐          |
| 11  | **Đóng góp vào dự án/tổ chức**      | Hiệu quả công việc, sáng kiến cải tiến, ghi nhận từ team                                         | ☐   | ✅   | ☐          |
| 12  | **Tổng thể**                        | Đánh giá chung về toàn bộ quá trình thực tập                                                     | ☐   | ✅   | ☐          |

### Cần cải thiện

* Tìm hiểu sâu hơn ngoài các dịch vụ AWS cốt lõi đã dùng trong QuickBite (EC2, RDS, S3, CloudFront, CloudWatch) — thực hành thêm về thiết kế IAM policy, mạng VPC, và infrastructure-as-code (CDK/CloudFormation) thay vì cấu hình thủ công qua console.
* Rèn thói quen viết test và tài liệu song song với code, thay vì chủ yếu viết sau khi tính năng đã chạy được.
* Cải thiện quản lý thời gian xuyên suốt một chu kỳ dự án — giai đoạn triển khai AWS mất nhiều thời gian hơn dự kiến vì các vấn đề về mạng (kết nối RDS, mixed content) chưa được lường trước sớm.
* Luyện tập trình bày các quyết định kỹ thuật ngắn gọn hơn, đặc biệt bằng tiếng Anh, vì phần lớn tài liệu AWS và trao đổi với người hướng dẫn diễn ra bằng tiếng Anh.