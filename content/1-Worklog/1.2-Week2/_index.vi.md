---
title: "Worklog Tuần 2"
date: 2025-08-18
weight: 1
chapter: false
pre: " <b> 1.2. </b> "
---

### Mục tiêu tuần 2:

* Nat Gateway
* Khám phá AWS Budgets
* Chuyển đổi IAM Role
* Thiết lập Hybrid DNS với Route 53 Resolver

### Các công việc cần triển khai trong tuần này:
| Thứ | Công việc                                                                                                                                                                                   | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu                            |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------ | --------------- | ----------------------------------------- |
| 2   | - Nat Gateway   <br>&emsp; + Tạo Elastic IP<br>&emsp; + Triển khai NAT Gateway <br>&emsp; + Cấu hình Route Table cho Private Subnet                                                                                   | 18/08/2025   | 18/08/2025      | <https://000003.awsstudygroup.com/vi/4-createec2server/4.2-connectec2/> |
| 3   | - Khám phá AWS Budgets <br>&emsp; +  Tạo Budget <br>&emsp; +  Tạo Cost Budget                                           | 19/08/2025   | 19/08/2025      | <https://000007.awsstudygroup.com/vi/2-usage-budget> |
| 4   | - Chuyển đổi IAM Role <br>&emsp; + Tạo IAM Group và IAM User <br>&emsp; +  Tạo IAM Role và IAM User <br>&emsp; + Chuyển đổi IAM Role | 20/08/2025   | 20/08/2025      | <https://000002.awsstudygroup.com/vi/4-switch-roles> |
| 5   | - Thiết lập Hybrid DNS với Route 53 Resolver <br>&emsp; + Thiết lập Hybrid DNS với Route 53 Resolver và kiểm tra tên miền <br>&emsp; + Tạo Key Pair <br>&emsp; + Khởi tạo CloudFormation Template <br> | 21/08/2025   | 21/08/2025      | <https://000010.awsstudygroup.com/vi/2-prerequiste> |
| 6   | - Thiết lập Hybrid DNS với Route 53 Resolver<br>&emsp; + Cấu hình Security Group <br>&emsp; + Kết nối RDGW <br>&emsp; + Cài đặt <br>&emsp; + Tạo Route 53 Outbound EndpointDNSvolume                                                                                         | 22/08/2025   | 22/08/2025      | <https://000010.awsstudygroup.com> |


### Kết quả đạt được tuần 2:

* Nắm vững và triển khai các dịch vụ AWS ở mức cơ bản: 
  * Hiểu và triển khai NAT Gateway:
  * Tạo Elastic IP
  * Tạo và cấu hình NAT Gateway 
  * Cập nhật Route Table cho Private Subnet để đảm bảo kết nối Internet cho instances.

* Quản lý chi phí (Cost Management):
  * Làm quen với AWS Budgets
  * Tạo Budget cơ bản
  * Tạo Cost Budget theo yêu cầu để theo dõi và kiểm soát chi phí.

 * Cập nhật Route Table cho Private Subnet để đảm bảo kết nối Internet cho instances.

  * Thực hành chuyển đổi IAM Role:
    * Tạo IAM Group và IAM User
    * Tạo IAM Role
    * Thực hiện Switch Role thành công để quản lý quyền truy cập linh hoạt.

* Thiết lập Hybrid DNS với Route 53 Resolver:
  * Cấu hình Hybrid DNS và kiểm tra phân giải tên miền
  * Tạo Key Pair & khởi tạo CloudFormation Template
  * Cấu hình Security Group, kết nối RDGW, cài đặt môi trường
  * Tạo Route 53 Outbound Endpoint và kiểm tra hoạt động.


