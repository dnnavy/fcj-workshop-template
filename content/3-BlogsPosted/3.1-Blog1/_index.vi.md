---
title: "Blog 1"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 3.1. </b> "
---

# Phương ngữ DSQL SQL: Amazon Aurora DSQL khác gì với single-instance PostgreSQL

Amazon Aurora DSQL dựa trên mã nguồn mở PostgreSQL, nhưng do bản chất là cơ sở dữ liệu phân tán, dẫn đến một số khác biệt về các tính năng được hỗ trợ và hành vi. Việc hiểu rõ điểm khác biệt của Aurora DSQL và PostgreSQL tiêu chuẩn giúp giảm thiểu rủi ro, thiết kế các lược đồ tối ưu từ đầu.

Bài viết này dành cho các kiến trúc sư cơ sở dữ liệu, nhà phát triển và quản trị viên cơ sở dữ liệu (DBA) cần đánh giá Aurora DSQL hoặc làm việc với khối lượng công việc PostgreSQL trên cơ sở dữ liệu phân tán.

---

### Điểm tương đồng

Amazon Aurora DSQL và PostgreSQL tiêu chuẩn gần như tương đồng trong hầu hết các tác vụ cơ bản:

* **Phiên bản & Giao thức:** Sử dụng PostgreSQL v16 tiêu chuẩn và giao thức truyền tải v3.0+.
* **Công cụ hỗ trợ:** Các công cụ và thư viện phổ biến như `psql`, `pgjdbc`, `psycopg`, Django, ActiveRecord, Hibernate đều có thể kết nối và hoạt động bình thường.
* **Kết quả truy vấn:** Các truy vấn SQL (khi sử dụng tính năng được hỗ trợ) trả về kết quả hoàn toàn giống nhau về cách xử lý giá trị `NULL`, thứ tự sắp xếp, độ chính xác số học và hành vi của chuỗi.
* **Tính năng SQL cốt lõi:** DML tiêu chuẩn, DDL, điều khiển giao dịch và các kiểu dữ liệu cốt lõi vẫn được giữ nguyên. Ứng dụng sử dụng câu lệnh SQL tiêu chuẩn sẽ có độ tương thích rất cao.

---

### Điểm khác biệt và lý do

Sự khác biệt về cú pháp và hành vi trong Aurora DSQL xuất phát từ kiến trúc phân tán, không chia sẻ tài nguyên (shared-nothing):

* **Lưu trữ sắp xếp theo khóa chính:** PostgreSQL truyền thống dùng cấu trúc heap (các hàng lưu trong trang không tuần tự). DSQL lưu trữ và duy trì thứ tự theo khóa chính cho cả bảng và chỉ mục phụ.
* **Xử lý tách biệt Tính toán & Lưu trữ:** 
  * *Hạn chế kiểu khóa chỉ mục:* Không phải mọi kiểu dữ liệu PostgreSQL đều làm khóa chỉ mục được trong DSQL.
  * *Thao tác đẩy xuống (Pushdown):* Phép so sánh bằng/phạm vi đơn giản được đẩy xuống lớp lưu trữ. Các biểu thức phức tạp hoặc hàm sẽ đánh giá tại lớp tính toán.
  * *Index-only scan:* Truy vấn trả lời hoàn toàn từ chỉ mục sẽ tránh được lượt truy cập bổ sung vào bộ nhớ.
* **Cơ chế Kiểm soát Đồng thời Lạc quan (OCC):** Thay vì dùng MVCC với khóa cấp hàng (dễ gây nghẽn/chờ khóa), DSQL dùng OCC (xác thực xung đột khi commit). Điều này không đổi cú pháp SQL nhưng giảm tắc nghẽn giao dịch. Mức cô lập cố định là `Repeatable Read`.
* **DDL Bất đồng bộ:** Một số lệnh DDL trong DSQL diễn ra bất đồng bộ. Bắt buộc chỉ có một câu lệnh DDL mỗi giao dịch, không kết hợp DDL và DML chung. Phải xác minh DDL hoàn thành qua `sys.jobs` trước khi thực hiện thao tác phụ thuộc.
* **Xác thực dựa trên IAM:** Thay thế `pg_hba.conf` và user/password bằng AWS IAM với token ngắn hạn.
* **Tính năng không hỗ trợ:** Một số tính năng đặc thù của PostgreSQL đơn lẻ chưa có bản tương đương trực tiếp trên DSQL.

---

### Kết luận

Amazon Aurora DSQL sử dụng trình phân tích cú pháp, trình lập kế hoạch và hệ thống kiểu của PostgreSQL nên về cơ bản hoàn toàn tương thích. Trọng tâm thiết kế là hiểu rõ các điểm tối ưu hóa của kiến trúc phân tán để khai thác hiệu quả.

---

### Tài liệu tham khảo

* [Amazon Aurora DSQL SQL Dialect Documentation](https://docs.aws.amazon.com/aurora-dsql/latest/userguide/what-is-aurora-dsql.html)
* [SQL feature compatibility in Aurora DSQL](https://docs.aws.amazon.com/aurora-dsql/latest/userguide/working-with-postgresql-compatibility.html)
* [Aurora DSQL and PostgreSQL](https://docs.aws.amazon.com/aurora-dsql/latest/userguide/working-with.html)
* [What is Amazon Aurora DSQL](https://docs.aws.amazon.com/aurora-dsql/latest/userguide/what-is-aurora-dsql.html)

---

**Link bài post:** [Facebook Group Post](https://web.facebook.com/groups/awsstudygroupfcj/permalink/2227753051322988/)