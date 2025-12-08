---
title: "Worklog Tuần 3"
date: 2025-08-25
weight: 1
chapter: false
pre: " <b> 1.3. </b> "
---


### Mục tiêu tuần 3:

* Thiết lập VPC Peering
* Tìm hiểu về AWS Transit Gateway
* Triển khai Wordpress trên AWS Cloud

### Các công việc cần triển khai trong tuần này:
| Thứ | Công việc                                                                                                                                                                                   | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu                            |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------ | --------------- | ----------------------------------------- |
| 2   | -  Thiết lập VPC Peering <br>&emsp; + Khởi tạo CloudFormation Template <br>&emsp; + Tạo Security Group  <br>&emsp; + Tạo EC2 instance  <br>&emsp; + Cập nhật Network ACL                                                                              | 25/08/2025   | 25/08/2025      |<https://000019.awsstudygroup.com/vi/1-introduce/>
| 3   | - Thiết lập VPC Peering <br>&emsp; + Tạo kết nối Peering <br>&emsp; + Kích hoạt Cross-Peer DNS<br>&emsp; + Dọn dẹp tài nguyên                                           | 26/08/2025   | 26/08/2025      | <https://000019.awsstudygroup.com/vi/6-crosspeerdns/> |
| 4   | - Tìm hiểu về AWS Transit Gateway <br>&emsp;- **Thực hành:** <br>&emsp; + Tạo Key Pair <br>&emsp;  + Khởi tạo CloudFormation Template <br>&emsp; + Tạo Transit Gateway  | 27/08/2025   | 27/08/2025      | <https://000020.awsstudygroup.com/vi/> |
| 5   | - Tìm hiểu về AWS Transit Gateway <br>&emsp;**Thực hành:** <br>&emsp; + Tạo Transit Gateway Attachments <br>&emsp; + Tạo Transit Gateway Route Tables <br>&emsp; + Thêm Transit Gateway Routes vào VPC Route Tables <br>&emsp; + Dọn dẹp tài nguyên                | 28/08/2025   | 28/08/2025      | <https://000020.awsstudygroup.com/vi/> |
| 6   | - Triển khai Wordpress trên AWS Cloud <br>&emsp;**Thực hành:** <br>&emsp; + Chuẩn bị VPC và Subnet <br>&emsp; + Tạo Security Group cho EC2 <br>&emsp; + Tạo Security Group cho Database Instancevolume <br>&emsp; + Khởi tạo EC2 Instance <br>&emsp; + Khởi tạo Database Instance                                                                                        | 29/08/2025   | 29/08/2025      | https://000021.awsstudygroup.com/> |


### Kết quả đạt được tuần 3:

* Tìm hiểu Networking – VPC Peering
  * Khởi tạo CloudFormation Template cho môi trường thử nghiệm
  * Tạo Security Group cho EC2 instance
  * Tạo EC2 instance phục vụ kết nối Peering
  * Cập nhật Network ACL để đảm bảo kết nối giữa các subnet
  * Tạo kết nối VPC Peering giữa hai VPC
  * Kích hoạt Cross-Peer DNS Resolution để phân giải tên miền qua Peering
  * Thực hiện dọn dẹp tài nguyên sau khi kiểm tra thành công


* Tìm hiểu Networking – AWS Transit Gateway
  * Hiểu được vai trò của Transit Gateway trong việc kết nối nhiều VPC và on-premise networks
  * Tạo, gắn và quản lý Transit Gateway Attachments cũng như Route Tables để điều hướng traffic tập trung.
  * Đảm bảo việc định tuyến hoạt động ổn định và dễ mở rộng hơn so với VPC Peering.

* Thực hành bước đầu triển khai Wordpress trên AWS Cloud:
  * Triển khai thành công môi trường Wordpress với EC2 Instance (ứng dụng) và Database Instance (MySQL/RDS).
  * Thiết lập hệ thống mạng (VPC, Subnet) và phân quyền bảo mật bằng Security Groups để đảm bảo an toàn cho ứng dụng.
  * Kết nối được giữa ứng dụng Wordpress và cơ sở dữ liệu, chạy thử nghiệm thành công.

