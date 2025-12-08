---
title: "Event 1"
date: 2025-09-30
weight: 1
chapter: false
pre: " <b> 4.1. </b> "
---


# Summary Report: “AWS AI/ML & Bedrock Workshop”

### Event Objectives

- Network and clarify learning goals; understand the AI/ML landscape in Vietnam
- Get an overview of AWS AI/ML services with focus on SageMaker (end-to-end ML) and Bedrock (GenAI)
- Align objectives from data prep, training/deploy to building a GenAI chatbot

### Speakers

- **Kha Van** 
- **Kiet Lam** 
- **Aiden Dinh**

### Key Highlights

#### Welcome & Introduction (8:30 – 9:00)

- Registration, networking, sharing PoC expectations
- Ice-breaker to surface use cases: internal knowledge chatbot, document classification, CS automation
- Snapshot of local AI/ML landscape: data security needs, GenAI opportunities

#### AWS AI/ML Services Overview (9:00 – 10:30)

- **Amazon SageMaker**: data prep, labeling, training, tuning, deployment
- **Integrated MLOps**: pipelines, experiment tracking, model registry, canary/blue-green for endpoints
- **Cost optimization**: spot training, endpoint autoscaling, right-size instances
- **Demo SageMaker Studio**: unified notebook + tracking + deploy

#### Coffee Break (10:30 – 10:45)

- Quick discussions on internal use cases and data constraints

#### Generative AI with Amazon Bedrock (10:45 – 12:00)

- **Foundation Models**: Claude, Llama, Titan — selection by use case (reasoning, extensibility, AWS integration)
- **Prompt engineering**: chain-of-thought, few-shot, control length and confidence
- **RAG**: vector store + knowledge base, reduce hallucination, fast data refresh
- **Bedrock Agents**: orchestrate multi-step workflows, integrate external tools/systems
- **Guardrails**: policies to filter sensitive content, PII controls
- **Demo**: build a QA chatbot on enterprise data using Bedrock + RAG

### Key Takeaways

#### Design Mindset

- Start from business problems and internal data before picking models
- Design for safety: guardrails, sensitive-topic filtering, PII controls
- Define metrics: answer quality, time-to-deploy, inference cost

#### Technical Architecture

- MLOps with SageMaker: pipelines, model registry, canary/blue-green endpoints
- RAG for GenAI: choose vector store/knowledge base, data refresh strategy, access controls
- Pragmatic prompt engineering: few-shot, chain-of-thought, control length and confidence

#### Modernization Strategy

- Select Foundation Model per use case (reasoning, extensibility, AWS fit)
- Optimize costs early: spot training, endpoint autoscaling, monitor drift to avoid waste
- Roadmap PoC → pilot → production with safety/compliance checklist

### Applying to Work

- Prepare an internal QA chatbot PoC using Bedrock + RAG on enterprise docs
- Standardize train/tune/deploy with SageMaker; use model registry and canary/blue-green rollout
- Create a prompt-engineering and guardrails checklist for product teams
- Estimate and optimize costs: spot training, autoscaling, monitor drift and quality

### Event Experience

Attending the **AWS AI/ML & Bedrock** workshop clarified how to apply GenAI and MLOps to real problems.

#### Learning from speakers
- Criteria to choose Foundation Models (Claude, Llama, Titan) and operate SageMaker at scale
- How to enforce safety/content controls with guardrails and input/output policies

#### Technical exposure
- Demo of SageMaker Studio: notebook + tracking + deploy in one interface
- Demo of Bedrock + RAG chatbot on enterprise data, understanding the ingest → index → query flow

#### Practical application
- Clear path to build an internal knowledge chatbot with Bedrock Agents and RAG
- How to set autoscaling/cost controls and canary/blue-green for SageMaker endpoints

#### Lessons learned
- Begin with business/data and guardrails before scaling models
- Standardize ML/GenAI lifecycle with pipelines, registry, drift and quality monitoring

