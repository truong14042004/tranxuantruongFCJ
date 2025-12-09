---
title: "Event 2"
date: 2025-09-30
weight: 1
chapter: false
pre: " <b> 4.2. </b> "
---



# Bài thu hoạch “DevOps on AWS”

### Mục Đích Của Sự Kiện

- Định hình tư duy DevOps, văn hoá và metrics (DORA, MTTR, tần suất deploy)
- Nắm bộ dịch vụ DevOps trên AWS: CodeCommit, CodeBuild, CodeDeploy, CodePipeline
- Thực hành IaC với CloudFormation/CDK; so sánh IaC tools
- Ôn lại AI/ML phiên trước và kết nối vào CI/CD, quan sát, vận hành

### Danh Sách Diễn Giả

- AWS Solutions Architect Team – DevOps Specialists
- AWS Container Services Experts
- AWS Observability and Cloud Operations Team

### Nội Dung Nổi Bật

#### Welcome & DevOps Mindset (8:30 – 9:00)

- Recap nhanh phiên AI/ML trước; đặt mục tiêu kết nối AI/ML với DevOps
- DevOps culture & principles; lợi ích và metrics chính (DORA, MTTR, deployment frequency)

#### AWS DevOps Services – CI/CD Pipeline (9:00 – 10:30)

- Source Control: CodeCommit, chiến lược GitFlow vs Trunk-based
- Build & Test: CodeBuild cấu hình build/test pipeline
- Deploy: CodeDeploy với blue/green, canary, rolling
- Orchestration: CodePipeline tự động hoá CI/CD end-to-end
- Demo: walkthrough đầy đủ pipeline

#### Break (10:30 – 10:45)

- Trao đổi nhanh về bài toán và rào cản hiện tại

#### Infrastructure as Code (10:45 – 12:00)

- CloudFormation: template, stack, drift detection
- AWS CDK: constructs, reusable patterns, language support
- Demo: deploy với CloudFormation & CDK; thảo luận chọn công cụ IaC

#### Lunch (12:00 – 13:00) – tự túc

#### Container Services on AWS (13:00 – 14:30)

- Docker fundamentals, microservices & containerization
- ECR: image storage, scanning, lifecycle policies
- ECS & EKS: chiến lược triển khai, scaling, orchestration
- App Runner: triển khai container đơn giản
- Demo & case study: so sánh triển khai microservices

#### Break (14:30 – 14:45)

#### Monitoring & Observability (14:45 – 16:00)

- CloudWatch: metrics, logs, alarms, dashboards
- X-Ray: distributed tracing & performance insights
- Demo: thiết lập observability full-stack; best practices alerting/on-call

#### DevOps Best Practices & Case Studies (16:00 – 16:45)

- Deployment strategies: feature flags, A/B testing
- Automated testing & CI/CD integration
- Incident management & postmortems; case studies startup/enterprise

#### Q&A & Wrap-up (16:45 – 17:00)

- DevOps career pathways, AWS certification roadmap

### Những Gì Học Được

#### Tư Duy Thiết Kế

- DevOps là văn hoá và quy trình: ưu tiên flow, feedback, học hỏi liên tục
- Đo lường bằng DORA/MTTR/deploy frequency; chuẩn hoá guardrails thay vì cản trở
- Kết nối AI/ML pipeline với CI/CD để ra mắt tính năng nhanh nhưng an toàn

#### Kiến Trúc Kỹ Thuật

- Thiết kế pipeline CI/CD với CodeCommit/CodeBuild/CodeDeploy/CodePipeline
- Chọn chiến lược triển khai: blue/green, canary, rolling; kết hợp feature flags/A-B testing
- IaC: CloudFormation vs CDK, phát hiện drift và tái sử dụng constructs
- Observability full-stack: CloudWatch metrics/logs/alarms + X-Ray tracing

#### Chiến Lược Hiện Đại Hóa

- Container-first: ECR + ECS/EKS; App Runner cho triển khai nhanh dịch vụ nhẹ
- Chuẩn hoá bảo mật và compliance trong pipeline (scan image, policy, least privilege)
- Lộ trình kỹ năng & chứng chỉ AWS DevOps; plan PoC → pilot → prod

### Ứng Dụng Vào Công Việc

- Thiết lập repo mẫu CI/CD với CodeCommit + CodeBuild + CodeDeploy + CodePipeline
- Áp dụng blue/green hoặc canary cho dịch vụ hiện có; thêm feature flag để giảm rủi ro
- Viết IaC bằng CDK cho một workload nhỏ; so sánh với CloudFormation template
- Chuẩn hoá observability: CloudWatch dashboards/alarms, X-Ray cho trace chính
- Quản lý image tại ECR: enable scan, lifecycle policy để dọn dẹp image cũ

### Trải nghiệm trong event

Tham gia workshop **“DevOps on AWS”** giúp kết nối kiến thức AI/ML trước đó với thực hành CI/CD, IaC, containers và observability.

#### Học hỏi từ các diễn giả
- Nghe chia sẻ về chiến lược Git, pipeline CI/CD, và triển khai an toàn (blue/green, canary)
- So sánh CloudFormation vs CDK và cách phát hiện/drift, tái sử dụng constructs

#### Trải nghiệm kỹ thuật
- Xem demo pipeline CodePipeline + CodeBuild + CodeDeploy end-to-end
- Demo IaC triển khai hạ tầng bằng CloudFormation và CDK
- Demo observability: CloudWatch metrics/logs/alarms + X-Ray tracing

#### Ứng dụng thực tế
- Hình dung rõ cách chuẩn hoá pipeline và IaC cho dự án hiện tại
- Biết cách bật scan/lifecycle cho ECR, cấu hình scaling/triển khai trên ECS/EKS/App Runner

#### Bài học rút ra
- DevOps cần đo lường bằng DORA/MTTR và thiết kế pipeline an toàn ngay từ đầu
- IaC và observability là nền tảng để scale đội ngũ và giảm rủi ro triển khai

