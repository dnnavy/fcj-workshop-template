---
title: "Dọn dẹp"
date: 2024-01-01
weight: 6
chapter: false
pre : " <b> 5.6. </b> "
---

### 1. Xóa Frontend Hosting (AWS Amplify)

Nên xoá giao diện trước. 
1. Mở AWS Console -> tìm dịch vụ **AWS Amplify**.
2. Chọn ứng dụng BK-Sync mà ta đã tạo.
3. Ở menu bên cạnh, bấm vào **App settings** -> **General settings**.
4. Kéo xuống dưới cùng và bấm **Delete app** để xóa.
![alt text](image.png)

### 2. Xóa hạ tầng Backend (AWS SAM)

Để tránh bị AWS tính phí, bạn bắt buộc phải gỡ bỏ toàn bộ Lambda, API Gateway, DynamoDB... đã tạo ra.

**Cách 1: Xóa bằng lệnh (Khuyên dùng)**
Mở Terminal (đang đứng trong thư mục `backend`) và chạy lệnh:
```bash
sam delete
```
Xác nhận bằng phím `y` cho các câu hỏi. CloudFormation sẽ tự động dò tìm và gỡ bỏ toàn bộ.

**Cách 2: Xóa bằng giao diện Web (Đề phòng lỗi)**
Đôi khi việc xóa bằng lệnh bị lỗi (do AWS Secrets Manager khóa Secret bảo vệ 30 ngày). Nếu bạn gặp dòng chữ báo `DELETE_FAILED` đối với resource `HmacSecretV2`, hãy làm như sau:
1. Mở AWS Console -> tìm dịch vụ **CloudFormation**.
![alt text](image-1.png)
2. Bấm vào stack `qr-attendance-backend-dev`, chọn **Delete**(hoặc **Retry delete** nếu trước đó delete thất bại).
![alt text](image-2.png)
3. Một bảng thông báo hiện ra , chọn **Force delete this entire stack**, nhấn **Delete stack**.
![alt text](image-3.png)

Vậy là hệ thống đã được dọn dẹp sạch sẽ!

