---
title: "5. Workshop"
weight: 5
---

# Thiết lập Code PileLine và Code Build cho Elastic Container Registry

### Tổng quan

Thiết lập CodePipeline và CodeBuild cho Amazon ECR là một cách tiếp cận hợp lý và tự động để xây dựng, kiểm thử và triển khai container image vào Elastic Container Registry của bạn. Workshop này sẽ hướng dẫn bạn qua các bước thiết yếu để tạo một quy trình CI/CD hoàn toàn tự động.

Thông qua workshop này, bạn sẽ:

- Hiểu các khái niệm cốt lõi của CodePipeline và CodeBuild
- Học cách cấu hình một pipeline bảo mật và tự động
- Khám phá cách CodeBuild xây dựng và đẩy Docker image lên ECR
- Thực hành thiết lập file buildspec cho các ứng dụng container hóa
- Tự động hóa quy trình lưu trữ và cập nhật image trong ECR

Hãy bắt đầu hành trình tự động hóa việc phân phối container image với CodePipeline và CodeBuild!

### Nội dung chính

1. [Giới thiệu](5.1-Introduction/)
2. [Chuẩn bị](5.2-Preparation/)
3. [Tạo Repository](5.3-CreateRepository/)
4. [Tạo Code Build](5.4-CreateCodeBuild/)
5. [Tạo Code PileLine](5.5-CreateCodePipeline/)
6. [Kết quả kiểm tra](5.6-TestResult/)
7. [Dọn dẹp](5.7-CleanUp/)