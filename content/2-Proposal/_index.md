---
title: "Proposal"
date: 2026-07-29
weight: 2
chapter: false
pre: " <b> 2. </b> "
---

## 2.3. Proposal

### BK-Sync - Smart Attendance System using Dynamic QR codes
**BK-Sync** is a smart attendance system using dynamic QR codes (Real-time QR Attendance) built on the AWS cloud platform. The system leverages the power of Serverless architecture to handle thousands of concurrent student access at the beginning of classes without maintaining continuous servers.

### Objectives
- Save 80% of class time spent on roll-call for lecturers.
- Eliminate proxy attendance and fraud.
- Provide a smooth and convenient experience for students via their mobile devices.

### Problem Statement
In universities with large class sizes (50-150 students), traditional roll-call methods consume too much time and disrupt lectures. 
Using static QR codes for attendance makes it easy for students to take photos and share them with absent friends. BK-Sync solves this problem by generating dynamic QR Codes (auto-refreshing every few seconds) and expiring the token immediately after the session ends.

### Solution Architecture

The system is designed with a **100% Serverless** model, taking full advantage of AWS managed services:

![Solution Architecture Diagram](/images/dia.jpg)

| AWS Service | Purpose / Role | Reason for Selection |
|---|---|---|
| **Amazon Cognito** | User Identity Management (Authentication & Authorization for Admin, Teacher, Student) | Convenient, built-in login interface, secure |
| **Amazon API Gateway** | Acts as the communication gateway between Frontend and Backend | Good load handling, DDoS protection, easy integration with Lambda |
| **AWS Lambda** | Processes business logic (Core logic) | Serverless, no server management required, pay-per-request only |
| **Amazon DynamoDB** | NoSQL database for data storage | Millisecond read/write speeds, infinite scalability |
| **AWS Secrets Manager** | Stores HMAC secret key for QR code encryption | High security, prevents secrets from leaking into source code |
| **AWS Amplify Hosting** | Automatic Frontend deployment | Smooth CI/CD, free SSL certificate support |

### Timeline (8 Weeks)
- **Week 1-2:** Requirement analysis, system architecture design (Use Cases, Sequence Diagrams), and repository setup.
- **Week 3-4-5-6:** Backend system development (AWS SAM, Lambda, API Gateway, DynamoDB).
- **Week 5-6-7:** Frontend interface development (React/Vite) and API integration.
- **Week 7-8:** Beta testing and bug fixing.
- **Week 8:** Documentation, security hardening, and project presentation.

### Budget
Thanks to the Serverless architecture, the system mostly operates on a **Pay-as-you-go** model. Most services (Lambda, DynamoDB) fall completely within the **AWS Free Tier**. However, there are a few minor costs to consider:
- **AWS Secrets Manager:** Storage fee is ~$0.40/month per secret.
- **AWS Amplify Hosting:** Free hosting for small traffic, but Build Time may incur costs ($0.01/minute) if the monthly free tier is exceeded.
- **Overall:** For a workshop/lab scale, the estimated operational cost is well under **$1/month**.

### Risks & Mitigations
- **Risk:** Students using the same device to scan QR codes for multiple accounts.
- **Mitigation:** The backend tracks user sessions and can export attendance data to an Excel report, thereby warning the lecturer if it detects multiple accounts checking in from the same physical device.