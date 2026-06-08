# Mindwell
Serverless AI emotional wellness platform built on AWS: submitted to the AWS Prompt the Planet Challenge
# Mind-well — AI Emotional Wellness Agent

> *Helping people understand and manage their emotions by turning daily thoughts into structured reflection, mood awareness, and gentle self-care guidance.*

---

## Overview

Mind-well is a serverless AI emotional wellness platform that helps users journal daily thoughts, track emotional patterns, and receive personalised reflections. Users simply type how they feel and the app responds with structured emotional insight, mood summaries, and gentle self-care suggestions.

The platform addresses a real problem — many people struggle to process their emotions, and traditional journaling lacks guidance. Mind-well solves this using AI to analyse emotional tone, generate meaningful reflections, and optionally connect users with peer support communities.

---

## The Problem

People often experience emotions without fully understanding them. This can lead to:
- Stress and emotional overwhelm
- Difficulty expressing feelings
- Lack of self-awareness over time
- Emotional isolation

Existing journaling tools lack emotional intelligence and do not guide reflection in a meaningful way.

---

## The Solution

Mind-well acts as an AI emotional reflection companion. Instead of unstructured journaling, users receive:
- Guided emotional analysis
- Structured reflection and reframing
- Gentle self-care suggestions
- Optional peer community support

---

## AWS Architecture

This project uses a fully serverless AWS backend — no servers to manage, scales automatically, and costs near zero at low usage.

### Services Used

| Service | Purpose |
|---|---|
| AWS Lambda | Processes journal entries and generates AI reflections |
| API Gateway | Exposes REST endpoints for the frontend |
| DynamoDB | Stores journal entries and emotional history |
| SNS | Sends wellness reminder notifications |
| S3 | Stores guided wellness content and resources |
| Cognito | Handles user authentication and login |
| CloudWatch | Monitors app health and logs activity |
| X-Ray | Traces requests through the system |
| IAM | Controls permissions with least privilege |

### Architecture Diagram

```
User App
    │
    ▼
API Gateway
    │
    ├── POST /journal ──────► Lambda (mindwell-processor)
    │                               │
    ├── GET /history/{userId} ──────┤──► DynamoDB (mindwell-entries)
    │                               │
    └── POST /reflect ─────────────┘──► SNS (mindwell-notifications)
                                        S3 (mindwell-resources)
```

---

## The Prompt

Use this prompt with any AI assistant (Claude, Kiro, ChatGPT) to deploy the complete Mind-well AWS backend:

```
Create a production-ready serverless AI emotional wellness application on AWS with the following specifications:

INFRASTRUCTURE SETUP:
1. Create an AWS Lambda function (Python 3.12) named "mindwell-processor" with 512MB memory and 30 second timeout
2. Create an API Gateway REST API named "mindwell-api" with the following endpoints:
   - POST /journal - accepts user journal entries
   - GET /history/{userId} - retrieves emotional history
   - POST /reflect - triggers AI reflection generation
3. Create a DynamoDB table named "mindwell-entries" with:
   - Partition key: userId (String)
   - Sort key: timestamp (String)
   - Enable TTL on attribute "expiry"
   - Enable point-in-time recovery
4. Create an SNS topic named "mindwell-notifications" for wellness reminders
5. Create an S3 bucket named "mindwell-resources" for storing guided wellness content

SECURITY:
- Create an IAM role "mindwell-lambda-role" with least privilege permissions
- Enable API Gateway authentication using Cognito User Pool
- Enable encryption at rest for DynamoDB and S3
- Enable CloudWatch logging for all Lambda invocations
- Block all public S3 access

MONITORING:
- Create CloudWatch alarms for Lambda errors exceeding 5 per minute
- Enable X-Ray tracing on Lambda and API Gateway
- Create a CloudWatch dashboard named "mindwell-health"

COST CONTROLS:
- Set Lambda reserved concurrency to 10
- Enable DynamoDB on-demand billing
- Set S3 lifecycle policy to transition objects to Glacier after 90 days
```

---

## Prerequisites

- AWS account with admin permissions
- AWS CLI configured locally
- Python 3.12 runtime available in your region

---

## Expected Outcome

A fully deployed serverless wellness application backend with:
- Secure REST API endpoints
- Encrypted data storage
- User authentication
- Monitoring dashboards
- Cost controls

Production ready in under 10 minutes.

---

## Troubleshooting

| Issue | Fix |
|---|---|
| Lambda times out | Increase timeout to 60 seconds |
| DynamoDB throttling | Switch from provisioned to on-demand billing |
| API Gateway returns 403 | Check Cognito User Pool is correctly attached |

---

## Well-Architected Framework Alignment

- **Security** — Least privilege IAM, encryption at rest, Cognito authentication
- **Reliability** — Point-in-time recovery, CloudWatch alarms
- **Cost Optimisation** — On-demand billing, S3 Glacier lifecycle policies
- **Operational Excellence** — X-Ray tracing, CloudWatch dashboards

---

## Safety & Boundaries

- Does NOT provide medical diagnosis
- Does NOT replace therapy or professional care
- Avoids harmful or directive medical advice
- Focus is emotional support, reflection, and wellbeing only

---

## Future Extensions

- Anonymous peer support groups
- AI-moderated community spaces
- Emotional trend tracking dashboards
- Guided audio wellness sessions
- Gentle habit reminders

---

## Submitted To

AWS Prompt the Planet Challenge — DoraHacks (June 2026)
Prize pool: $50,000 in AWS Activate Credits

---

*Built by Trudy Foster | AWS Certified Solutions Architect Associate | AWS Certified Cloud Practitioner*
