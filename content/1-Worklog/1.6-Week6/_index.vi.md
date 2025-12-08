---
title: "Worklog Tuần 6"
date: 2025-10-13
weight: 1
chapter: false
pre: " <b> 1.6. </b> "
---



### Mục tiêu tuần 6:

* Sử dụng AWS IAM Identity Center để quản lý định danh.
* Làm quen với AWS Web Application Firewall.
* Quản lý tài nguyên bằng Tag và Resource Groups.

### Các công việc cần triển khai trong tuần này:
| Thứ | Công việc                                                                                                                                                                                   | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu                            |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------ | --------------- | ----------------------------------------- |
| 2   | -  Sử dụng AWS IAM Identity Center để quản lý định danh mạnh mẽ <br>&emsp; +  Truy cập AWS CLI <br>&emsp; + Customer Managed Policies  <br>&emsp; + Quản lý và kiểm toán các hoạt động User và Group của AWS IAM Identity Center    <br>&emsp; + Clean resource                                                                    | 13/10/2025   | 13/10/2025      |<https://000012.awsstudygroup.com/>
| 3   | - Tìm hiểu khái niệm và thực hành về AWS Web Application Firewall. <br>&emsp; + Giới thiệu về AWS WAF <br>&emsp; + Tạo S3 bucket<br>&emsp; + Sử dụng OWASP Juice Shop để triển khai ứng dụng mẫu                                    | 14/10/2025   | 14/10/2025      | <https://000026.awsstudygroup.com/> |
| 4   | - Tìm hiểu khái niệm và thực hành về AWS Web Application Firewall.<br>- Sử dụng AWS WAF <br>&emsp;**Thực hành:** <br>&emsp;  + Triển khai Web ACLs với managed rules <br>&emsp; +  Tạo các rule tùy chỉnh để xử lý các request  <br>&emsp; + Định nghĩa rule sử dụng JSON cho phép bạn áp dụng việc quản lý phiên bản nhằm dễ dàng xem xét cách thức, thời điểm và lý do một tập các rule phức tạp được thay đổi <br>&emsp; + Kiểm thử Rule mới <br>&emsp; + Sử dụng Amazon Kinesis Firehose để ghi nhật ký request <br>&emsp; + Dọn dẹp tài nguyên  | 15/10/2025   | 15/10/2025      | <https://000026.awsstudygroup.com/vi/> |
| 5   | - Quản lý tài nguyên bằng Tag và Resource Groups  <br>- Hướng dẫn cách gán các metadata của mỗi tài nguyên dưới dạng Tag <br>&emsp; + Thực hiện gắn tag các tài nguyên, thực hiện thêm, xóa tag trên các tài nguyên cũng như quản lý, lọc tài nguyên được gắn tag. <br>&emsp; +  Sử dụng tag trên Console: thực hiện các thao tác với các thẻ (tag) trên AWS Management Console. <br>&emsp; + Tạo EC2 Instance có tag<br>&emsp; + Thêm hoặc xóa tag <br>&emsp; + Lọc tài nguyên theo tag <br>&emsp; + Sử dụng tag bằng CLI          | 16/10/2025   | 16/10/2025       | <https://000027.awsstudygroup.com/vi/1-using-tags> |
| 6   | - Quản lý tài nguyên bằng Tag và Resource Groups <br>&emsp;**Thực hành:** <br>&emsp; + Sử dụng tag bằng CLI <br>&emsp; + Thêm tag cho tài nguyên hiện có <br>&emsp; + Thêm tag cho tài nguyên mới <br>&emsp; + Mô tả các tài nguyên được gắn tag <br>&emsp; + Tạo một Resource Group: tạo một Resource Group được phân loại theo thẻ <br>&emsp; + Dọn dẹp tài nguyên                                                                                        | 17/10/2025   | 17/10/2025      | <https://000027.awsstudygroup.com/vi/1-using-tags>|

### Kết quả đạt được tuần 6:
* Quản lý định danh với AWS IAM Identity Center
  * Làm quen với cách quản lý người dùng, nhóm và quyền truy cập tập trung bằng IAM Identity Center.
  * Áp dụng Customer Managed Policies để kiểm soát chi tiết quyền truy cập.
  * Thực hành quản lý, giám sát và kiểm toán hoạt động User/Group thông qua CLI và Console

* Tìm hiểu và thực hành AWS Web Application Firewall
  * Nắm vững khái niệm và vai trò của WAF trong việc bảo vệ ứng dụng web khỏi các mối đe dọa bảo mật.
  * Triển khai ứng dụng mẫu bằng OWASP Juice Shop để kiểm thử.
  * Thực hành tạo Web ACLs với managed rules và rule tùy chỉnh (JSON), kiểm soát và ghi lại request qua Amazon Kinesis Firehose.
  * Xây dựng được môi trường thử nghiệm WAF, hiểu rõ cách áp dụng và kiểm thử rule bảo mật.

* Quản lý tài nguyên với Tag và Resource Groups:

  * Nắm được cơ chế Tagging để gắn metadata cho tài nguyên AWS.
  * Thực hiện gắn, thêm, xóa tag cho tài nguyên qua Console và CLI, quản lý và lọc tài nguyên hiệu quả.
  * Tạo Resource Group dựa trên tag, giúp phân loại và tổ chức tài nguyên theo từng nhóm, phục vụ quản trị hệ thống dễ dàng hơn.



