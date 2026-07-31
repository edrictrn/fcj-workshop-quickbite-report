---
title: "Week 6 Worklog"
date: 2026-07-06
weight: 6
chapter: false
pre: " <b> 1.6. </b> "
---

### Week 6 Objectives:

* Research AWS Serverless and Event-Driven concepts: Amazon EventBridge, Amazon SQS, Amazon SNS, and AWS Lambda + Amazon SES for email.
* Design (without deploying) an asynchronous notification path for QuickBite's `OrderCreated` and `OrderStatusChanged` events.
* Evaluate whether the current EC2/RDS/S3/CloudWatch demo actually needs Lambda + SES, or whether Mailpit remains the right fit for this stage.
* Write up the research as an internal design note documenting the proposed future architecture.

### Tasks to be carried out this week:
| Day | Task | Start Date | Completion Date | Reference Material |
| --- | --- | --- | --- | --- |
| 2 | - Learn Serverless concepts, AWS Lambda execution models, and IAM execution roles <br> - **Amazon SES Research:** <br>&emsp; + Read about SES Sandbox, sender identity verification, and sending policies <br>&emsp; + Compare SES against Mailpit for QuickBite's current single-demo-environment scope | 06/07/2026 | 06/07/2026 | - <https://cloudjourney.awsstudygroup.com/> <br> - AWS SES Docs |
| 3 | - **Event-Driven Pattern Research:** <br>&emsp; + Study Amazon EventBridge rule-based routing, Amazon SQS durable queues, and Amazon SNS fan-out <br>&emsp; + Sketch an `OrderCreated` → EventBridge → SQS → Lambda → SES flow as a design exercise | 07/07/2026 | 07/07/2026 | - AWS Lambda Docs <br> - AWS EventBridge Docs |
| 4 | - **Design Problems Worth Documenting:** <br>&emsp; + Work through retries/backoff, idempotency, event ordering, dead-letter queues, and event schema versioning for the proposed flow <br>&emsp; + Decide these are future-roadmap items, not required for the current fixed-capacity demo | 08/07/2026 | 08/07/2026 | - AWS EventBridge DLQ Docs |
| 5 | - **Write the Design Note:** <br>&emsp; + Draft a short internal note on event-driven architecture, explaining how it could decouple email, reporting, and notifications from order creation <br>&emsp; + State explicitly that EventBridge, SQS, Lambda, and SES are **not deployed** in the QuickBite demo | 09/07/2026 | 09/07/2026 | - QuickBite README.md |
| 6 | - **Review & Wrap Up:** <br>&emsp; + Proofread the design note in English and Vietnamese <br>&emsp; + Confirm the deployed system still uses Mailpit for local/demo email, keeping the report's evidence honest | 10/07/2026 | 10/07/2026 | - Design note draft |


### Week 6 Achievements:

* **AWS & Cloud Foundation:**
  * Studied Serverless and event-driven concepts (EventBridge, SQS, SNS, Lambda, SES) and how they could decouple secondary tasks from the order-creation request.
  * Worked through the harder parts of async design on paper: retries, idempotency, ordering, dead-letter queues, and schema versioning.
  * Concluded that Lambda + SES is a **future-roadmap item** for QuickBite, not something the current single-environment demo needs; Mailpit remains the deployed mock for order and status emails.

* **QuickBite Project Development:**
  * Documented an explicit `OrderCreated → EventBridge → SQS → Lambda → SES` design proposal as a future-roadmap note, in both English and Vietnamese.
  * Kept the report's evidence honest: no Lambda function or SES sender identity was actually created for this demo.
