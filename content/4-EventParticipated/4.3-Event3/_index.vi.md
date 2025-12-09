---
title: "Event 3"
date: 2025-11-29
weight: 1
chapter: false
pre: " <b> 4.3. </b> "
---



# Bài thu hoạch “AWS Well-Architected Security Pillar”

### Mục Đích Của Sự Kiện

- Nắm vai trò Security Pillar trong Well-Architected và các nguyên tắc: Least Privilege, Zero Trust, Defense in Depth
- Hiểu Shared Responsibility Model và các mối đe doạ cloud phổ biến tại Việt Nam
- Thực hành IAM, Detection, Infrastructure Protection, Data Protection, Incident Response ở mức nền tảng

### Danh Sách Diễn Giả

- AWS Solutions Architect Team – Security Specialists
- AWS Security & Compliance Experts
- AWS Cloud Operations Team

### Nội Dung Nổi Bật

#### Opening & Security Foundation (8:30 – 8:50)
- Security Pillar trong Well-Architected; nguyên tắc cốt lõi: least privilege, zero trust, defense in depth
- Shared Responsibility Model; top threats trong môi trường cloud tại Việt Nam

#### Pillar 1 — Identity & Access Management (8:50 – 9:30)
- IAM: Users, Roles, Policies; tránh long-term credentials
- IAM Identity Center: SSO, permission sets; SCP & permission boundaries cho multi-account
- MFA, credential rotation, Access Analyzer; mini demo validate/simulate policy

#### Pillar 2 — Detection (9:30 – 9:55)
- CloudTrail (org-level), GuardDuty, Security Hub
- Logging đa tầng: VPC Flow Logs, ALB/S3 logs; alerting & automation với EventBridge
- Detection-as-Code: hạ tầng + rule kiểm soát

#### Coffee Break (9:55 – 10:10)

#### Pillar 3 — Infrastructure Protection (10:10 – 10:40)
- VPC segmentation; public vs private placement
- Security Groups vs NACLs: mô hình áp dụng
- WAF + Shield + Network Firewall; bảo vệ workload EC2/ECS/EKS cơ bản

#### Pillar 4 — Data Protection (10:40 – 11:10)
- KMS: key policies, grants, rotation
- Mã hoá at-rest & in-transit: S3, EBS, RDS, DynamoDB
- Secrets Manager & Parameter Store: pattern rotation, tách quyền truy cập
- Phân loại dữ liệu và guardrails truy cập

#### Pillar 5 — Incident Response (11:10 – 11:40)
- Quy trình IR của AWS; playbook: compromised IAM key, S3 public exposure, EC2 malware
- Snapshot, isolation, evidence collection; auto-response bằng Lambda/Step Functions

#### Wrap-Up & Q&A (11:40 – 12:00)
- Tổng kết 5 pillars; common pitfalls và thực tế doanh nghiệp Việt Nam
- Roadmap học tập: Security Specialty, SA Pro

### Những Gì Học Được

#### Tư Duy Thiết Kế
- Thiết kế theo least privilege, zero trust, defense in depth; luôn kèm guardrails tổ chức
- Phân định rõ shared responsibility; audit và minh bạch quyền truy cập
- Đặt mục tiêu đo lường: time-to-detect, time-to-contain, coverage logging

#### Kiến Trúc Kỹ Thuật
- IAM chuẩn: SSO/Identity Center, ngắn hạn credentials, MFA bắt buộc
- Ghi log tập trung: org-level CloudTrail, VPC Flow Logs, ALB/S3 logs; GuardDuty + Security Hub
- Bảo vệ mạng & workload: SG/NACL đúng tầng, WAF/Shield/Network Firewall, baseline cho ECS/EKS/EC2
- Mã hoá & bí mật: KMS key policy rõ ràng, rotation, Secrets Manager/Parameter Store

#### Chiến Lược Vận Hành
- Detection-as-Code và auto-remediation với EventBridge + Lambda/Step Functions
- Playbook IR sẵn sàng: khóa/rotate key, cô lập instance, chụp bằng chứng
- Lộ trình kỹ năng/cert: Security Specialty, SA Pro; luyện tập tabletop

### Ứng Dụng Vào Công Việc
- Bật org-level CloudTrail, GuardDuty, Security Hub; thiết lập alerting qua EventBridge
- Chuẩn hoá IAM: MFA bắt buộc, SSO/permission sets, SCP/permission boundary cho multi-account
- Thiết kế mạng: tách public/private, SG theo nguyên tắc tối thiểu, review NACL
- Bật mã hoá và quản lý key với KMS; dùng Secrets Manager/Parameter Store kèm rotation
- Viết playbook IR cho: IAM key lộ, S3 public, EC2 nghi malware; tự động hoá bước cô lập và thu thập bằng chứng

### Trải nghiệm trong event
- Nghe chuyên gia chia sẻ threat thực tế tại VN và cách map vào 5 pillars
- Xem demo simulate IAM policy và kích hoạt dịch vụ phát hiện/giám sát
- Thảo luận playbook IR và cách tự động hoá phản ứng ban đầu


