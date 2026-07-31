---
title: "Đóng góp & Trải nghiệm"
date: 2024-01-01
weight: 7
chapter: false
pre : " <b> 5.7. </b> "
---


### 1. Khó khăn gặp phải & Cách giải quyết

**Khó khăn 1: Xung đột tài nguyên do Hard-code Name**
- **Sự cố:** Bị lỗi đụng độ tên khi cố gắng triển khai nhiều môi trường (VD: `develop` và `local`) trên cùng 1 tài khoản AWS (do trùng tên `TopicName` và Secrets Manager `Name`).
- **Giải quyết:** Gỡ bỏ các cấu hình tên cứng, thay bằng biến nội suy `${AWS::StackName}` hoặc để AWS tự động sinh ID ngẫu nhiên, giúp các môi trường hoàn toàn cô lập và có thể scale không giới hạn.

**Khó khăn 2: Policy Template gây lỗi AccessDenied ngầm**
- **Sự cố:** AWS SAM cung cấp sẵn một template tên là `AWSSecretsManagerGetSecretValuePolicy` để cấp quyền cho Lambda đọc khóa HMAC. Tuy nhiên, khi deploy, Lambda vẫn bị lỗi 500 do `AccessDeniedException` và `ResourceNotFoundException`.
- **Giải quyết:** Trải qua quá trình debug log API, phát hiện ra Template của SAM xử lý chuỗi ARN chưa hoàn hảo khi Secret bị tạo lại. Đã quyết định đập bỏ Template và viết lại bằng **Inline IAM Policy** nguyên thủy của CloudFormation (khối `Statement` với `Resource: !Ref HmacSecretV2`). Việc đổi Logical ID sang `HmacSecretV2` cũng giúp CloudFormation ép tạo tài nguyên mới, đồng bộ lại ARN chuẩn xác nhất. 

Những trải nghiệm này đã mang lại bài học vô giá về sự tỉ mỉ khi vận hành hạ tầng Serverless và nguyên tắc Đặc quyền Tối thiểu trên AWS.

### 2. Đóng góp cá nhân

Trong quá trình thực hiện dự án, tôi đã trực tiếp tham gia hiện thực hóa cả hai mảng Frontend và Backend. Việc tự tay kết nối các dịch vụ Serverless ở phía sau với giao diện người dùng giúp tôi nắm bắt bao quát toàn bộ luồng đi của dữ liệu. Nhờ có cái nhìn tổng thể này, tôi cũng tham gia theo dõi tiến độ kỹ thuật chung, hỗ trợ gỡ lỗi và định hướng cách ráp nối các module lại với nhau sao cho hệ thống vận hành trơn tru và đồng nhất nhất có thể.
