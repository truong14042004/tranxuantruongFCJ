---
title: "Event 3"
date: 2025-11-29
weight: 1
chapter: false
pre: " <b> 4.3. </b> "
---


# Summary Report: “AWS Well-Architected Security Pillar”

### Event Objectives

- Understand the Security Pillar in Well-Architected and core principles: Least Privilege, Zero Trust, Defense in Depth
- Clarify the Shared Responsibility Model and common cloud threats in Vietnam
- Practice IAM, Detection, Infrastructure Protection, Data Protection, and Incident Response at a foundational level

### Speakers

- AWS Solutions Architect Team – Security Specialists
- AWS Security & Compliance Experts
- AWS Cloud Operations Team

### Key Highlights

#### Opening & Security Foundation (8:30 – 8:50)
- Role of the Security Pillar; core principles: least privilege, zero trust, defense in depth
- Shared Responsibility Model; top cloud threats in Vietnam

#### Pillar 1 — Identity & Access Management (8:50 – 9:30)
- IAM: Users, Roles, Policies; avoid long-term credentials
- IAM Identity Center: SSO, permission sets; SCP and permission boundaries for multi-account
- MFA, credential rotation, Access Analyzer; mini demo to validate/simulate policy

#### Pillar 2 — Detection (9:30 – 9:55)
- CloudTrail (org-level), GuardDuty, Security Hub
- Multi-layer logging: VPC Flow Logs, ALB/S3 logs; alerting and automation with EventBridge
- Detection-as-Code: infrastructure + control rules

#### Coffee Break (9:55 – 10:10)

#### Pillar 3 — Infrastructure Protection (10:10 – 10:40)
- VPC segmentation; public vs private placement
- Security Groups vs NACLs: application models
- WAF + Shield + Network Firewall; baseline workload protection for EC2/ECS/EKS

#### Pillar 4 — Data Protection (10:40 – 11:10)
- KMS: key policies, grants, rotation
- Encryption at-rest & in-transit: S3, EBS, RDS, DynamoDB
- Secrets Manager & Parameter Store: rotation patterns, separated access
- Data classification and access guardrails

#### Pillar 5 — Incident Response (11:10 – 11:40)
- AWS IR lifecycle; playbooks: compromised IAM key, S3 public exposure, EC2 malware
- Snapshot, isolation, evidence collection; auto-response with Lambda/Step Functions

#### Wrap-Up & Q&A (11:40 – 12:00)
- Recap of 5 pillars; common pitfalls and Vietnam enterprise realities
- Security learning roadmap: Security Specialty, SA Pro

### Key Takeaways

#### Design Mindset
- Design with least privilege, zero trust, defense in depth; enforce org-level guardrails
- Make shared responsibility explicit; audit and transparency for access
- Track metrics: time-to-detect, time-to-contain, logging coverage

#### Technical Architecture
- Solid IAM: SSO/Identity Center, short-lived credentials, mandatory MFA
- Centralized logging: org-level CloudTrail, VPC Flow Logs, ALB/S3 logs; GuardDuty + Security Hub
- Network & workload protection: SG/NACL per layer, WAF/Shield/Network Firewall, baselines for ECS/EKS/EC2
- Encryption & secrets: clear KMS key policies, rotation, Secrets Manager/Parameter Store

#### Operational Strategy
- Detection-as-Code and auto-remediation with EventBridge + Lambda/Step Functions
- Ready IR playbooks: rotate/lock keys, isolate instances, capture evidence
- Skills/cert path: Security Specialty, SA Pro; tabletop practice

### Applying to Work
- Enable org-level CloudTrail, GuardDuty, Security Hub; wire alerts via EventBridge
- Standardize IAM: enforce MFA, SSO/permission sets, SCP/permission boundaries for multi-account
- Network design: separate public/private, principle-of-least-privilege SGs, review NACLs
- Turn on encryption and manage keys with KMS; use Secrets Manager/Parameter Store with rotation
- Write IR playbooks for leaked IAM key, public S3, suspected EC2 malware; automate isolation and evidence capture

### Event Experience
- Learned how local threats map to the 5 pillars from AWS security experts
- Saw demos on IAM policy simulation and enabling detection/monitoring services
- Discussed IR playbooks and automating first-response steps

