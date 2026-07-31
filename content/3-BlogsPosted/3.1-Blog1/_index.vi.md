---
title: "Blog 1"
date: 2026-07-29
weight: 1
chapter: false
pre: " <b> 3.1. </b> "
---

# Phương ngữ DSQL SQL: Amazon Aurora DSQL khác gì với single-instance PostgreSQL

* Amazon Aurora DSQL dựa trên mã nguồn mở PostgreSQL, nhưng do bản chất là cơ sở dữ liệu phân tán, dẫn đến một số khác biệt về các tính năng được hỗ trợ và hành vi. Việc hiểu rõ điểm khác biệt của Aurora DSQL và PostgreSQL tiêu chuẩn giúp giảm thiểu rủi ro, thiết kế các lược đồ tối ưu từ đầu.
* Bài viết này dành cho các kiến ​​trúc sư cơ sở dữ liệu, nhà phát triển và quản trị viên cơ sở dữ liệu (DBA) cần đánh giá Aurora DSQL hoặc làm việc với khối lượng công việc PostgreSQL trên cơ sở dữ liệu phân tán.
---
* Điểm tương đồng: có thể nói gần như là tương đồng.
    * Amazon Aurora DSQL sử dụng PostgreSQL v16 tiêu chuẩn và giao thức truyền tải v3.0+.
    * Các công cụ và thư viện phổ biến như: psql, pgjdbc, psycopg, Django, ActiveRecord, Hibernate đều có thể kết nối và hoạt động bình thường.
    * Các truy vấn SQL với giả định rằng chúng sử dụng các tính năng được hỗ trợ, sẽ trả về kết quả hoàn toàn giống nhau (cùng cách xử lý giá trị NULL, thứ tự sắp xếp, độ chính xác số học và hành vi của chuỗi).
    * Các tính năng SQL cốt lõi vẫn còn nguyên vẹn (DML tiêu chuẩn, DDL, điều khiển giao dịch, các kiểu dữ liệu cốt lõi). Nếu ứng dụng của bạn sử dụng các câu lệnh SQL tiêu chuẩn cho khối lượng công việc giao dịch, khả năng tương thích của là rất cao.
---
* Điểm khác biệt và lí do: Sự khác biệt về cú pháp và hành vi trong Aurora DSQL xuất phát từ kiến trúc phân tán, không chia sẻ tài nguyên.
    * Lưu trữ được sắp xếp theo khóa chính là sự khác biệt cơ bản nhất. PostgreSQL truyền thống sử dụng cấu trúc dữ liệu heap ,các hàng được lưu trữ trong các trang không tuần tự không liên hệ khóa chính. Trong DSQL, dữ liệu được lưu trữ và duy trì thứ tự theo khóa chính (áp dụng cho cả bảng và chỉ mục phụ được sắp xếp theo cột khóa của chúng).
    * Không phải mọi thao tác đều được đẩy xuống tầng lưu trữ. Aurora DSQL tách biệt phần tính toán và lưu trữ, đây là một trong những yếu tố then chốt giúp nó tự động mở rộng quy mô và vận hành hoàn toàn không cần máy chủ. Điều này ảnh hưởng đến phương ngữ theo hai cách cụ thể là hạn chế kiểu khóa chỉ mục (không phải mọi kiểu dữ liệu PostgreSQL đều có thể được sử dụng làm khóa của chỉ mục trong Aurora DSQL) và thao tác đẩy xuống (các phép so sánh bằng và so sánh phạm vi đơn giản trên các kiểu dữ liệu được hỗ trợ thường được đẩy xuống lớp lưu trữ. Các biểu thức phức tạp, các lệnh gọi hàm hoặc các thao tác trên các kiểu dữ liệu mà lớp lưu trữ không xử lý trực tiếp sẽ được đánh giá ở lớp tính toán sau khi truy xuất các hàng). Do sự tách biệt giữa tính toán và lưu trữ, một truy vấn có thể được trả lời hoàn toàn từ chỉ mục (mà không cần lấy hàng dữ liệu từ bảng cơ sở) sẽ tránh được một lượt truy cập bổ sung vào bộ nhớ.
    * Cơ chế kiểm soát truy cập đồng thời lạc quan: PostgreSQL sử dụng MVCC với khóa cấp hàng cho các thao tác ghi (các giao dịch ghi đồng thời nắm giữ các khóa có thể chặn lẫn nhau khi xảy ra xung đột). Aurora DSQL sử dụng cơ chế kiểm soát đồng thời lạc quan (OCC) (các giao dịch được thực thi mà không cần khóa và được kiểm tra xung đột tại thời điểm commit). Điều này không làm thay đổi cú pháp SQL, nhưng thay đổi hành vi của ngôn ngữ lập trình. Giúp hạn chế tình trạng tắc nghẽn, lỗi tuần tự hóa khi xảy ra xung đột, các giao dịch chỉ đọc không gây xung đột, mức độ cô lập tương đương với PostgreSQL Repeatable Read (không thể chọn mức độ cô lập, đây là mức cố định duy nhất mà hệ thống cung cấp).
    * DDL bất đồng bộ: Trong PostgreSQL, DDL hoạt động đồng bộ: khi lệnh CREATE TABLE trả về kết quả, bảng tồn tại. Trong Aurora DSQL, một số lệnh DDL hoạt động đồng bộ và một số thì không. Có 1 số ràng buộc về phương ngữ được phát sinh: chỉ có một câu lệnh DDL cho mỗi giao dịch; không thể kết hợp DDL và DML trong cùng một giao dịch; đối với DDL bất đồng bộ, phải xác minh thao tác DDL đã hoàn thành (bằng cách chạy lệnh SELECT * FROM sys.jobs, hoặc chờ job_id xử lý xong) trước khi thực hiện các thao tác phụ thuộc vào sự thay đổi cấu trúc (schema) đó. Quá trình đọc và ghi vẫn tiếp tục diễn ra không gián đoạn trong suốt các thao tác DDL.
    * Xác thực dựa trên IAM, không phải mật khẩu: Aurora DSQL thay thế PostgreSQL pg_hba.conf và cơ chế đăng nhập bằng tên người dùng/mật khẩu với AWS Identity and Access Management (IAM). Kết nối bằng cách sử dụng các token có thời hạn ngắn được tạo bằng AWS SDK . Điều này không thay đổi ngôn ngữ SQL, nhưng thay đổi mọi chuỗi kết nối và luồng xác thực trong ứng dụng.
    * Các tính năng không được hỗ trợ ảnh hưởng đến phương ngữ: Không phải mọi tính năng của PostgreSQL đều tương đương trực tiếp trong Aurora DSQL.
---
* Kết luận: Amazon Aurora DSQL sử dụng trình phân tích cú pháp, trình lập kế hoạch và hệ thống kiểu của PostgreSQL, do đó ngôn ngữ SQL về cơ bản là tương thích. Trọng tâm là tìm hiểu Aurora DSQL giống và khác như thế nào.
---
Tài liệu tham khảo:
https://aws.amazon.com/...dsql-sql-dialect-how-amazon.../
--- 
Link bài post:
https://web.facebook.com/groups/awsstudygroupfcj/permalink/2227753051322988/?rdid=4BxzLitflB0OFY8E#
