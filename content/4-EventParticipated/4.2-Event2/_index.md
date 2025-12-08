---
title: "Event 2"
date: 2025-09-30
weight: 1
chapter: false
pre: " <b> 4.2. </b> "
---

{{% notice warning %}}
⚠️ **Note:** The information below is for reference purposes only. Please **do not copy it verbatim** into your report, including this warning.
{{% /notice %}}

# Summary Report: “DevOps on AWS”

### Event Objectives

- Shape DevOps mindset, culture, and metrics (DORA, MTTR, deployment frequency)
- Learn AWS DevOps services: CodeCommit, CodeBuild, CodeDeploy, CodePipeline
- Practice IaC with CloudFormation/CDK and compare IaC tool choices
- Bridge prior AI/ML learnings into CI/CD, observability, and operations

### Speakers

- AWS Specialist / Solutions Architect for DevOps & Containers (names TBD)

### Key Highlights

#### Welcome & DevOps Mindset (8:30 – 9:00)

- Quick recap of prior AI/ML session; align DevOps goals
- DevOps culture & principles; benefits and key metrics (DORA, MTTR, deployment frequency)

#### AWS DevOps Services – CI/CD Pipeline (9:00 – 10:30)

- Source control: CodeCommit; GitFlow vs Trunk-based strategies
- Build & test: CodeBuild pipeline configuration
- Deploy: CodeDeploy with blue/green, canary, rolling
- Orchestration: CodePipeline end-to-end automation
- Demo: full CI/CD pipeline walkthrough

#### Break (10:30 – 10:45)

#### Infrastructure as Code (10:45 – 12:00)

- CloudFormation: templates, stacks, drift detection
- AWS CDK: constructs, reusable patterns, language support
- Demo: deploy with CloudFormation & CDK; discuss IaC tool selection

#### Lunch (12:00 – 13:00) – self-arranged

#### Container Services on AWS (13:00 – 14:30)

- Docker fundamentals, microservices & containerization
- ECR: image storage, scanning, lifecycle policies
- ECS & EKS: deployment strategies, scaling, orchestration
- App Runner: simplified container deployment
- Demo & case study: microservices deployment comparison

#### Break (14:30 – 14:45)

#### Monitoring & Observability (14:45 – 16:00)

- CloudWatch: metrics, logs, alarms, dashboards
- X-Ray: distributed tracing and performance insights
- Demo: full-stack observability setup; alerting/on-call best practices

#### DevOps Best Practices & Case Studies (16:00 – 16:45)

- Deployment strategies: feature flags, A/B testing
- Automated testing & CI/CD integration
- Incident management and postmortems; startup/enterprise case studies

#### Q&A & Wrap-up (16:45 – 17:00)

- DevOps career pathways; AWS certification roadmap

### Key Takeaways

#### Design Mindset

- DevOps is culture and process: prioritize flow, feedback, continuous learning
- Measure with DORA/MTTR/deploy frequency; set guardrails to enable, not block
- Connect AI/ML pipelines into CI/CD for fast but safe releases

#### Technical Architecture

- Design CI/CD with CodeCommit/CodeBuild/CodeDeploy/CodePipeline
- Choose deployment strategies: blue/green, canary, rolling; add feature flags/A-B testing
- IaC: CloudFormation vs CDK, drift detection, reusable constructs
- Full-stack observability: CloudWatch metrics/logs/alarms + X-Ray tracing

#### Modernization Strategy

- Container-first: ECR + ECS/EKS; App Runner for quick service deployments
- Standardize security/compliance in pipelines (image scanning, policy, least privilege)
- Skills and certification path for AWS DevOps; plan PoC → pilot → production

### Applying to Work

- Set up a sample CI/CD repo with CodeCommit + CodeBuild + CodeDeploy + CodePipeline
- Apply blue/green or canary to existing services; add feature flags to reduce risk
- Write IaC with CDK for a small workload; compare with CloudFormation templates
- Standardize observability: CloudWatch dashboards/alarms, X-Ray for key traces
- Manage images in ECR: enable scan, lifecycle policies to clean old images

### Event Experience

Attending **“DevOps on AWS”** connected prior AI/ML learnings with CI/CD, IaC, containers, and observability.

#### Learning from speakers
- Git strategies, CI/CD pipelines, and safe deployments (blue/green, canary)
- CloudFormation vs CDK, drift detection, reusable constructs

#### Technical exposure
- End-to-end pipeline demo with CodePipeline + CodeBuild + CodeDeploy
- IaC deployment demo with CloudFormation and CDK
- Observability demo: CloudWatch metrics/logs/alarms + X-Ray tracing

#### Practical application
- Clear approach to standardize pipelines and IaC for current projects
- How to enable scan/lifecycle for ECR and deploy/scale on ECS/EKS/App Runner

#### Lessons learned
- Measure DevOps with DORA/MTTR and design safe pipelines from day one
- IaC and observability are foundations to scale teams and reduce deployment risk

