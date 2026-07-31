---
title: "FCAJ x Agentic AI Build Week"
date: 2026-07-25
weight: 2
chapter: false
pre: " <b> 4.2. </b> "
---

# Summary Report: “FCAJ x Agentic AI Build Week: Show Up. Build. Pitch. WIN!”

### Event Objectives

- Tạo sân chơi Hackathon thực chiến cho các builder trải nghiệm và cùng nhau biến ý tưởng AI thành sản phẩm hoàn chỉnh
- Truyền cảm hứng cho thế hệ tài năng trẻ chuyển đổi tư duy (mental model), áp dụng Agentic AI để đổi mới sáng tạo
- Trình diễn các sản phẩm thắng giải, kiến trúc kỹ thuật tiêu biểu trên hạ tầng AWS và ứng dụng thực tế
- Chia sẻ kinh nghiệm thực tế về quản lý dự án, tinh thần làm việc nhóm và kỹ năng pitching khi tham gia Hackathon

### Speakers

- **Joseph Marazota** – Head of Technology, Asia
- **Nguyễn Gia Hưng** – Head of Solutions Architecture, Vietnam
- **One Team** – Đội đạt Giải Nhất (AWS Track)
- **Signal Scout** – Đội đạt Giải Nhì (AWS Track)
- **Team Plan** – Đội tham gia Hackathon
- **Team 3K** – Đội tham gia Hackathon
- **Six Pillars** – Đội tham gia Hackathon

### Key Highlights

#### Mở đầu & Phát biểu truyền cảm hứng
- **Tư duy phát triển mới**: Chuyển đổi từ mô hình phát hành phần mềm truyền thống (vài tháng/lần) sang kỷ nguyên Agentic AI với khả năng tự động triển khai liên tục.
- **Vai trò của AI và Con người**: AI và Agent thông minh giúp vận hành hạ tầng quy mô lớn (như hàng triệu robot kho vận), giữ con người ở vị trí quyết định (Human-in-the-loop).

#### Team 1: One Team (Giải Nhất) – Trợ lý đặt hàng bằng AI
- **Vấn đề**: Việc bắt khách hàng chuyển đổi sang app riêng để đặt hàng gây đứt gãy trải nghiệm và mất đơn hàng.
- **Giải pháp**: Xây dựng Multi-channel Agent trên Zalo/WhatsApp giúp người dùng đặt đồ ăn trực tiếp trong khung chat.
- **Kiến trúc & Chi phí**: Sử dụng AWS Bedrock, Agent Core tích hợp bộ nhớ (Memory) lưu thói quen người dùng và TinyFish để cào dữ liệu, chi phí tối ưu chỉ khoảng $0.006/đơn hàng.

#### Team 2: Signal Scout (Giải Nhì) – Hệ thống Multi-Agent thu thập thông tin chiến lược
- **Vấn đề**: Thông tin chiến lược và đối thủ cạnh tranh bị phân tán rải rác trên nhiều báo cáo tài chính và truyền thông.
- **Giải pháp**: Hệ thống Multi-Agent tự động cào và tổng hợp tín hiệu kinh doanh qua TinyFish/Apify, đưa ra phân tích và dự báo ROI chiến lược.
- **Kiến trúc**: Triển khai trên AWS Amplify, xác thực Cognito, sử dụng Bedrock Agents và tích hợp Langfuse để giám sát Agent.

#### Team 3: Team Plan – Trợ lý AI thiết kế kiến trúc hệ thống
- **Vấn đề**: Kiến trúc sư giải pháp (SA) mất nhiều thời gian để vẽ sơ đồ kiến trúc, tính toán chi phí và viết mã triển khai.
- **Giải pháp**: Ứng dụng AI cho phép nhập yêu cầu bằng ngôn ngữ tự nhiên hoặc tài liệu để tự động sinh sơ đồ (Draw.io), bảng tính chi phí và file Terraform/CloudFormation để tự động triển khai.

#### Team 4: Team 3K – Hệ thống giám sát và điều phối đám đông Shepherd
- **Vấn đề**: Ùn tắc cục bộ tại sân bay, siêu thị và các sự kiện lớn gây gián đoạn luồng vận hành.
- **Giải pháp**: Giám sát luồng người qua camera real-time, phân tích mật độ theo từng khu vực và đưa ra cảnh báo điều phối tự động.
- **Kiến trúc**: Sử dụng Kinesis Video Streams, ECS Fargate chạy YOLOv26 & ByteTrack, DynamoDB/S3 và AI Copilot tương tác với quản lý.

#### Team 5: Six Pillars – Engine phân tích và điều tra phòng chống rửa tiền (AML)
- **Vấn đề**: 90-95% cảnh báo rửa tiền ở các ngân hàng là cảnh báo giả (false positive), gây tốn kém chi phí review thủ công.
- **Giải pháp**: Hệ thống Multi-Agent tự động hóa khâu xác minh KYC, phân tích dòng tiền và đối soát danh sách cấm vận (Sanctions).
- **Kiến trúc**: Kết hợp Kinesis Data Streams, mô hình XGBoost phân loại nhanh, các Bedrock Sub-agents và Bedrock Guardrails kiểm soát rủi ro.

### Key Takeaways

#### Design Mindset
- **Tập trung vào nỗi đau thực tế**: Công nghệ dù phức tạp đến đâu cũng phải bắt đầu từ việc giải quyết vấn đề nghiệp vụ cụ thể của doanh nghiệp.
- **Giữ con người trong vòng kiểm soát (Human-in-the-loop)**: Đặc biệt quan trọng đối với các lĩnh vực nhạy cảm như tài chính, ngân hàng và quản trị rủi ro.

#### Technical Architecture
- **Mô hình Multi-Agent**: Tách biệt nhiệm vụ cho các Sub-Agent chuyên biệt được điều phối bởi Agent trung tâm giúp tăng tính chính xác và dễ bảo trì.
- **Tối ưu hóa chi phí & Bảo mật**: Kết hợp dịch vụ AWS Native với công cụ bên thứ ba hợp lý để vừa đảm bảo compliance vừa tiết kiệm ngân sách.

#### Modernization Strategy
- **Chiến lược khoanh vùng MVP**: Khi làm sản phẩm nhanh, cần tập trung hoàn thiện luồng cốt lõi (Proof of Concept / MVP) thay vì mở rộng scope quá lớn.
- **Học tập qua trải nghiệm thực tế**: Tham gia Hackathon là phương pháp ngắn nhất để thử nghiệm ý tưởng, nâng cao tay nghề và kết nối cộng đồng.

### Applying to Work

- **Ứng dụng Agentic Workflow**: Áp dụng mô hình Multi-Agent để tự động hóa các quy trình làm việc đa bước trong doanh nghiệp.
- **Tận dụng dịch vụ Serverless & Managed AI**: Sử dụng AWS Bedrock, Agent Core, Kinesis để xây dựng kiến trúc xử lý sự kiện linh hoạt và tiết kiệm.
- **Tích hợp kênh tương tác thân thiện**: Đưa trải nghiệm AI trực tiếp vào các ứng dụng trò chuyện quen thuộc (như Zalo, WhatsApp) hoặc Dashboard nội bộ.

### Event Experience

Tham dự sự kiện **“FCAJ x Agentic AI Build Week”** mang lại cái nhìn toàn diện về cách phát triển sản phẩm AI thế hệ mới từ khâu lên ý tưởng, thiết kế kiến trúc đến triển khai thực tế. Các trải nghiệm nổi bật bao gồm:

#### Learning from highly skilled speakers
- Lắng nghe những chia sẻ định hướng tư duy công nghệ từ các lãnh đạo AWS.
- Tiếp thu các bài học thực chiến từ các đội thi qua những case study thực tế trong nhiều lĩnh vực như F&B, Tài chính - Ngân hàng, Bán lẻ.

#### Hands-on technical exposure
- Trực tiếp theo dõi demo các giải pháp Multi-Agent, xử lý video real-time và sinh mã tự động.
- Hiểu rõ hơn về các đánh đổi (trade-off) giữa chi phí, độ trễ và độ an toàn khi thiết kế hệ thống trên Cloud.

#### Leveraging modern tools
- Khám phá chuyên sâu các dịch vụ AWS tiên tiến như **AWS Bedrock**, **Agent Core**, **Kinesis Video Streams**, **ECS Fargate**, **Amplify**.

#### Networking and discussions
- Giao lưu, trao đổi kinh nghiệm cùng các chuyên gia, cố vấn kỹ thuật và các đồng nghiệp trong cộng đồng lập trình viên.

#### Lessons learned
- Việc quản lý phạm vi dự án (scope) và tinh thần đồng đội là yếu tố quyết định để hoàn thiện sản phẩm chất lượng trong thời gian ngắn.
- AI Agent đóng vai trò trợ lý đắc lực nâng cao năng suất làm việc của con người chứ không thay thế hoàn toàn vai trò quyết định chuyên môn.

#### Some event photos

{{< report-image src="images/events/fcaj-agentic-ai-build-week.jpg" alt="Tham dự hackathon FCAJ x Agentic AI Build Week cùng các bạn builder khác" caption="Tại sự kiện FCAJ x Agentic AI Build Week, cùng các builder khác tham dự." >}}

> Nhìn chung, sự kiện không chỉ cung cấp những kiến thức kỹ thuật giá trị mà còn định hình lại tư duy thiết kế hệ thống, ứng dụng GenAI và tăng cường tinh thần hợp tác trong cộng đồng công nghệ.
