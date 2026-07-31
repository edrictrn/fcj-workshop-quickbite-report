---
title: "Blog 3 - Amazon GuardDuty vs Amazon Inspector"
date: 2026-07-30
weight: 3
chapter: false
pre: " <b> 3.3. </b> "
---
# Amazon GuardDuty vs Amazon Inspector: Đâu là giải pháp bảo mật phù hợp cho hệ thống AWS của bạn?

**Trạng thái nội dung:** Hoàn thành

**Minh chứng đăng bài:** [Xem bài viết trên Facebook (AWS Study Group FCJ)](https://www.facebook.com/groups/awsstudygroupfcj/permalink/2228988517866108/?rdid=YsCTVpaj1baaJAKe)

Khi bắt đầu xây dựng và vận hành hệ thống trên đám mây AWS, bảo mật luôn là chủ đề khiến nhiều bạn đau đầu nhất. Trong hệ sinh thái rộng lớn của AWS, hai dịch vụ bảo mật rất dễ gây nhầm lẫn mà mình thường nhận được câu hỏi nhất chính là **Amazon GuardDuty** và **Amazon Inspector**.

Cả hai đều là công cụ đắc lực giúp bảo vệ tài nguyên trên đám mây, nhưng chúng lại giải quyết hai bài toán hoàn toàn khác nhau: phát hiện mối đe dọa theo thời gian thực (Threat Detection) và quản lý lỗ hổng bảo mật (Vulnerability Management).

Trong bài viết này, mình sẽ cùng bạn phân tích chi tiết từng dịch vụ, đặt chúng lên bàn cân so sánh và rút ra những bài học thực tế để bạn áp dụng cho hệ thống của mình nhé!

## 1. Amazon GuardDuty: "camera an ninh" theo dõi 24/7

Để dễ hình dung, mình thường so sánh GuardDuty như một chiếc camera an ninh thông minh. Nó không trực tiếp can thiệp hay sửa chữa mã nguồn của bạn, mà liên tục quan sát mọi chuyển động xung quanh ngôi nhà AWS.

**Cơ chế hoạt động:** GuardDuty phân tích thụ động các luồng dữ liệu log hệ thống như AWS CloudTrail, VPC Flow Logs, DNS Logs, EKS Audit Logs hay S3 Event Logs. Dịch vụ này ứng dụng Machine Learning, phát hiện các hành vi bất thường và kết nối với dữ liệu Threat Intelligence toàn cầu.

**Mục tiêu cốt lõi:** phát hiện kẻ tấn công hoặc mã độc ngay tại thời điểm chúng đang hoạt động (runtime/real-time).

Ví dụ thực tế từ kinh nghiệm của mình:

- cảnh báo ngay lập tức nếu IAM Access Key của bạn vô tình bị rò rỉ và đang được gọi từ một địa chỉ IP lạ ở nửa bên kia thế giới;
- phát hiện máy chủ EC2 hoặc container trên EKS bị nhiễm malware và bắt đầu âm thầm đào tiền ảo (crypto mining) hoặc kết nối tới máy chủ điều khiển của hacker;
- phát hiện các hành vi truy vấn và tải dữ liệu bất thường trên Amazon S3 hoặc Amazon RDS.

## 2. Amazon Inspector: "bác sĩ khám sức khỏe" định kỳ

Khác với GuardDuty chỉ đứng ngoài quan sát hành vi, Amazon Inspector đóng vai trò như một chuyên gia kiểm toán chủ động. Dịch vụ này sẽ nhảy vào bên trong tài nguyên của bạn để kiểm tra từng dòng cấu hình, từng gói phần mềm nhằm tìm ra điểm yếu trước khi kẻ xấu kịp lợi dụng.

**Cơ chế hoạt động:** Inspector chủ động thực hiện kiểm tra cấu hình mạng, quét các phần mềm và thư viện đã cài đặt dựa trên cơ sở dữ liệu lỗ hổng bảo mật phổ biến toàn cầu (CVE - Common Vulnerabilities and Exposures).

**Mục tiêu cốt lõi:** phát hiện các lỗ hổng tiềm ẩn trước khi sự cố xảy ra (pre-deployment/scan-time).

Ví dụ thực tế từ kinh nghiệm của mình:

- quét hệ điều hành của EC2 hoặc Container Image trên Amazon ECR để tìm các lỗ hổng thư viện nguy hiểm (như Log4j, OpenSSL,...);
- đánh giá mã nguồn và các phụ thuộc (dependencies) của hàm AWS Lambda để phát hiện điểm yếu bảo mật;
- cảnh báo các máy chủ EC2 đang vô tình mở cổng (port) ra môi trường Internet công cộng mà không có rào chắn bảo vệ.

## 3. So sánh trực quan: GuardDuty vs Inspector

Thay vì dùng bảng biểu phức tạp, mình tóm tắt những điểm khác biệt cốt lõi giữa hai dịch vụ này theo từng tiêu chí cụ thể bên dưới.

### Về bản chất

- GuardDuty là hệ thống phát hiện xâm nhập (Threat Detection / IDS).
- Inspector là hệ thống quản lý và quét lỗ hổng (Vulnerability Management).

### Về cách tiếp cận

- GuardDuty chọn cách phân tích thụ động. Nó chỉ đọc dữ liệu log mà không can thiệp trực tiếp vào tài nguyên.
- Inspector chọn cách quét chủ động. Nó trực tiếp kiểm tra sâu vào cấu hình, hệ điều hành và gói phần mềm.

### Về phạm vi bảo vệ

- GuardDuty bao phủ diện rộng toàn tài khoản: IAM, VPC, DNS, S3, RDS, EKS, Lambda,...
- Inspector tập trung sâu vào các khối lượng công việc cụ thể: đĩa EC2 (EBS), Container Image (ECR), và mã nguồn Lambda.

### Về thời điểm phát huy tác dụng

- GuardDuty hoạt động ở giai đoạn runtime. Dịch vụ phát cảnh báo ngay khi cuộc tấn công hoặc hành vi bất thường đang diễn ra.
- Inspector hoạt động ở giai đoạn static/scan-time. Dịch vụ phát hiện điểm yếu bảo mật từ trước để bạn kịp thời vá lại.

### Về góc nhìn kỹ thuật

- GuardDuty giúp bạn trả lời câu hỏi: "Hệ thống của mình có đang bị ai đó tấn công hay xâm nhập hay không?"
- Inspector giúp bạn trả lời câu hỏi: "Hệ thống của mình có đang chứa lỗ hổng nào dễ bị khai thác hay không?"

## 4. Bài học rút ra

Từ quá trình triển khai và vận hành thực tế trên AWS, mình rút ra 3 bài học quan trọng mà bạn nên bỏ túi:

### Không có giải pháp đơn lẻ nào là đủ

Bảo mật đám mây luôn tuân theo nguyên tắc "Phòng thủ chiều sâu" (Defense-in-Depth). Bạn không nên chỉ chọn 1 trong 2 dịch vụ.

- Nếu chỉ dùng Inspector: bạn vá hết lỗ hổng đã biết, nhưng vẫn có thể bị lộ IAM Key hoặc bị tấn công Zero-day mà không hay biết.
- Nếu chỉ dùng GuardDuty: bạn biết mình đang bị tấn công, nhưng hệ thống lại đầy lỗ hổng chưa vá khiến kẻ xấu dễ dàng quay lại.

### Áp dụng quy trình "phòng bệnh hơn chữa bệnh"

Hãy dùng Inspector ngay từ giai đoạn CI/CD pipeline (khi build Docker image hoặc deploy code Lambda). Việc phát hiện và sửa lỗ hổng ngay từ lúc viết code luôn tốn ít chi phí và công sức hơn rất nhiều so với việc xử lý sự cố trên production.

### Tối ưu hóa việc quản lý cảnh báo

Khi bật cả hai dịch vụ, lượng cảnh báo (findings) gửi về có thể làm bạn bị ngợp. Bài học của mình là hãy kết hợp cả GuardDuty và Inspector về một đầu mối tập trung là AWS Security Hub. Tại đây, bạn có thể dễ dàng phân loại mức độ ưu tiên và thiết lập tự động hóa gửi thông báo qua Slack/Telegram hoặc tự động vá lỗi.

Ở quy mô demo hiện tại của QuickBite, GuardDuty và Inspector **chưa được bật** cho tài khoản AWS thực tập; phần bảo mật hiện có tập trung vào IAM least-privilege, Security Group và Secrets Manager. Bật GuardDuty toàn tài khoản và Inspector cho image trên ECR là bước hợp lý tiếp theo, vì cả hai đều không yêu cầu thay đổi hạ tầng Terraform hiện tại.

## Tài liệu tham khảo

- [Amazon GuardDuty & Amazon Inspector – AWS Security](https://aws.amazon.com/vi/products/security/detection-and-response/)
