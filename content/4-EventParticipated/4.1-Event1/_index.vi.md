---
title: "Event 1"
date: 2026-07-31
weight: 1
chapter: false
pre: " <b> 4.1. </b> "
---

# Bài thu hoạch "AWS Quiz Battle - Buổi khởi động First Cloud AI Journey"

### Thông tin sự kiện

&emsp;**Tên sự kiện:** AWS Quiz Battle - Buổi khởi động chương trình First Cloud AI Journey

&emsp;**Thời gian:** Ngày 20/06/2026

&emsp;**Địa điểm:** Tầng 26, tòa nhà Bitexco Tower, số 02 đường Hải Triều, phường Sài Gòn, Thành phố Hồ Chí Minh

&emsp;**Đơn vị tổ chức:** Công ty TNHH Amazon Web Services Viet Nam - chương trình First Cloud AI Journey

&emsp;**Vai trò trong sự kiện:** Người tham dự, theo dõi cuộc thi với vai trò khán giả

&emsp;**Hình thức sự kiện:** Thi đấu theo đội, mỗi đội từ 4 đến 5 thành viên

### Mục Đích Của Sự Kiện

- Tạo không khí gắn kết giữa các thành viên trong buổi gặp mặt đầu tiên của chương trình
- Giúp người tham dự nhìn ra mặt bằng kiến thức nền tảng về AWS mà chương trình kỳ vọng
- Giới thiệu dạng câu hỏi tình huống mà doanh nghiệp thực sự gặp phải, thay vì chỉ dừng ở lý thuyết thuần túy
- Định hướng lộ trình tự học cho giai đoạn tiếp theo dựa trên những phần kiến thức còn thiếu

### Hình Thức Và Thể Lệ

Các đội thi được chia ngẫu nhiên, mỗi đội từ 4 đến 5 người. Vì chia ngẫu nhiên nên các thành viên trong cùng một đội hầu như chưa quen nhau, buộc mỗi đội phải tự phân công vai trò trong thời gian rất ngắn.

Cuộc thi được tổ chức theo nhiều vòng với độ khó tăng dần:

| Vòng thi | Nội dung | Cách tính điểm |
|---|---|---|
| **Vòng 1 - Khởi động** | Câu hỏi trắc nghiệm nhanh về khái niệm nền tảng của điện toán đám mây và AWS | Trả lời đúng và nhanh được điểm cao hơn |
| **Vòng 2 - Kiến thức dịch vụ** | Câu hỏi về đặc điểm, giới hạn và cách tính phí của các dịch vụ cốt lõi | Điểm cố định cho mỗi câu đúng |
| **Vòng 3 - Tình huống doanh nghiệp** | Cho trước một yêu cầu nghiệp vụ có thật, đội phải đề xuất dịch vụ AWS phù hợp và giải thích lý do | Chấm theo tính hợp lý của phương án và phần lập luận |
| **Vòng 4 - Về đích** | Câu hỏi mở, đội tự chọn mức điểm tương ứng với độ khó | Trả lời sai bị trừ điểm |

Sau mỗi câu hỏi, ban giám khảo là các mentor và kỹ sư của AWS sẽ giải thích đáp án, phân tích vì sao một phương án tưởng chừng đúng lại không phù hợp trong bối cảnh cụ thể. Với một người tham dự ở vị trí khán giả như em, đây chính là phần giá trị nhất của sự kiện, vì được nghe trọn vẹn phần lập luận mà không bị áp lực thời gian chi phối như các bạn đang thi đấu.

### Nội Dung Bộ Câu Hỏi

#### Nhóm 1 - Kiến thức nền tảng

- Phân biệt ba mô hình dịch vụ IaaS, PaaS và SaaS
- Phân biệt Region, Availability Zone và Edge Location
- Mô hình trách nhiệm chung giữa AWS và khách hàng
- Các nhóm dịch vụ chính và dịch vụ tiêu biểu của từng nhóm

#### Nhóm 2 - Dịch vụ cốt lõi

- Amazon EC2: các họ instance, bốn mô hình giá và trường hợp phù hợp của từng mô hình
- Amazon S3: các storage class, độ bền dữ liệu và cơ chế lifecycle
- Amazon VPC: subnet public và private, vai trò của Internet Gateway và NAT Gateway
- AWS IAM: user, group, role và thứ tự đánh giá policy
- Amazon RDS: khác biệt giữa Multi-AZ và read replica

#### Nhóm 3 - Tình huống thực tiễn theo yêu cầu doanh nghiệp

Đây là nhóm câu hỏi khó nhất và cũng là phần gây tranh luận nhiều nhất giữa các đội. Mỗi câu đưa ra một bài toán kinh doanh kèm ràng buộc về chi phí, thời gian hoặc bảo mật, và yêu cầu đội đề xuất phương án trên AWS.

Dưới đây là một số tình huống em ghi lại được trong lúc theo dõi cuộc thi:

| Yêu cầu doanh nghiệp | Phương án các đội đưa ra | Phần giải thích của ban giám khảo |
|---|---|---|
| Một sàn thương mại điện tử có lưu lượng tăng đột biến vào khung giờ khuyến mãi, còn lại thì rất thấp. Chi phí máy chủ nhàn rỗi đang quá cao | Dùng Auto Scaling Group kết hợp Application Load Balancer, đặt scaling policy theo mức sử dụng CPU | Phương án hợp lý. Ban giám khảo bổ sung hướng dùng scheduled scaling vì khung giờ khuyến mãi đã biết trước, sẽ phản ứng kịp thời hơn so với chờ CPU tăng rồi mới mở rộng |
| Doanh nghiệp cần lưu trữ hồ sơ kế toán trong bảy năm theo quy định, gần như không truy cập lại, yêu cầu chi phí thấp nhất có thể | Đưa dữ liệu vào Amazon S3 rồi dùng lifecycle rule chuyển sang S3 Glacier Deep Archive | Đúng hướng. Ban giám khảo lưu ý thêm rằng thời gian khôi phục dữ liệu của Deep Archive có thể lên tới hàng giờ, cần thống nhất trước với bộ phận nghiệp vụ |
| Ứng dụng nội bộ chạy trong VPC cần đọc ghi dữ liệu trên S3 nhưng bộ phận bảo mật không cho phép lưu lượng đi ra internet | Có đội đề xuất dùng NAT Gateway | Chưa đạt. Đáp án phù hợp là VPC Gateway Endpoint cho S3, vừa giữ lưu lượng không đi qua internet vừa không phát sinh chi phí theo giờ như NAT Gateway |
| Hệ thống phải tiếp tục hoạt động khi mất trọn một Availability Zone, thời gian gián đoạn cho phép rất ngắn | Triển khai tầng ứng dụng trên nhiều Availability Zone bằng Auto Scaling Group, bật Multi-AZ cho cơ sở dữ liệu | Phương án đầy đủ. Ban giám khảo hỏi thêm về sự khác biệt giữa Multi-AZ và read replica để làm rõ mục đích của từng cơ chế |
| Một nhân viên nghỉ việc, cần thu hồi toàn bộ quyền truy cập ngay lập tức và tránh lặp lại rủi ro tương tự | Vô hiệu hóa IAM user và xóa access key | Đúng nhưng chưa đủ. Ban giám khảo định hướng sang việc dùng IAM role và đăng nhập tập trung thay cho access key dài hạn, để việc thu hồi quyền diễn ra tức thời và có thể kiểm toán |

#### Nhóm 4 - Chi phí và tối ưu

- Ước tính chi phí của một kiến trúc đơn giản dựa trên bảng giá
- Nhận diện các thành phần thường bị bỏ quên nhưng vẫn phát sinh chi phí liên tục như NAT Gateway, Elastic IP không sử dụng, EBS volume mồ côi
- Vai trò của cost allocation tag trong việc quy trách nhiệm chi phí cho từng nhóm

### Quan Sát Và Ghi Nhận Từ Vị Trí Khán Giả

Ở hai vòng đầu, phần lớn các đội trả lời khá tốt vì đây là những khái niệm có thể học thuộc từ tài liệu.

Sự phân hóa chỉ thực sự xuất hiện ở vòng tình huống doanh nghiệp. Nhiều câu không có một đáp án duy nhất đúng mà phụ thuộc vào ràng buộc cụ thể của đề bài. Có những phương án chạy được hoàn toàn về mặt kỹ thuật nhưng vẫn bị đánh giá thấp vì chi phí không hợp lý hoặc vi phạm yêu cầu bảo mật đã nêu trong đề. Ngồi theo dõi, em nhận thấy các đội mắc lỗi chủ yếu không phải vì thiếu kiến thức mà vì đọc lướt qua ràng buộc trong đề bài.

Một điểm nữa em quan sát được là cách các đội xử lý bất đồng. Những đội thống nhất phương án nhanh thường là những đội quay lại đối chiếu với yêu cầu trong đề, thay vì tranh luận xem dịch vụ nào tốt hơn một cách chung chung.

Vì không trực tiếp thi đấu nên em có điều kiện ghi chép lại đầy đủ cả câu hỏi lẫn phần phân tích của ban giám khảo. Tập ghi chép này trở thành tài liệu tham khảo khá hữu ích cho giai đoạn tự học sau đó.

### Những Gì Học Được

#### Về kiến thức

- Hình dung được mức độ kiến thức nền tảng mà chương trình kỳ vọng ở một thực tập sinh, từ đó biết mình đang đứng ở đâu
- Nhận ra khoảng cách giữa việc biết một dịch vụ tồn tại và việc biết khi nào nên dùng dịch vụ đó
- Hiểu rằng nhiều dịch vụ AWS trông có vẻ thay thế được cho nhau nhưng khác nhau rõ rệt về chi phí và mô hình bảo mật, điển hình là NAT Gateway so với VPC Endpoint

#### Về tư duy giải bài toán doanh nghiệp

- Một phương án kỹ thuật đúng chưa chắc là phương án tốt. Phải cân nhắc đồng thời chi phí, độ phức tạp vận hành và yêu cầu tuân thủ
- Cần đọc kỹ ràng buộc trong đề bài trước khi nghĩ tới giải pháp. Phần lớn câu trả lời bị đánh giá thấp trong buổi thi đều do bỏ sót một điều kiện đã nêu rõ
- Luôn phải giải thích được lý do lựa chọn, vì trong công việc thực tế thì phần lập luận quan trọng không kém kết quả

#### Về giá trị của việc quan sát

- Theo dõi người khác giải quyết vấn đề dưới áp lực thời gian cho thấy rõ những lỗi tư duy phổ biến, những lỗi mà nếu tự học một mình sẽ khó nhận ra
- Phần giải thích của ban giám khảo sau mỗi câu hỏi có giá trị hơn bản thân đáp án, vì nó cho thấy cách một kỹ sư có kinh nghiệm phân tích ràng buộc trước khi chọn dịch vụ

### Ứng Dụng Vào Quá Trình Thực Tập

Những phần kiến thức xuất hiện nhiều trong buổi thi đã trở thành định hướng tự học cho các tuần tiếp theo:

- Phần phân quyền và nguyên tắc đặc quyền tối thiểu được ưu tiên học ngay ở tuần 4 cùng với việc kiểm soát chi phí
- Phần storage class và lifecycle của S3 được thực hành kỹ ở tuần 5
- Phần mạng, đặc biệt là sự khác biệt giữa NAT Gateway và VPC Endpoint, được làm rõ ở tuần 6
- Thói quen đọc kỹ ràng buộc và ước tính chi phí trước khi triển khai được duy trì cho mọi bài lab về sau

### Một Số Hình Ảnh Khi Tham Gia Sự Kiện

<!--
HƯỚNG DẪN CHÈN ẢNH:
1. Đặt file ảnh vào thư mục: static/images/4-EventParticipated/4.1-Event1/
2. Bỏ dấu chú thích của các dòng bên dưới và sửa lại tên file cho đúng.
3. Tên file không dấu, không khoảng trắng. Ví dụ: toan-canh.png, ban-giam-khao.png
-->

<!-- ![Toàn cảnh buổi thi tại tầng 26 tòa nhà Bitexco Tower](/images/4-EventParticipated/4.1-Event1/toan-canh.png) -->

<!-- ![Các đội thi trong vòng câu hỏi tình huống doanh nghiệp](/images/4-EventParticipated/4.1-Event1/vong-tinh-huong.png) -->

<!-- ![Ban giám khảo giải thích đáp án sau mỗi câu hỏi](/images/4-EventParticipated/4.1-Event1/giai-thich-dap-an.png) -->

![Ảnh chụp tại sự kiện](/fcj-workshop-template/static/images/4.1-Event1/event.jpg)

> Nhìn lại, đây là một cách mở đầu chương trình rất hiệu quả. Dù chỉ tham dự với vai trò khán giả, em vẫn thu được nhiều hơn kỳ vọng ban đầu. Giá trị lớn nhất không nằm ở việc biết thêm vài dịch vụ mới, mà ở việc lần đầu tiên tiếp cận AWS dưới góc nhìn của một bài toán doanh nghiệp có ràng buộc thật, thay vì chỉ là danh sách các dịch vụ cần ghi nhớ.
