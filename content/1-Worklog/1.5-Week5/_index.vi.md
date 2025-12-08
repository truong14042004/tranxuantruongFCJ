---
title: "Worklog Tuần 5"
date: 2025-10-06
weight: 1
chapter: false
pre: " <b> 1.5. </b> "
---


### Mục tiêu tuần 5:

* Làm quen S3 bucket và tạo EC2 Instance sử dụng AMI Storage Gateway.
* Triển khai ứng dụng FCJ Management với Auto Scaling Group.
* Thực hành với Amazon CloudWatch

### Các công việc cần triển khai trong tuần này:
| Thứ | Công việc                                                                                                                                                                                   | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu                            |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------ | --------------- | ----------------------------------------- |
| 2   | -  Làm quen S3 bucket và tạo EC2 Instance sử dụng AMI Storage Gateway <br>&emsp; + Tạo S3 Bucket <br>&emsp; + Tạo EC2 cho Storage Gateway  <br>&emsp; + Sử dụng AWS Storage Gateway  <br>&emsp; + Clean resource                                                                    | 06/10/2025   | 06/10/2025      |<https://000024.awsstudygroup.com/1-introduce/>
| 3   | - Triển khai ứng dụng FCJ Management với Auto Scaling Group <br>&emsp; + Thiết lập hạ tầng mạng <br>&emsp; + Khởi tạo EC2 Instance<br>&emsp; + Khởi tạo Database Instance với Amazon RDS <br>&emsp; + Cài đặt dữ liệu cho Database  <br>&emsp; + Triển khai máy chủ web   <br>&emsp; + Chuẩn bị các metric cho Predictive scaling                                   | 07/10/2025   | 07/10/2025      | <https://000006.awsstudygroup.com/vi/6-create-auto-scaling-group/> |
| 4   | - Triển khai ứng dụng FCJ Management với Auto Scaling Group <br>&emsp;**Thực hành:** <br>&emsp;  + Thiết lập Load Balancer <br>&emsp; + Tạo Target Group  <br>&emsp; + Tạo Load Balancer| 08/10/2025   | 08/10/2025      | <https://000006.awsstudygroup.com/vi/6-create-auto-scaling-group/> |
| 5   | - Triển khai ứng dụng FCJ Management với Auto Scaling Group  <br>&emsp; + Kiểm tra kết quả <br>&emsp; + Tạo Auto Scaling Group <br>&emsp; +  Kiểm thử các giải pháp <br>&emsp; + Dọn dẹp tài nguyên            | 09/10/2025   | 09/10/2025       | <https://000006.awsstudygroup.com/vi/6-create-auto-scaling-group/> |
| 6   | -  Thực hành với Amazon CloudWatch <br>&emsp;**Thực hành:** <br>&emsp; + Triển khai CloudFormation Stack <br>&emsp; + CloudWatch Metric <br>&emsp; + CloudWatch Logs <br>&emsp; + CloudWatch Alarms <br>&emsp; + CloudWatch Dashboards <br>&emsp; + Dọn dẹp tài nguyên                                                                                        | 10/10/2025   | 10/10/2025      | <https://000008.awsstudygroup.com/vi/5-cloud-watch-alarm/>|


### Kết quả đạt được tuần 5:

* Làm quen với Amazon S3 và Storage Gateway
  * Tạo và quản lý S3 Bucket thành công.
  * Khởi tạo EC2 Instance để cài đặt và sử dụng AWS Storage Gateway.
  * Hiểu được cách kết nối giữa on-premise storage và cloud thông qua Storage Gateway, hỗ trợ lưu trữ dữ liệu hiệu quả.


* Triển khai ứng dụng FCJ Management với Auto Scaling Group
  * Thiết lập đầy đủ hạ tầng mạng, khởi tạo EC2 Instance và Database Instance (Amazon RDS), triển khai dữ liệu và ứng dụng web.
  * Cấu hình thành công Load Balancer + Target Group, đảm bảo khả năng phân phối tải giữa các instance.
  * Tạo và kiểm thử Auto Scaling Group, hệ thống có khả năng mở rộng và thu hẹp tự động dựa trên tải thực tế.
  * Kiểm tra và đánh giá các giải pháp scaling, đảm bảo ứng dụng hoạt động ổn định và linh hoạt.

* Thực hành với Amazon CloudWatch

  * Tìm hiểu và triển khai CloudWatch Metrics, Logs, Alarms và Dashboards để giám sát hệ thống.
  * Xây dựng được các cảnh báo theo thời gian thực, hỗ trợ việc quản lý và tối ưu tài nguyên AWS hiệu quả.



