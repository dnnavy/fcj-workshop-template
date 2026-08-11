---
title: "Event 2"
date: 2026-07-31
weight: 2
chapter: false
pre: " <b> 4.2. </b> "
---

# Bài thu hoạch "Chung kết AWS Quiz Battle"

### Thông tin sự kiện

&emsp;**Tên sự kiện:** Chung kết AWS Quiz Battle

&emsp;**Thời gian:** Ngày 11/07/2026

&emsp;**Địa điểm:** Tầng 26, tòa nhà Bitexco Tower, số 02 đường Hải Triều, phường Sài Gòn, Thành phố Hồ Chí Minh

&emsp;**Đơn vị tổ chức:** Công ty TNHH Amazon Web Services Viet Nam - chương trình First Cloud AI Journey

&emsp;**Vai trò trong sự kiện:** Người tham dự

&emsp;**Hình thức:** Vòng chung kết gồm ba chủ đề chuyên sâu được trình bày lần lượt

### Bối Cảnh

Đây là vòng cuối của AWS Quiz Battle, cuộc thi được khởi động từ ngày 20/06/2026 mà em đã theo dõi ở vai trò khán giả và ghi lại trong phần [Event 1](../4.1-event1/).

Khác với vòng đầu chủ yếu kiểm tra kiến thức nền tảng qua các câu hỏi nhanh, vòng chung kết chuyển sang hình thức trình bày chuyên sâu theo chủ đề. Ba chủ đề được đưa ra lần này đi vào những phần mà một người mới học AWS thường bỏ qua: cam kết chất lượng dịch vụ và giám sát, bảo mật ứng dụng web bằng agent, và cấu trúc thực tế của kỳ thi chứng chỉ nền tảng.

### Cấu Trúc Chương Trình

| Chủ đề | Tên | Trọng tâm |
|---|---|---|
| **Topic 1** | SLA and Monitoring - From SLA to Monitoring What Really Matters | Từ cam kết dịch vụ tới việc giám sát đúng thứ cần giám sát |
| **Topic 2** | Securing Your Web Apps With AWS Security Agent | Tự động hóa kiểm thử bảo mật xuyên suốt vòng đời phát triển |
| **Topic 3** | Inside The Exam - AWS Cloud Practitioner | Cấu trúc và trọng số các miền kiến thức của kỳ thi |

## Topic 1 - SLA and Monitoring: From SLA to Monitoring What Really Matters

### SLA là gì và tại sao cần

**SLA (Service Level Agreement)** là cam kết chính thức về mức kỳ vọng dịch vụ giữa nhà cung cấp và khách hàng. SLA mang lại bốn giá trị:

- Định hình kỳ vọng một cách rõ ràng giữa hai bên
- Xác định trách nhiệm giải trình khi có sự cố
- Tạo cơ sở để đo lường hiệu năng
- Phục vụ cho việc quản trị rủi ro

### Giám sát nằm bên trong quản trị rủi ro

Điểm mà diễn giả nhấn mạnh là giám sát không phải một hoạt động riêng lẻ mà là một phần của quản trị rủi ro. Mục tiêu của giám sát là phát hiện rủi ro sớm, trước khi nó gây ảnh hưởng tới SLA. Chu trình gồm bốn bước:

| Bước | Nội dung |
|---|---|
| **Nhận diện rủi ro** | Xác định những gì có thể làm hệ thống vi phạm SLA |
| **Giám sát tín hiệu** | Thu thập metrics, logs và thiết lập alarms |
| **Phản ứng** | Kích hoạt thông báo qua Amazon SNS, chạy quy trình xử lý sự cố đã định sẵn, khôi phục hệ thống |
| **Cải tiến** | Đánh giá lại sự cố sau khi xử lý, tinh chỉnh để phòng ngừa tái diễn |

### Mô hình Kim Tự Tháp Giám Sát

Đây là phần có giá trị nhất của chủ đề. Mô hình xếp các lớp cần giám sát theo thứ tự từ đỉnh xuống đáy:

| Tầng | Nội dung giám sát |
|---|---|
| **Customer Experience** (đỉnh) | Trải nghiệm thực tế của người dùng cuối |
| **Business** | Tỷ lệ đăng nhập thành công, số lượng đơn hàng, doanh thu |
| **Application** | Độ trễ, tỷ lệ lỗi, số lượng yêu cầu |
| **Infrastructure** | CPU, bộ nhớ, ổ đĩa, mạng |
| **Cloud Provider** (đáy) | Trạng thái các dịch vụ EC2, RDS, ALB, S3 |

Điều đáng chú ý là thứ tự này ngược với cách một người mới học thường tiếp cận. Người mới thường bắt đầu từ đáy kim tự tháp, tức là theo dõi CPU và bộ nhớ, vì đó là những chỉ số dễ lấy nhất. Trong khi đó tầng quan trọng nhất lại nằm ở đỉnh và khó đo nhất.

### Kết luận của chủ đề

- **Hạ tầng khỏe không đồng nghĩa với người dùng hài lòng.** Một kiến trúc hạ tầng tốt không bảo đảm người dùng có trải nghiệm tốt. Health check có thể vẫn pass trong khi trải nghiệm người dùng đã lỗi. Chỉ riêng các chỉ số hạ tầng không nói lên được toàn bộ tình trạng hệ thống.
- **Phải hiểu SLA trong bối cảnh trách nhiệm chung.** AWS chịu trách nhiệm cho hạ tầng đám mây, còn trách nhiệm với trải nghiệm của người dùng thuộc về chính người xây dựng hệ thống.
- **Phải hiểu người dùng làm gì và cần gì**, chứ không chỉ biết về hệ thống của mình.

## Topic 2 - Securing Your Web Apps With AWS Security Agent

### Điểm nghẽn của kiểm thử bảo mật truyền thống

Diễn giả mở đầu bằng ba vấn đề của cách kiểm thử xâm nhập theo cách thủ công:

- Một đợt pentest thủ công thường kéo dài nhiều tuần
- Chi phí thuê chuyên gia pentest từ bên thứ ba rất cao, dao động khoảng năm nghìn tới hai mươi nghìn đô la Mỹ
- Kết quả kiểm thử phụ thuộc nhiều vào trình độ của từng pentester

Ba vấn đề này khiến kiểm thử bảo mật thường bị đẩy về cuối chu trình phát triển hoặc bị bỏ qua ở các dự án nhỏ.

### Frontier Agent và điểm khác biệt so với một chatbot

Sản phẩm được trình bày là một security agent vận hành bởi **Amazon Bedrock**, có khả năng tự lên kế hoạch và thực thi các tác vụ bảo mật phức tạp mà không cần con người can thiệp từng bước.

Điểm khác biệt cốt lõi so với một chatbot dựa trên mô hình ngôn ngữ thông thường là agent này **kiểm chứng lỗ hổng bằng cách thực hiện khai thác thực tế**, thay vì chỉ đưa ra dự đoán về những lỗ hổng có thể tồn tại. Ba khả năng chính:

| Khả năng | Cách hoạt động |
|---|---|
| **Rà soát thiết kế** | Phân tích tài liệu kiến trúc từ trước khi viết code, kiểm tra theo các chuẩn PCI DSS, NIST CSF và AWS Well-Architected để bảo đảm thiết kế thỏa mãn yêu cầu bảo mật |
| **Rà soát mã nguồn** | Tự động quét các pull request để tìm lỗ hổng bảo mật và các thông tin riêng tư bị rò rỉ trong code như mật khẩu hay API key |
| **Kiểm thử xâm nhập chủ động** | Tự động tấn công vào ứng dụng, đóng vai một người dùng thực thụ, thực hiện các chuỗi tấn công đa bước rồi đưa ra sơ đồ tấn công kèm bằng chứng có thể xác minh chi tiết |

Ba khả năng này phủ toàn bộ vòng đời phát triển: rà soát thiết kế, bảo mật mã nguồn và kiểm thử xâm nhập chủ động.

### Tích hợp vào quy trình làm việc

Agent cho phép tích hợp trực tiếp vào pull request trên GitHub hoặc GitLab, để lại nhận xét ngay trên từng dòng code, và đề xuất các bản vá mã nguồn hợp lệ dưới dạng pull request tự động.

Đây là điểm em thấy đáng chú ý về mặt thiết kế sản phẩm: thay vì tạo ra một báo cáo bảo mật riêng biệt mà lập trình viên phải chủ động đi đọc, kết quả được đưa thẳng vào nơi lập trình viên đang làm việc.

### Các giới hạn cần lưu ý

Phần này em thấy giá trị không kém phần giới thiệu tính năng, vì diễn giả nói rõ agent không phải giải pháp thay thế hoàn toàn:

- Các cơ chế xác thực như MFA, sinh trắc học hay mTLS sẽ làm gián đoạn khả năng tự động của agent
- Agent gặp khó khăn khi phát hiện các lỗi gian lận thuộc về logic nghiệp vụ, nếu thiếu ngữ cảnh nghiệp vụ đủ sâu
- Ứng dụng càng phức tạp thì càng tiêu tốn thời gian thực thi, do đó việc theo dõi thời gian chạy của agent là bắt buộc

## Topic 3 - Inside The Exam: AWS Cloud Practitioner

### Định vị của chứng chỉ

**AWS Certified Cloud Practitioner** là một chứng chỉ nền tảng, tập trung vào tư duy và bức tranh tổng quan về AWS Cloud. Kỳ thi không yêu cầu kỹ năng lập trình hay khả năng cấu hình chuyên sâu, nên phù hợp làm bước đầu tiên cho người mới tiếp cận nền tảng.

### Cấu trúc bốn miền kiến thức

| Miền kiến thức | Trọng số |
|---|---|
| Domain 1 - Cloud Concepts | 24% |
| Domain 2 - Security and Compliance | 30% |
| Domain 3 - Cloud Technology and Services | 34% |
| Domain 4 - Billing, Pricing, and Support | 12% |

Điều em thấy đáng chú ý ở bảng trọng số này là **Security and Compliance chiếm 30%**, gần bằng miền về dịch vụ và công nghệ, dù đây chỉ là một chứng chỉ nền tảng. Điều đó cho thấy AWS xem hiểu biết về bảo mật là kiến thức bắt buộc từ mức cơ bản nhất, không phải nội dung dành riêng cho người đi chuyên sâu.

Miền Billing, Pricing and Support chiếm 12%, tỷ lệ không nhỏ đối với một nội dung thường bị người học bỏ qua vì cho rằng không liên quan tới kỹ thuật.

### Những Gì Học Được

#### Về giám sát và vận hành

- Giám sát không phải là bật một dịch vụ theo dõi rồi coi như xong. Mô hình kim tự tháp cho thấy các chỉ số hạ tầng chỉ nằm ở tầng gần đáy, còn thứ thực sự quan trọng là trải nghiệm người dùng ở đỉnh.
- Hiểu được vì sao một hệ thống có health check bình thường vẫn có thể đang gây trải nghiệm tồi cho người dùng, và vì sao cần đo thêm các chỉ số ở tầng nghiệp vụ như tỷ lệ đăng nhập thành công.
- Nắm được chu trình đầy đủ từ nhận diện rủi ro tới cải tiến sau sự cố, thay vì chỉ dừng ở việc đặt cảnh báo.

#### Về bảo mật

- Thấy được sự dịch chuyển từ chỗ kiểm thử bảo mật là một hoạt động tách rời ở cuối chu trình, sang chỗ bảo mật được kiểm tra liên tục ngay từ giai đoạn thiết kế.
- Hiểu được khác biệt quan trọng giữa một hệ thống dự đoán lỗ hổng và một hệ thống kiểm chứng lỗ hổng bằng khai thác thực tế. Cái thứ hai cho ra bằng chứng có thể xác minh, nên kết quả đáng tin hơn nhiều.
- Nhận ra rằng việc rò rỉ mật khẩu và API key trong mã nguồn là một loại lỗi phổ biến tới mức cần có công cụ tự động quét, chứ không thể trông vào sự cẩn thận của từng người.
- Ghi nhận các giới hạn của tự động hóa: những gì cần ngữ cảnh nghiệp vụ hoặc vượt qua xác thực nhiều lớp vẫn cần con người.

#### Về lộ trình chứng chỉ

- Có được bức tranh cụ thể về cấu trúc kỳ thi Cloud Practitioner thay vì chỉ biết tên chứng chỉ.
- Trọng số 30% dành cho bảo mật và tuân thủ là chỉ dấu để em phân bổ lại thời gian ôn tập, thay vì tập trung quá nhiều vào phần danh sách dịch vụ.

### Ứng Dụng Vào Quá Trình Thực Tập

Sự kiện diễn ra ngay sau tuần thứ 6 của kỳ thực tập, thời điểm em vừa hoàn thành phần mạng và bắt đầu chuẩn bị cho nội dung cân bằng tải cùng tính sẵn sàng cao ở tuần 7. Ba chủ đề của buổi chung kết ảnh hưởng tới cách em làm việc ở giai đoạn sau như sau:

- **Từ Topic 1:** ở tuần 6 em đã bật VPC Flow Logs và gửi log sang CloudWatch Logs, nhưng chỉ dừng ở mục đích gỡ lỗi kết nối. Mô hình kim tự tháp giám sát cho em thấy đó chỉ là tầng gần đáy. Khi triển khai kiến trúc cân bằng tải ở tuần 7, em chú ý thêm tới các chỉ số ở tầng ứng dụng như độ trễ và tỷ lệ lỗi thay vì chỉ nhìn mức sử dụng CPU.
- **Từ Topic 1:** phần trách nhiệm chung trong SLA nối trực tiếp với mô hình trách nhiệm chung em đã học ở tuần 2, nhưng ở góc nhìn cụ thể hơn: AWS bảo đảm hạ tầng, còn trải nghiệm người dùng là phần em phải tự chịu trách nhiệm.
- **Từ Topic 2:** vấn đề rò rỉ API key trong mã nguồn củng cố thêm lý do em đã chọn dùng IAM role thay cho access key dài hạn từ tuần 4, và khiến em rà lại các file cấu hình trong repository báo cáo.
- **Từ Topic 2:** việc agent đối chiếu thiết kế với chuẩn AWS Well-Architected nhắc em dùng chính bộ trụ cột này làm danh sách rà soát cho bản đề xuất giải pháp, thay vì chỉ vẽ kiến trúc rồi để đó.
- **Từ Topic 3:** em điều chỉnh lại kế hoạch ôn thi chứng chỉ đã đặt ra từ tuần 1, chọn Cloud Practitioner làm bước đệm trước Solutions Architect Associate, và dành thêm thời gian cho phần bảo mật và tuân thủ theo đúng trọng số của kỳ thi.

### Một Số Hình Ảnh Khi Tham Gia Sự Kiện

<!--
HƯỚNG DẪN CHÈN ẢNH:
1. Đặt file ảnh vào thư mục: static/images/4-EventParticipated/4.2-Event2/
2. Bỏ dấu chú thích của các dòng bên dưới và sửa lại tên file cho đúng.
3. Tên file không dấu, không khoảng trắng. Ví dụ: toan-canh.png, topic1-sla.png
-->

<!-- ![Toàn cảnh vòng chung kết](/images/4-EventParticipated/4.2-Event2/toan-canh.png) -->

<!-- ![Topic 1 - SLA và mô hình kim tự tháp giám sát](/images/4-EventParticipated/4.2-Event2/topic1-sla.png) -->

<!-- ![Topic 2 - AWS Security Agent](/images/4-EventParticipated/4.2-Event2/topic2-security-agent.png) -->

<!-- ![Topic 3 - Cấu trúc kỳ thi AWS Cloud Practitioner](/images/4-EventParticipated/4.2-Event2/topic3-exam.png) -->

![Ảnh chụp tại sự kiện](/images/4.2-Event2/event.jpg)

> Vòng chung kết có tính chất khác hẳn vòng đầu. Nếu buổi 20/06 kiểm tra xem người tham dự biết những gì, thì buổi này cho thấy những phần mà một người mới học AWS rất dễ bỏ qua. Với em, chủ đề về SLA và giám sát là phần thay đổi cách nghĩ nhiều nhất: trước đó em vẫn ngầm hiểu rằng hệ thống chạy được và các chỉ số hạ tầng bình thường thì nghĩa là ổn. Mô hình kim tự tháp giám sát cho thấy đó mới là tầng thấp nhất, và phần khó nhất của việc vận hành nằm ở chỗ đo được thứ mà người dùng thực sự cảm nhận.
