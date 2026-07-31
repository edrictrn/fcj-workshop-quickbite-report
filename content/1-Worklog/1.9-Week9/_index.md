---
title: "Week 9 Worklog"
date: 2026-07-27
weight: 9
chapter: false
pre: " <b> 1.9. </b> "
---

### Week 9 Objectives:

* Integrate Amazon CloudWatch for application logging, metric collection, and automated alarms.
* Enhance and thoroughly test the production Health Check endpoint (`GET /health`).
* Hardened Cloud infrastructure security: Environment variable protection, CORS settings, and AWS Security Groups.
* Evaluate API rate limiting and server stress performance.

### Tasks to be carried out this week:
| Day | Task | Start Date | Completion Date | Reference Material |
| --- | --- | --- | --- | --- |
| 2 | - **AWS CloudWatch Logging Integration:** <br>&emsp; + Configure AWS CloudWatch Agent on EC2 to stream FastAPI logs <br>&emsp; + Setup dedicated CloudWatch Log Groups and Streams for Production environments | 07/27/2026 | 07/27/2026 | - `docs/aws-deployment.md` <br> - AWS CloudWatch Docs |
| 3 | - **Configure CloudWatch Alarms & Metrics:** <br>&emsp; + Create Metric Filters to monitor 5xx server errors and 4xx request rates <br>&emsp; + Configure the CPU alarm at 70% for two 300-second periods and route Alarm/OK state changes through SNS email | 07/28/2026 | 07/28/2026 | - AWS CloudWatch Docs |
| 4 | - **Optimize Health Check Endpoint (`main.py`):** <br>&emsp; + Upgrade `GET /health` endpoint to perform deep ping checks against RDS PostgreSQL and S3 <br>&emsp; + Integrate API health check with AWS Target Group Health Checks | 07/29/2026 | 07/29/2026 | - `backend/main.py` <br> - QuickBite README.md |
| 5 | - **Security Hardening & Rate Limiting:** <br>&emsp; + Integrate `rate_limit.py` middleware to mitigate brute-force attacks on Auth routes <br>&emsp; + Restrict CORS origins strictly to CloudFront/S3 Frontend domains | 07/30/2026 | 07/30/2026 | - `backend/rate_limit.py` <br> - `backend/main.py` |
| 6 | - **Monitoring & Alarm Verification:** <br>&emsp; + Simulate server errors to verify CloudWatch Alarm SNS notifications <br>&emsp; + Verify API responsiveness and memory usage under load | 07/31/2026 | 07/31/2026 | - QuickBite Codebase |


### Week 9 Achievements:

* **AWS & Cloud Foundation:**
  * Integrated Amazon CloudWatch logging across EC2 instances and set up automated SNS alarms.
  * Configured AWS Security Groups and IAM policies adhering to the Principle of Least Privilege.

* **QuickBite Project Development:**
  * Enhanced the Health Check endpoint (`/health`) up to production cloud monitoring standards.
  * Applied API Rate Limiting (`rate_limit.py`) and hardened Backend CORS security configurations.