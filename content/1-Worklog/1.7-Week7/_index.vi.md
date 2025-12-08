---
title: "Worklog Tuần 7"
date: 2025-10-20
weight: 1
chapter: false
pre: " <b> 1.7. </b> "
---



### Mục tiêu tuần 7:

* Quản lý truy cập vào dịch vụ EC2 Resource Tag với AWS IAM.
* Bắt đầu với Grafana trên AWS
* GIỚI HẠN QUYỀN CỦA USER VỚI IAM PERMISSION BOUNDARY

### Các công việc cần triển khai trong tuần này:
| Thứ | Công việc                                                                                                                                                                                   | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu                            |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------ | --------------- | ----------------------------------------- |
| 2   | - Quản lý truy cập vào dịch vụ EC2 Resource Tag với AWS IAM <br> - Tạo các chính sách với các role có thể được sử dụng bởi một số người dùng <br>&emsp; + Tạo IAM User <br>&emsp; + Tạo IAM Policy <br>&emsp;**Thực hành:**  <br>&emsp; + Tạo IAM Role    <br>&emsp; + Đăng nhập vào AWS Management Console và truy cập đến IAM Management Console. <br>&emsp; + Create role   <br>&emsp; + Tiến hành tạo một IAM role cho người dùng EC2 Administrator cùng với những chính sách đã được tạo ra ở phần trước.                                                              | 20/10/2025   | 20/10/2025      |<https://000028.awsstudygroup.com>
| 3   | -  Quản lý truy cập vào dịch vụ EC2 Resource Tag với AWS IAM. <br>- Kiểm tra chính sách<br>&emsp; + Chuyển Role <br>&emsp; + Kiểm tra IAM Policy<br>&emsp; + Tiến hành truy cập EC2 console ở AWS Region - Tokyo <br>&emsp; + Tiến hành truy cập EC2 console ở AWS Region - North Virginia <br>&emsp; + Tiến hành tạo EC2 instance khi không có và có Tags thỏa điều kiện<br>&emsp; + Chỉnh sửa Resource Tag trên EC2 Instance<br>&emsp; + Kiểm tra chính sách <br>&emsp; + Dọn dẹp tài nguyên                                 | 21/10/2025   | 21/10/2025      | <https://000028.awsstudygroup.com> |
| 4   | - Bắt đầu với Grafana trên AWS <br>- Các bước chuẩn bị: <br>&emsp;**Thực hành:** <br>&emsp;  + Tạo VPC và subnet <br>&emsp; +   Tạo Security Group  <br>&emsp; + Tạo EC2 Instance <br>&emsp; + Tạo IAM User <br>&emsp; + Tạo IAM Role <br>&emsp; + Gán IAM Role<br>- Cài đặt Grafana<br>- Giám sát với Grafana  | 22/10/2025   | 22/10/2025      | <https://000029.awsstudygroup.com> |
| 5   | - GIỚI HẠN QUYỀN CỦA USER VỚI IAM PERMISSION BOUNDARY  <br>- Chuẩn bị tài khoản AWS có thể sử dụng IAM. <br>&emsp; + Create Policy <br>&emsp; + Copy đoạn JSON trong bài workshop vào khung <br>&emsp; + Bỏ qua bước gán tag và chọn Next: Review<br>&emsp; + Đặt tên policy là ec2-admin-restrict-region.       | 23/10/2025   | 23/10/2025       | <https://000030.awsstudygroup.com/vi/3-createpolicy> |
| 6   | - GIỚI HẠN QUYỀN CỦA USER VỚI IAM PERMISSION BOUNDARY <br>&emsp;**Thực hành:** <br>&emsp; + Tạo một IAM user và áp giới hạn quyền lên user <br>&emsp; + Kiểm tra IAM User Giới Hạn <br>&emsp; + Kiểm tra xem liệu user được gán quyền AmazonEC2FullAccess có bị giới hạn quyền bởi Permission Boundary hay không <br>&emsp; + Dọn dẹp tài nguyên                                                                                        | 24/10/2025   | 24/10/2025      | <https://000030.awsstudygroup.com/vi/3-createpolicy>|


### Kết quả đạt được tuần 7:

* Quản lý truy cập dịch vụ EC2 với AWS IAM (Resource Tag)n: 
  * Hiểu và áp dụng cơ chế IAM Policy để kiểm soát quyền truy cập EC2 dựa trên Resource Tag.
  * Tạo và gán IAM Role/Policy cho user, qua đó giới hạn khả năng thao tác EC2 instance theo tag được định nghĩa.
  * Thực hiện kiểm tra thành công chính sách bằng cách tạo/sửa EC2 instance ở các region khác nhau


* Bắt đầu với Grafana trên AWS
  * Cài đặt và triển khai Grafana trên EC2.
  * Hiểu cơ chế gán IAM Role và tích hợp giám sát dữ liệu.
  * Xây dựng môi trường giám sát cơ bản với Grafana, phục vụ theo dõi hệ thống và ứng dụng AWS trực quan hơn.

* Giới hạn quyền với IAM Permission Boundary:

  * Tìm hiểu khái niệm Permission Boundary để kiểm soát phạm vi tối đa quyền hạn của IAM User.
  * Triển khai chính sách giới hạn quyền
  * Kiểm tra thành công: dù user được cấp quyền AmazonEC2FullAccess, vẫn bị giới hạn thao tác ngoài phạm vi cho phép.



