---
title: "Blog 1 - Tìm hiểu AWS Secrets Manager"
date: 2026-07-30
weight: 1
chapter: false
pre: " <b> 3.1. </b> "
---
# Tìm hiểu AWS Secrets Manager – Giải pháp bảo mật thông tin cấu hình nhạy cảm trên Cloud

**Trạng thái nội dung:** Hoàn thành

Trong quá trình học và làm việc với các ứng dụng Web trên Cloud, thói quen ban đầu của mình (và có lẽ của rất nhiều bạn mới bắt đầu) là lưu các thông tin nhạy cảm như `DATABASE_URL`, `JWT_SECRET_KEY`, hay API Keys trực tiếp trong file môi trường `.env`.

Tuy nhiên, khi đưa ứng dụng lên máy chủ EC2 hoặc làm việc nhóm, việc lưu trữ mật khẩu ở dạng plain text (văn bản thuần) tiềm ẩn rất nhiều rủi ro rò rỉ dữ liệu — đặc biệt là nguy cơ vô tình commit file chứa secret lên GitHub repository.

Khi tìm hiểu sâu hơn về các giải pháp bảo mật trên AWS, mình biết đến **AWS Secrets Manager**. Đây là dịch vụ giúp quản lý, lưu trữ an toàn và tự động xoay vòng (rotate) các thông tin nhạy cảm mà không cần phải hardcode vào mã nguồn hay lưu ở các file cấu hình tĩnh.

## AWS Secrets Manager hoạt động như thế nào?

Ý tưởng của Secrets Manager rất trực quan và an toàn.

Thay vì ứng dụng đọc biến môi trường từ file `.env` lưu trên đĩa cứng máy chủ, ứng dụng sẽ thực hiện một lệnh gọi API bảo mật tới AWS Secrets Manager (thường qua SDK như `boto3` trong Python, `aws-sdk` trong Node.js) để lấy dữ liệu về memory ngay khi khởi chạy.

Toàn bộ thông tin lưu trong Secrets Manager đều được mã hóa bằng dịch vụ **AWS KMS (Key Management Service)**. Bên cạnh đó, chúng ta có thể phân quyền chi tiết thông qua IAM Role, chỉ cho phép đúng máy chủ hoặc ứng dụng được chỉ định mới có quyền giải mã và đọc secret đó.

Ví dụ, thay vì lưu chuỗi kết nối Database cố định trong code:

```text
postgresql://admin:MyHardcodedPassword123@db-instance:5432/appdb
```

Ứng dụng sẽ gửi yêu cầu lên Secrets Manager, nhận về chuỗi JSON đã giải mã chứa `username` và `password`, sau đó mới tiến hành khởi tạo kết nối cơ sở dữ liệu.

## Thử cấu hình và sử dụng Secrets Manager

Để hiểu rõ hơn luồng vận hành, mình đã thử tạo và lấy dữ liệu từ AWS Secrets Manager theo các bước sau:

### Bước 1: Tạo secret trên AWS Console

1. Truy cập AWS Management Console và tìm dịch vụ AWS Secrets Manager.
2. Chọn **Store a new secret**.
3. Chọn loại secret (ví dụ: *Credentials for Amazon RDS database* hoặc *Other type of secret* nếu là API Key/Token).
4. Nhập các cặp Key/Value nhạy cảm, ví dụ:
   - `DB_HOST`: `my-db-instance.c123456789.us-east-1.rds.amazonaws.com`
   - `DB_PASSWORD`: `SecurePassword2026!`
   - `API_KEY`: `secret-api-key-xyz`
5. Đặt tên cho Secret (ví dụ: `prod/backend/config`) và nhấn tạo.

### Bước 2: Phân quyền IAM Role

Cấp quyền `secretsmanager:GetSecretValue` cho IAM Role gắn liền với máy chủ EC2 hoặc dịch vụ chạy ứng dụng. Nhờ sử dụng IAM Role, ứng dụng không cần phải lưu bất kỳ AWS Access Key / Secret Key nào dưới máy chủ nữa.

### Bước 3: Truy xuất secret từ ứng dụng

Trong code ứng dụng, thay vì đọc biến môi trường tĩnh, mình sử dụng AWS SDK để truy xuất dữ liệu theo luồng:

```text
Khởi chạy App → Gọi Secrets Manager API → Giải mã qua KMS → Tải Config vào Memory
```

{{< report-image src="images/blog/aws-secrets-manager.png" alt="Bài viết Tìm hiểu AWS Secrets Manager đăng trong nhóm AWS Study Group VN" caption="Bài viết đang chờ duyệt (Pending) trong nhóm Facebook AWS Study Group VN." >}}

## Một vài điểm mình thấy hữu ích

Sau khi tìm hiểu và trải nghiệm thử, mình thấy AWS Secrets Manager có một số ưu điểm rất giá trị:

- **Tuyệt đối an toàn cho mã nguồn:** loại bỏ hoàn toàn rủi ro lỡ tay đẩy mật khẩu, connection string hay API Keys lên GitHub.
- **Tự động xoay vòng mật khẩu (Automatic Rotation):** có thể cấu hình kết hợp với AWS Lambda để Secrets Manager tự động đổi mật khẩu Database định kỳ (ví dụ mỗi 30 hoặc 90 ngày) hoàn toàn tự động.
- **Tích hợp chặt chẽ với IAM:** phân quyền truy cập cực kỳ chuẩn xác theo nguyên tắc "Least Privilege" (chỉ cấp vừa đủ quyền).
- **Quản lý tập trung:** khi cần thay đổi mật khẩu Database hay Secret Key, chỉ cần cập nhật tại một nơi duy nhất trên AWS Console mà không cần SSH vào từng server để chỉnh sửa file cấu hình.

## Một số điểm cần lưu ý

Bên cạnh những ưu điểm trên, mình cũng rút ra một vài điều cần cân nhắc khi sử dụng:

- **Chi phí dịch vụ:** AWS Secrets Manager có tính phí dựa trên số lượng Secret lưu trữ (~0.40$ / secret / tháng) và số lượng lệnh gọi API. Do đó, kinh nghiệm là nên gộp các biến cấu hình liên quan vào chung một JSON Secret thay vì tạo mỗi biến một Secret riêng lẻ để tiết kiệm chi phí.
- **Độ trễ API (Latency):** việc gọi API sang Secrets Manager mỗi khi có request có thể làm tăng độ trễ của ứng dụng. Giải pháp tối ưu là tải Secret một lần khi ứng dụng vừa khởi động (Startup) và lưu tạm vào memory (caching), thay vì gọi API liên tục mỗi lần xử lý logic.

## Khi nào nên sử dụng?

Theo góc nhìn của mình, AWS Secrets Manager rất phù hợp khi:

- Xây dựng các ứng dụng trên môi trường Production đòi hỏi tiêu chuẩn bảo mật cao.
- Cần quản lý thông tin đăng nhập vào các cơ sở dữ liệu quan trọng (RDS, DocumentDB,...).
- Cần cơ chế tự động đổi mật khẩu định kỳ để tuân thủ các chính sách an toàn thông tin.
- Hệ thống gồm nhiều microservices cùng chia sẻ và khai thác chung các chuỗi cấu hình bảo mật.

Đây cũng chính là lý do QuickBite dùng Secrets Manager cho `DATABASE_URL` và JWT secret trong Terraform data module: mọi EC2 instance trong Auto Scaling Group đều đọc chung một secret duy nhất qua IAM role của mình, thay vì mỗi instance tự giữ một bản `.env` khác nhau.

## Kết luận

AWS Secrets Manager là một dịch vụ rất thực tế và cần thiết cho bất kỳ ai đang học cũng như triển khai ứng dụng trên nền tảng AWS. Việc chuyển từ tư duy lưu file `.env` truyền thống sang quản lý Secret tập trung trên Cloud không chỉ giúp mã nguồn sạch sẽ, chuyên nghiệp hơn mà còn giúp bảo vệ hệ thống trước những nguy cơ rò rỉ an ninh mạng phổ biến.

## Nguồn tham khảo

- [AWS Documentation – AWS Secrets Manager Concepts](https://docs.aws.amazon.com/secretsmanager/latest/userguide/developerguide-concepts.html)
- [AWS Code Examples – Retrieve Secret Value using Python (boto3)](https://docs.aws.amazon.com/secretsmanager/latest/userguide/snippets.html)
