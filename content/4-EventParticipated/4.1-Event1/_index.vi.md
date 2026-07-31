---
title: "AWS Security Agent, SLA/Monitoring & Cloud Certification"
date: 2026-07-30
weight: 1
chapter: false
pre: " <b> 4.1. </b> "
---


# Summary Report: “AWS Security Agent, SLA/Monitoring & Cloud Certification Workshop”

### Event Objectives

- Giới thiệu dịch vụ mới **AWS Security Agent** hỗ trợ tự động hóa Pentest, Code Review và Design Review.
- Chia sẻ tư duy quản trị vận hành hệ thống qua **SLA/Service Level Agreement** và phương pháp **Monitoring hiệu quả** đứng từ góc nhìn doanh nghiệp.
- Cung cấp lộ trình, cấu trúc bài thi và các mẹo thực chiến để chinh phục chứng chỉ **AWS Certified Cloud Practitioner (CLF-C02)**.

### Speakers

- **Anh Thịnh** – DevSecOps Engineer @ 2Solutions & FirstFlow AI
- **Anh Sơn** – Infrastructure Support Engineer @ Endava (Cựu Student Builder @ UIT)
- **Anh Huy** – AWS Cloud Enthusiast & Speaker

### Key Highlights

#### 1. AWS Security Agent & Tự động hóa Bảo mật (Presenter: Anh Thịnh)
- **Giải quyết Pain Point thực tế**: Thuê đội ngũ Pentest truyền thống tốn kém từ $5,000 – $20,000/dự án, tốn thời gian và phụ thuộc nhiều vào trình độ nhân sự.
- **Các tính năng cốt lõi**:
  - **Design Security Review**: Phân tích file Markdown/Doc/Terraform dựa trên bộ tiêu chuẩn PCI-DSS, AWS Well-Architected Framework (Free tier: 200 lượt review/tháng).
  - **Code Review**: Tích hợp trực tiếp Webhook vào GitHub/GitLab, tự động quét và gợi ý sửa lỗi bảo mật qua Pull Request (Free tier: 1,000 PR review/tháng).
  - **Penetration Testing (Pentest)**: Tự động giả lập các kịch bản tấn công thực tế từ Front-end đến Back-end, hỗ trợ xuất báo cáo chi tiết và bước tái hiện lỗi (Dùng thử miễn phí 2 tháng, 400 task-hours/tháng).
- **Hạn chế kỹ thuật**: Chưa hỗ trợ bypass MFA (khi yêu cầu OTP/SMS) và giao thức xác thực hai chiều mTLS (Mutual TLS).

#### 2. SLA & Monitoring trong môi trường Enterprise (Presenter: Anh Sơn)
- **Tầm quan trọng của SLA (Service Level Agreement)**: Cam kết chất lượng dịch vụ với khách hàng. Vi phạm SLA (downtime vượt ngưỡng cho phép) gây thiệt hại tài chính rất lớn cho doanh nghiệp.
- **Tư duy Monitoring toàn diện**:
  - **Healthy Infra ≠ Healthy User Experience**: Hạ tầng (CPU/RAM/Server) báo xanh không đồng nghĩa với việc người dùng không gặp lỗi ứng dụng hay không bị gián đoạn trải nghiệm.
  - **Mô hình Kim tự tháp Monitoring**: Giám sát đa tầng từ Cloud Provider, Hạ tầng (EC2/RDS), Ứng dụng (App/DB Connection) cho đến trải nghiệm người dùng cuối (Customer Journey).
  - **Quy trình ứng phó rủi ro (SOP & SNS)**: Sử dụng AWS CloudWatch Dashboards/Alarms kết hợp với Amazon SNS để gửi cảnh báo tức thì, ghi chép nhật ký (Log) để liên tục cải tiến hệ thống.

#### 3. Hành trình chinh phục Chứng chỉ AWS Cloud Practitioner (Presenter: Anh Huy)
- **Tổng quan về bài thi CLF-C02**:
  - Cấu trúc: 65 câu hỏi (50 câu tính điểm), thời gian 90 phút (+30 phút đền bù ngôn ngữ cho người Việt = 120 phút), điểm Pass: 700/1000, thời hạn 3 năm, lệ phí: $100.
  - 4 Miền kiến thức: Cloud Concepts (24%), Security & Compliance (30%), Cloud Technology & Services (34%), Billing & Pricing (12%).
- **Kiến thức trọng tâm cần nắm**:
  - **6 Trụ cột Well-Architected Framework** & **AWS Cloud Adoption Framework (CAF)**.
  - **Shared Responsibility Model**: Phân định rõ trách nhiệm bảo mật "OF the Cloud" (AWS) và "IN the Cloud" (Khách hàng).
  - **Mô hình chi phí EC2**: Phân biệt On-Demand, Reserved Instances (tiết kiệm đến 72%), và Spot Instances (tiết kiệm đến 90% nhưng có rủi ro bị thu hồi tài nguyên sau 2 phút thông báo).
- **Mẹo thi (Tips & Tricks)**:
  - **Keyword Mapping**: Nhận diện từ khóa nhanh (ví dụ: *Decouple/Microservices* → SQS; *List cost/Interruptible* → Spot Instance).
  - **Phương pháp loại trừ (Elimination Technique)**: Loại bỏ ngay 2 phương án không liên quan để tăng tỷ lệ chọn đúng lên 50/50.
  - **Tận dụng Flag for Review**: Đánh cờ các câu khó để quay lại sau, không sa lầy làm mất thời gian.

### Key Takeaways

#### Design Mindset
- **Security-First Approach**: Nhúng bảo mật ngay từ giai đoạn lập kế hoạch (Design review) và đưa công cụ kiểm tra tự động vào CI/CD pipeline.
- **Customer-Oriented Monitoring**: Đặt trải nghiệm khách hàng làm trọng tâm thay vì chỉ chăm chăm vào chỉ số kĩ thuật thuần túy của Server.

#### Technical Architecture
- **Tự động hóa bằng Multi-Agent**: Tận dụng AWS Bedrock & Multi-agent framework để tự động quét lỗ hổng và rà soát mã nguồn.
- **Kiến trúc HA (High Availability) & Monitoring**: Thiết kế hệ thống 3-tier chuẩn Best Practice trên AWS (ALB, EC2 trong Multi-AZ, RDS) kết hợp CloudWatch Alarms giám sát kết nối DB.

#### Modernization Strategy
- **Chuẩn hóa quy trình tài liệu (Doc-first)**: Mọi thay đổi về hạ tầng và thiết kế đều phải được làm Doc kỹ lưỡng trước khi triển khai.
- **Đầu tư chuẩn hóa năng lực (Cloud Certification)**: Xây dựng nền tảng bài bản qua các chứng chỉ AWS để nâng cao tư duy thiết kế hệ thống theo tiêu chuẩn doanh nghiệp.

### Applying to Work

- **Tích hợp AWS Security Agent**: Thử nghiệm tính năng Code Review trên repository GitHub/GitLab cá nhân hoặc dự án đồ án.
- **Xây dựng Custom CloudWatch Alarm**: Thiết lập cảnh báo cho các chỉ số quan trọng (Database Connections, HTTP Status 5xx) gửi thông báo qua Email/SMS bằng SNS.
- **Luyện đề & Đăng ký thi CLF-C02**: Áp dụng phương pháp khoanh vùng Keyword và loại trừ phương án sai để chinh phục chứng chỉ AWS cơ bản.

### Event Experience

Buổi chia sẻ mang lại nhiều kiến thức thực chiến từ các diễn giả dày dặn kinh nghiệm làm việc tại các môi trường doanh nghiệp và Global:

#### Learning from highly skilled speakers
- Tiếp thu tư duy bảo mật DevSecOps thực tế và các công cụ AI mới nhất từ anh Thịnh.
- Hiểu được góc nhìn vận hành hệ thống thực tế ở các công ty lớn (NOC/SOC, SLA, Risk Management) từ chia sẻ đầy hài hước và chân thật của anh Sơn.
- Nắm trọn bí kíp và lộ trình ôn thi chứng chỉ AWS từ anh Huy.

#### Hands-on technical exposure
- Theo dõi Demo trực tiếp các bước cấu hình Domain Verification, GitHub Integration, PenTest và cách đọc báo cáo Security Findings.
- Trải nghiệm bài Demo thực hành xử lý sự cố đứt kết nối Database thực tế trên giao diện AWS CloudWatch Dashboard & SNS.

#### Leveraging modern tools
- Khám phá dịch vụ mới **AWS Security Agent**, **AWS Bedrock**, **Amazon CloudWatch**, **Amazon SNS**, **AWS Well-Architected Tool**.

#### Networking and discussions
- Học hỏi các câu chuyện thực tế về môi trường làm việc IT, cách vượt qua thử thách khi làm vị trí Support/Infra Layer 1 và định hướng phát triển sự nghiệp Cloud.

#### Some event photos

{{< report-image src="images/events/aws-security-agent-sla-monitoring-cloud-cert.jpg" alt="Diễn giả trình bày phần SLA và Monitoring trong buổi AWS Security Agent, SLA/Monitoring & Cloud Certification" caption="Anh Sơn trình bày về khoảng cách giữa “hạ tầng khỏe” và “người dùng hài lòng” trong phần SLA/Monitoring." >}}

> Tóm lại, sự kiện mang đến cái nhìn toàn diện từ khâu bảo mật tự động, tư duy vận hành hệ thống theo chuẩn SLA doanh nghiệp cho đến lộ trình chuẩn hóa kiến thức Cloud qua chứng chỉ quốc tế.