---
title: "Event 1"
date: 2025-09-30
weight: 1
chapter: false
pre: " <b> 4.1. </b> "
---



# Bài thu hoạch “AWS AI/ML & Bedrock Workshop”

### Mục Đích Của Sự Kiện

- Đăng ký, networking để hiểu nhu cầu học tập và kết nối nhóm
- Nắm tổng quan landscape AI/ML tại Việt Nam và định vị dịch vụ AWS
- Làm quen bộ dịch vụ trọng tâm: Amazon SageMaker (ML end-to-end) và Amazon Bedrock (GenAI)
- Thống nhất mục tiêu học: từ chuẩn bị dữ liệu, train/deploy đến xây chatbot GenAI

### Danh Sách Diễn Giả

- **Kha Van** 
- **Kiet Lam** 
- **Aiden Dinh** 

### Nội Dung Nổi Bật

#### Welcome & Introduction (8:30 – 9:00)

- Đăng ký, networking, chia sẻ kỳ vọng PoC
- Ice-breaker giúp nhóm hóa bài toán: chatbot tri thức nội bộ, phân loại tài liệu, tự động hóa CSKH
- Phác họa bức tranh AI/ML trong nước: yêu cầu bảo mật dữ liệu, cơ hội áp dụng GenAI

#### AWS AI/ML Services Overview (9:00 – 10:30)

- **Amazon SageMaker**: quy trình chuẩn bị dữ liệu, labeling, training, tuning, deployment
- **MLOps tích hợp**: pipelines, experiment tracking, model registry, canary/blue-green cho endpoint
- **Tối ưu chi phí**: spot training, autoscaling endpoint, chọn instance phù hợp workload
- **Demo SageMaker Studio**: giao diện hợp nhất notebook + tracking + deploy

#### Coffee Break (10:30 – 10:45)

- Thảo luận nhanh về use case nội bộ, rào cản dữ liệu và bảo mật

#### Generative AI với Amazon Bedrock (10:45 – 12:00)

- **Foundation Models**: Claude, Llama, Titan – tiêu chí chọn theo use case (reasoning, mở rộng, tích hợp AWS)
- **Prompt engineering**: chain-of-thought, few-shot, kiểm soát độ dài và độ tự tin
- **RAG**: kiến trúc vector store + knowledge base, giảm hallucination, cập nhật dữ liệu nhanh
- **Bedrock Agents**: orchestrate workflow nhiều bước, tích hợp tools/hệ thống ngoài
- **Guardrails**: policy lọc nội dung nhạy cảm, kiểm soát PII cho input/output
- **Demo**: dựng chatbot hỏi-đáp trên dữ liệu doanh nghiệp bằng Bedrock + RAG

### Những Gì Học Được

#### Tư Duy Thiết Kế

- Luôn xuất phát từ bài toán kinh doanh và dữ liệu nội bộ trước khi chọn mô hình
- Thiết kế trải nghiệm an toàn: guardrails, lọc chủ đề nhạy cảm, kiểm soát PII
- Đặt mục tiêu đo lường: chất lượng trả lời, thời gian triển khai, chi phí inference

#### Kiến Trúc Kỹ Thuật

- Pipeline MLOps với SageMaker: pipelines, model registry, canary/blue-green cho endpoint
- RAG cho GenAI: chọn vector store/knowledge base, chiến lược refresh dữ liệu, kiểm soát quyền truy cập
- Prompt engineering thực dụng: few-shot, chain-of-thought, ràng buộc độ dài và độ tự tin

#### Chiến Lược Hiện Đại Hóa

- Chọn Foundation Model theo use case (reasoning, mở rộng, tích hợp AWS)
- Tối ưu chi phí sớm: spot training, autoscaling endpoint, theo dõi drift để tránh lãng phí
- Lộ trình PoC → pilot → sản xuất với checklist an toàn và tuân thủ

### Ứng Dụng Vào Công Việc

- Chuẩn bị PoC chatbot nội bộ dùng Bedrock + RAG trên tài liệu doanh nghiệp
- Chuẩn hóa train/tune/deploy với SageMaker; dùng model registry và triển khai canary/blue-green
- Thiết lập checklist prompt engineering và guardrails cho nhóm sản phẩm
- Ước tính và tối ưu chi phí: spot training, autoscaling endpoint, giám sát drift và chất lượng

### Trải nghiệm trong event

Tham gia workshop **AWS AI/ML & Bedrock** mang lại góc nhìn rõ ràng về cách áp dụng GenAI và MLOps vào bài toán thực tế.

#### Học hỏi từ diễn giả
- Nghe chia sẻ về tiêu chí chọn Foundation Model (Claude, Llama, Titan) và cách vận hành SageMaker ở quy mô sản xuất
- Nắm cách kiểm soát an toàn/nội dung với guardrails và policy cho input/output

#### Trải nghiệm kỹ thuật
- Xem demo SageMaker Studio: notebook + tracking + deploy trong một giao diện thống nhất
- Theo dõi demo chatbot Bedrock + RAG trên tài liệu doanh nghiệp, hiểu luồng ingest → index → query

#### Ứng dụng thực tế
- Hình dung rõ quy trình dựng PoC chatbot tri thức nội bộ với Bedrock Agents và RAG
- Biết cách thiết lập autoscaling/chi phí và canary/blue-green cho endpoint trong SageMaker

#### Bài học rút ra
- Khởi động bằng bài toán kinh doanh, dữ liệu, và guardrails trước khi mở rộng mô hình
- Chuẩn hóa vòng đời ML/GenAI với pipelines, registry, monitoring drift và chất lượng

