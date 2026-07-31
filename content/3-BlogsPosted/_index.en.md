---
title: "Blogs Posted"
date: 2026-07-30
weight: 3
chapter: false
pre: " <b> 3. </b> "
includeInReport: false
---
This section introduces the three AWS articles I prepared while developing QuickBite. Each article is available in both English and Vietnamese.

### [Blog 1 - Learning AWS Secrets Manager](3.1-Blog1/)
This article explains how AWS Secrets Manager replaces storing `DATABASE_URL`, a JWT secret, and API keys in a `.env` file, covering KMS encryption, IAM-role-based access, the steps to create and read a secret, and the cost/latency trade-offs to consider. It relates directly to how QuickBite stores `DATABASE_URL` and the JWT secret in Secrets Manager through the Terraform data module.

### [Blog 2 - Disaster Recovery on AWS](3.2-Blog2/)
This article introduces RTO, RPO, Backup and Restore, Pilot Light, Warm Standby, and Multi-site Active/Active. It connects disaster-recovery planning with QuickBite through RDS backups, S3 data protection, restoration runbooks, and the distinction between a short-lived demo and a production workload.

### [Blog 3 - Amazon GuardDuty vs Amazon Inspector](3.3-Blog3/)
This article compares Amazon GuardDuty (real-time threat detection) and Amazon Inspector (vulnerability scanning), covering how each service works, its protection scope, and when it takes effect, along with lessons on defense-in-depth and consolidating findings through AWS Security Hub.
