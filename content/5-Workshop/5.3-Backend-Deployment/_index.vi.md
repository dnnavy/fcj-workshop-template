---
title: "Triển khai Backend"
date: 2024-01-01
weight: 3
chapter: false
pre : " <b> 5.3. </b> "
---

### 1. Tải Mã nguồn

Link mã nguồn:      
https://github.com/kentdoan/qr-attendance

Mở Terminal và clone kho chứa mã nguồn:
```bash
git clone https://github.com/kentdoan/qr-attendance.git
cd qr-attendance/backend
```

### 2. Biên dịch (Build)

Sử dụng `npm install` để tải thư viện trước, sau đó dùng AWS SAM để đóng gói code Lambda bằng ESBuild:
```bash
npm install
sam build
```

![alt text](image.png)
![alt text](image-1.png)

### 3. Triển khai (Deploy)

Trước khi deploy, hãy đảm bảo bạn đã đăng nhập và liên kết Terminal với tài khoản AWS:
```bash
aws login
```
![alt text](image-2.png)
![alt text](image-3.png)
![alt text](image-4.png)

Sau đó, chạy lệnh sau để triển khai hạ tầng lên AWS (CloudFormation sẽ tự động tạo Lambda, API Gateway, DynamoDB...):
```bash
sam deploy --guided
```

Hệ thống sẽ hỏi bạn một số cấu hình. Hãy trả lời như sau:
- **Stack Name**: `qr-attendance-backend-dev`
- **AWS Region**: `ap-southeast-1`
- **Confirm changes before deploy**: `y`
- **Allow SAM CLI IAM role creation**: `y`
- **Disable rollback**: `n`
- **Save arguments to configuration file**: `y`
- **SAM configuration file**: Nhấn `Enter` để mặc định là `samconfig.toml`
- **SAM configuration environment**: Nhấn `Enter` để mặc định là `default`
- Deploy this changeset? : y

Chờ khoảng 2-3 phút, hệ thống sẽ triển khai hoàn tất.

![alt text](image-5.png)

### 4. Lấy thông số cấu hình

Khi hoàn thành, Terminal sẽ in ra bảng **Outputs**. Bạn **BẮT BUỘC HÃY LƯU LẠI** 3 giá trị sau để cấu hình Frontend ở bước tiếp theo:
- `ApiEndpoint` (URL của API Gateway)
- `UserPoolId` (ID của Cognito User Pool)
- `UserPoolClientId` (ID của Cognito App Client)

---

### 5. Khởi tạo Tài khoản Admin

Để có thể đăng nhập và tạo lớp học, bạn cần có một tài khoản Admin. Chúng tôi đã viết sẵn một script tự động kết nối với AWS để tạo tài khoản cho bạn.

Chạy lệnh sau trong Terminal (đảm bảo bạn đang đứng ở thư mục `qr-attendance/backend`):
```bash
cd ../scripts
chmod +x create_admin.sh
./create_admin.sh
```

Hệ thống sẽ tự động tìm kiếm kết nối tới AWS và yêu cầu bạn nhập Email, Mật khẩu và Họ tên.

![alt text](image-6.png)

Khi màn hình báo "Thành công!", bạn đã có thể dùng tài khoản này để đăng nhập vào trang web ở phần sau.
