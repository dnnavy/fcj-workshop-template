---
title: "Introduction"
date: 2024-01-01
weight: 1
chapter: false
pre : " <b> 5.1. </b> "
---

### 1. Context & Problem

In higher education environments, especially in large classes with 50 to 100+ students, traditional roll-call attendance consumes a significant amount of time, disrupts the teaching process, and is prone to proxy attendance.

**BK-Sync System** was created to solve this problem. The target customers are:
- **Universities/Educational Institutions:** Need accurate attendance tracking and fraud prevention.
- **Lecturers/Teachers:** Need to save time on attendance to focus on teaching.
- **Students:** Need a fast and convenient check-in process using their mobile devices.

### 2. Solution Idea

Our solution is to build a **Real-time QR Attendance** system on the Cloud.
- The lecturer opens an attendance session on the website. A QR code is projected on the screen and continuously refreshes every few seconds to prevent students from taking photos and sending them to absent friends.
- Students use their smartphones to scan the QR code and confirm their presence.

### 3. Specific Goals (Outputs)

1. **Dashboard Interface (Frontend):** 
   - For Teachers: Create classes, open sessions, display rotating QR codes, view statistics, and export attendance data to Excel (the file can indicate whether students are sharing the same device).
   - For Students: View personal attendance history.
2. **Serverless API System (Backend):**
   - Handle user authentication, QR code generation, token validation, and attendance recording.
3. **Alerting & Monitoring:**
   - Monitor system health and send alerts via SNS Topic if the system encounters issues (e.g., continuous check-in function errors).

### 4. Architecture Diagram

The system is designed with a **100% Serverless** architecture on AWS, optimizing costs and enabling automatic scaling.

![System Architecture Diagram](/images/5-Workshop/diagram.png)


