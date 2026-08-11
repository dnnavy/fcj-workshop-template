---
title: "Bản đề xuất"
date: 2026-07-31
weight: 2
chapter: false
pre: " <b> 2. </b> "
---

## BK-Sync - Hệ thống điểm danh thông minh bằng mã QR động 

### Tổng quan dự án
**BK-Sync** là hệ thống điểm danh thông minh bằng mã QR động được xây dựng trên nền tảng điện toán đám mây AWS. Hệ thống tận dụng sức mạnh của kiến trúc Serverless để đảm bảo khả năng xử lý hàng ngàn sinh viên truy cập đồng thời vào đầu giờ học mà không cần phải duy trì máy chủ liên tục.

### Mục tiêu
- Tiết kiệm 80% thời gian điểm danh trên lớp cho giảng viên.
- Chấm dứt tình trạng gian lận, điểm danh hộ.
- Cung cấp trải nghiệm mượt mà, tiện lợi cho sinh viên thông qua thiết bị di động cá nhân.

### Vấn đề cần giải quyết
Tại các trường đại học với quy mô lớp học đông (50-150 sinh viên), phương pháp điểm danh gọi tên truyền thống tiêu tốn quá nhiều thời gian và làm gián đoạn bài giảng. 
Sử dụng mã QR tĩnh để điểm danh thì dễ bị sinh viên chụp ảnh và gửi cho bạn bè ở nhà quét hộ. BK-Sync giải quyết bài toán này bằng cách sinh ra QR Code động (tự động làm mới mỗi vài giây) và vô hiệu hóa mã ngay sau khi phiên điểm danh kết thúc.

### Kiến trúc giải pháp

Hệ thống được thiết kế theo mô hình **Serverless 100%**, tận dụng tối đa các dịch vụ managed của AWS:

![Sơ đồ kiến trúc giải pháp](/images/2-Proposal/platform_architecture.jpeg)

| Dịch vụ AWS | Mục đích / Vai trò | Lý do lựa chọn |
|---|---|---|
| **Amazon Cognito** | Quản lý danh tính người dùng (Xác thực & Phân quyền Admin, Teacher, Student) | Tiện lợi, có sẵn giao diện đăng nhập, an toàn |
| **Amazon API Gateway** | Đóng vai trò là cửa ngõ giao tiếp giữa Frontend và Backend | Chịu tải tốt, chống DDoS, dễ tích hợp với Lambda |
| **AWS Lambda** | Xử lý logic nghiệp vụ (Core logic) | Serverless, không cần quản lý máy chủ, chỉ trả tiền khi code chạy (Pay-per-request) |
| **Amazon DynamoDB** | Cơ sở dữ liệu NoSQL lưu trữ thông tin | Tốc độ đọc/ghi tính bằng mili-giây, khả năng scale vô hạn |
| **AWS Secrets Manager** | Lưu trữ khóa bí mật HMAC để mã hóa QR code | Bảo mật cao, không lộ secret vào source code |
| **AWS Amplify Hosting** | Triển khai Frontend tự động | CI/CD mượt mà, hỗ trợ chứng chỉ SSL miễn phí |

### Timeline (8 tuần)
- **Tuần 1-2:** Khảo sát yêu cầu, thiết kế kiến trúc hệ thống (Sơ đồ Use Case, Sequence Diagram) và setup kho lưu trữ (GitHub).
- **Tuần 3-4:** Phát triển hệ thống Backend (AWS SAM, Lambda, API Gateway, DynamoDB).
- **Tuần 5-6:** Xây dựng giao diện Frontend (React/Vite) và tích hợp API.
- **Tuần 7:** Triển khai thử nghiệm (Beta testing) và sửa lỗi (Bug fixing).
- **Tuần 8:** Viết tài liệu, tinh chỉnh bảo mật và báo cáo dự án.

### Ngân sách 
Nhờ sử dụng kiến trúc Serverless, hệ thống vận hành chủ yếu theo mô hình **Pay-as-you-go** (dùng bao nhiêu trả bấy nhiêu). Đa số các dịch vụ (Lambda, DynamoDB) nằm trong gói **AWS Free Tier**. Tuy nhiên, có một số chi phí nhỏ cần lưu ý:
- **AWS Secrets Manager:** Phí lưu trữ Secret là ~$0.40/tháng cho mỗi khóa.
- **AWS Amplify Hosting:** Miễn phí hosting với lưu lượng nhỏ, nhưng có thể bị tính phí Build Time ($0.01/phút) nếu vượt quá số phút miễn phí hàng tháng.
- **Tổng quan:** Ở quy mô đồ án/thực hành, chi phí vận hành ước tính chưa tới **$1/tháng**.

### Rủi ro 
- **Rủi ro:** Sinh viên sử dụng chung một thiết bị để quét mã QR cho nhiều tài khoản khác nhau.
- **Giải pháp:** Hệ thống Backend có lưu vết người dùng và có khả năng xuất dữ liệu điểm danh ra file Excel, qua đó cảnh báo cho giảng viên biết nếu phát hiện nhiều tài khoản điểm danh chung trên cùng một thiết bị.