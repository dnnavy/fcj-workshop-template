---
title: "UI & Testing"
date: 2024-01-01
weight: 5
chapter: false
pre : " <b> 5.5. </b> "
---

### 1. Registration/Login UI & Admin

**Registration/Login**

![alt text](image-4.png)
![alt text](image-5.png)

**Admin Dashboard**

![alt text](image-7.png)


### 2. Testing

**Teacher creates an attendance session**
- Log in with the Teacher account.
- Click **Add Course** (Thêm môn học) to create a new course.
![alt text](image-1.png)
- In the course details, click **Create Session** (Tạo phiên).
- The screen displays a QR code. Notice that this QR code **continuously changes** 
every few seconds to prevent proxy attendance!
![alt text](image.png)
- Students who successfully scan the QR code will appear in the **Attendance List**
on the right. This list can be exported to an Excel file.

**Student scans QR (Check-in)**
- Use your phone to access the website and log in with the Student account.
- Click **Start Scanning** (Bắt đầu quét) to use the camera to scan the QR code.
- A success message appears.
![alt text](image-3.png)

### 3. View Logs and Metrics (Logging & Monitoring)

To ensure smooth operation, we will examine the logs.

**View Lambda Logs:**
1. Open AWS Console -> **CloudWatch** -> **Log Management**.
![alt text](image-8.png)
2. Find the log group for `/aws/lambda/qr-attendance-backend-dev-CheckinFunction...`
3. You will see log entries recording successful student check-ins.
![alt text](image-9.png)

**Check Metrics:**
1. Open AWS Console -> **CloudWatch** -> **Metrics** -> **Classic metrics** 
2. Here you can view various infrastructure-related metrics.
![alt text](image-10.png)
