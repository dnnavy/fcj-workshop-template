---
title: "Đóng góp & Trải nghiệm"
date: 2024-01-01
weight: 7
chapter: false
pre : " <b> 5.7. </b> "
---


## 1. Khó khăn gặp phải & Cách giải quyết

**Khó khăn 1: Xung đột tài nguyên do Hard-code Name**
- **Sự cố:** Bị lỗi đụng độ tên khi cố gắng triển khai nhiều môi trường (VD: `develop` và `local`) trên cùng 1 tài khoản AWS (do trùng tên `TopicName` và Secrets Manager `Name`).
- **Giải quyết:** Gỡ bỏ các cấu hình tên cứng, thay bằng biến nội suy `${AWS::StackName}` hoặc để AWS tự động sinh ID ngẫu nhiên, giúp các môi trường hoàn toàn cô lập và có thể scale không giới hạn.

**Khó khăn 2: Policy Template gây lỗi AccessDenied ngầm**
- **Sự cố:** AWS SAM cung cấp sẵn một template tên là `AWSSecretsManagerGetSecretValuePolicy` để cấp quyền cho Lambda đọc khóa HMAC. Tuy nhiên, khi deploy, Lambda vẫn bị lỗi 500 do `AccessDeniedException` và `ResourceNotFoundException`.
- **Giải quyết:** Trải qua quá trình debug log API, phát hiện ra Template của SAM xử lý chuỗi ARN chưa hoàn hảo khi Secret bị tạo lại. Đã quyết định đập bỏ Template và viết lại bằng **Inline IAM Policy** nguyên thủy của CloudFormation (khối `Statement` với `Resource: !Ref HmacSecretV2`). Việc đổi Logical ID sang `HmacSecretV2` cũng giúp CloudFormation ép tạo tài nguyên mới, đồng bộ lại ARN chuẩn xác nhất. 

Những trải nghiệm này đã mang lại bài học vô giá về sự tỉ mỉ khi vận hành hạ tầng Serverless và nguyên tắc Đặc quyền Tối thiểu trên AWS.

### 2. Đóng góp cá nhân

Trong quá trình thực hiện dự án, tôi đã trực tiếp tham gia hiện thực hóa cả mảng Frontend ở
giai đoạn sau và mảng tìm hiểu để phát triển kiểm thử Cloud và FinOps ở giai đoạn đầu. Nhờ
đó mà tôi đã được tìm hiểu và biết thêm nhiều về những kiến thức có thể gọi là hoàn toàn mới
với tôi về Cloud và FinOps. Ngoài ra vì trực tiếp làm mảng frontend song song với kiểm thử
ứng dụng giúp tôi có góc nhìn toàn diện về hệ thống và có góc nhìn song song ở cả góc độ kiểm
thử lẫn phát triển, giúp tôi dễ dàng đặt mình vào vị trí của người dùng cuối để đề xuất các giải
pháp kỹ thuật tối ưu.

