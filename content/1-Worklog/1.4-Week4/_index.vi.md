---
title: "Worklog Tuần 4"
date: 2025-09-29
weight: 1
chapter: false
pre: " <b> 1.4. </b> "
---


### Mục tiêu tuần 4:

* Tiếp tục triển khai Wordpress trên AWS Cloud
* Làm quen với Amazon Relational Database Service (Amazon RDS)

### Các công việc cần triển khai trong tuần này:
| Thứ | Công việc                                                                                                                                                                                   | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu                            |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------ | --------------- | ----------------------------------------- |
| 2   | -  Triển khai Wordpress trên AWS Cloud <br>&emsp; + Cài đặt dịch vụ httpd <br>&emsp; + Cài đặt php-mysql  <br>&emsp; + Cài đặt php7.3  <br>&emsp; + Di chuyển thư mục về nơi wordpress thực thi để tiến hành tải và cài đặt Wordpress <br>&emsp; + Mở trình duyệt web truy cập địa chỉ ipv4 dns public của ec2 webserver <br>&emsp; + Thiết lập các thông số cơ bản cho wordpress để đăng nhập vào giao diện admin wordpress                                                                       | 29/09/2025   | 29/09/2025      |<https://000021.awsstudygroup.com/>
| 3   | - Triển khai Wordpress trên AWS Cloud <br>&emsp; + Thực hiện tạo Autoscaling cho wordpress Instance: <br>&emsp; + Khởi tạo AMI từ Webserver Instance DNS<br>&emsp; + Khởi tạo Launch Template <br>&emsp; + Khởi tạo Target Group  <br>&emsp; + Khởi tạo Load Balancer   <br>&emsp; + Khởi tạo Auto Scaling Group                                   | 30/09/2025   | 30/09/2025      | <https://000021.awsstudygroup.com/> |
| 4   | - Triển khai Wordpress trên AWS Cloud <br>&emsp; + Sao lưu và phục hồi database <br>&emsp;  + Khởi tạo Cloudfront cho Web Server <br>&emsp; + Dọn dẹp tài nguyên  | 01/10/2025   | 01/10/2025      | <https://000021.awsstudygroup.com/> |
| 5   | - Làm quen với Amazon Relational Database Service (Amazon RDS) <br>&emsp;**Thực hành:** <br>&emsp; + Tạo VPC <br>&emsp; + Tạo EC2 Security Group <br>&emsp; + Tạo RDS Security Group <br>&emsp; +  Tạo DB Subnet Group             | 02/10/2025   | 02/10/2025       | <https://000005.awsstudygroup.com/vi/4-create-rds/> |
| 6   | - Làm quen với Amazon Relational Database Service (Amazon RDS) <br>&emsp;**Thực hành:** <br>&emsp; + Tạo EC2 instance <br>&emsp; + Tạo RDS database instance <br>&emsp; +  Triển khai ứng dụng <br>&emsp; + Backup và restore <br>&emsp; + Dọn dẹp tài nguyên                                                                                        | 03/10/2025   | 03/10/2025      | <https://000005.awsstudygroup.com/vi/4-create-rds/>|


### Kết quả đạt được tuần 4:

* Triển khai Wordpress trên AWS Cloud
  * Cài đặt thành công Wordpress trên EC2 Webserver, truy cập được qua IPv4 Public DNS.
  * Thiết lập các thông số cơ bản và đăng nhập thành công
  * Xây dựng cơ chế Autoscaling cho Wordpress Instance thông qua AMI, Launch Template, Load Balancer, Target Group và Auto Scaling Group, giúp hệ thống có khả năng mở rộng linh hoạt.
  * Thực hiện sao lưu và phục hồi database cho Wordpress, đảm bảo tính sẵn sàng dữ liệu.
  * Tích hợp CloudFront để phân phối nội dung tĩnh, tăng tốc độ truy cập và cải thiện trải nghiệm người dùng.

* Làm quen với Amazon Relational Database Service (Amazon RDS)
  * Tìm hiểu cách vận hành RDS và các thành phần liên quan: VPC, Security Group, DB Subnet Group.
  * Khởi tạo thành công RDS Database Instance và kết nối với EC2 để triển khai ứng dụng.
  * Thực hành các thao tác quản trị: backup, restore và dọn dẹp tài nguyên.



