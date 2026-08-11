---
title: "Các bài blogs đã đăng"
date: 2024-01-01
weight: 3
chapter: false
pre: " <b> 3. </b> "
---


###  [Blog 1 - Phương ngữ DSQL SQL: Amazon Aurora DSQL khác gì với single-instance PostgreSQL](3.1-Blog1/)
Blog này giới thiệu bài viết phân tích chuyên sâu về phương ngữ SQL của Amazon Aurora DSQL và sự khác biệt cốt lõi so với PostgreSQL đơn thể (single-instance). Mặc dù Aurora DSQL giữ trọn khả năng tương thích cao với chuẩn PostgreSQL v16, kiến trúc phân tán shared-nothing và cơ chế tách biệt tính toán - lưu trữ đã mang lại những thay đổi quan trọng về lưu trữ dựa trên khóa chính, cơ chế kiểm soát đồng thời lạc quan (OCC), DDL bất đồng bộ cũng như xác thực qua AWS IAM. Đây là tài liệu tham khảo giá trị giúp các kiến trúc sư và nhà phát triển thiết kế tối ưu hệ thống và giảm thiểu rủi ro khi làm việc với cơ sở dữ liệu phân tán hoàn toàn serverless.

###  [Blog 2 - AWS SAM là gì? Tại sao AWS SAM không được xem là một dịch vụ Serverless của AWS?](3.2-Blog2/)
Blog này chia sẻ trải nghiệm thực tế về hành trình làm quen với kiến trúc AWS Serverless và cách lựa chọn bộ dịch vụ phù hợp để xây dựng workshop. Bài viết làm rõ những hiểu lầm phổ biến về khái niệm "không máy chủ", tư duy xử lý theo sự kiện (event-driven), cùng vai trò phối hợp chặt chẽ của bộ khung dịch vụ cốt lõi bao gồm AWS Lambda, API Gateway, DynamoDB (với bài học về Access Pattern & GSI) và Amazon Cognito. Đây là góc nhìn tổng quan và thực tế giúp bạn hình dung bức tranh toàn cảnh để thiết kế một hệ thống Serverless hoàn chỉnh, tối ưu chi phí và dễ dàng mở rộng.

###  [Blog 3 - AWS SAM là gì? Tại sao AWS SAM không được xem là một dịch vụ Serverless của AWS?](3.3-Blog3/)
Blog này giải thích bản chất của AWS Serverless Application Model (AWS SAM) và lý do tại sao bộ công cụ phổ biến này lại không được xếp vào nhóm "dịch vụ Serverless" của AWS. Qua bài viết, bạn sẽ hiểu rõ tư duy Hạ tầng dưới dạng mã nguồn (Infrastructure as Code - IaC), vai trò "bản thiết kế" của tệp template.yaml, các lệnh CLI quan trọng trong quá trình phát triển (sam init, build, local, deploy), cùng sự khác biệt cốt lõi giữa một khung phát triển (development framework) và một dịch vụ thực thi thời gian thực (runtime service).