---
title: "Week 5 Worklog"
date: 2026-06-29
weight: 5
chapter: false
pre: " <b> 1.5. </b> "
---

### Week 5 Objectives:

* Learn Terraform fundamentals (providers, state, modules) and design the QuickBite Infrastructure-as-Code layout.
* Bootstrap the Terraform backend: a versioned/encrypted S3 state bucket, a DynamoDB lock table, and the ECR repository.
* Build the main Terraform stack (network, data, and app modules) to replace manual AWS setup with a repeatable, two-Availability-Zone deployment.
* Host the React Frontend as a static site on Amazon S3, distributed through Amazon CloudFront.

### Tasks to be carried out this week:
| Day | Task | Start Date | Completion Date | Reference Material |
| --- | --- | --- | --- | --- |
| 2 | - Learn Terraform basics: providers, resources, state, and remote backends <br> - **Bootstrap Stack:** <br>&emsp; + Create a versioned, AES-256 encrypted S3 bucket for Terraform remote state <br>&emsp; + Create a DynamoDB table to prevent concurrent state writes <br>&emsp; + Create the `quickbite-backend` ECR repository with scan-on-push | 29/06/2026 | 29/06/2026 | - <https://cloudjourney.awsstudygroup.com/> <br> - Terraform Docs |
| 3 | - **Network Module:** <br>&emsp; + Define a VPC with two public, two private application, and two isolated database subnets across two Availability Zones <br>&emsp; + Wire Security Group chaining: ALB-SG → App-SG:8000 → DB-SG:5432, plus Internet Gateway and NAT Gateways | 30/06/2026 | 30/06/2026 | - Terraform AWS Provider Docs <br> - QuickBite README.md |
| 4 | - **Data Module:** <br>&emsp; + Provision an encrypted, Multi-AZ RDS PostgreSQL (db.t3.micro) across the isolated subnets <br>&emsp; + Store `DATABASE_URL` and the JWT secret in Secrets Manager instead of Terraform variables | 01/07/2026 | 01/07/2026 | - AWS RDS Docs <br> - AWS Secrets Manager Docs |
| 5 | - **App Module:** <br>&emsp; + Define the ALB, Target Group, and `/health` health check <br>&emsp; + Define a Launch Template and Auto Scaling Group (min 2, desired 2, max 4) with 60% CPU target tracking <br>&emsp; + Create private web and menu-images S3 buckets plus two CloudFront distributions with Origin Access Control | 02/07/2026 | 02/07/2026 | - AWS CloudFront Docs <br> - QuickBite README.md |
| 6 | - **Apply & Frontend Build:** <br>&emsp; + Run `terraform plan`/`apply` for the main stack and verify the resource count <br>&emsp; + Build React for production using the CloudFront API domain as the API base and sync `dist/` to the web S3 bucket <br>&emsp; + Configure SPA fallback (403/404 → `index.html`) | 03/07/2026 | 03/07/2026 | - QuickBite Codebase |


### Week 5 Achievements:

* **AWS & Cloud Foundation:**
  * Bootstrapped the Terraform backend: encrypted state bucket, DynamoDB lock table, and the `quickbite-backend` ECR repository.
  * Built the network module (VPC, two public/two private/two isolated subnets, IGW, NAT Gateways, and Security Group chaining) and the data module (Multi-AZ RDS PostgreSQL and Secrets Manager).
  * Built the app module: ALB with a `/health` target group, a Launch Template and Auto Scaling Group (min 2, desired 2, max 4, 60% CPU target tracking), private S3 buckets, and two CloudFront distributions with OAC.
  * Replaced the earlier idea of a single manually managed EC2 instance with a repeatable, two-Availability-Zone Terraform deployment — `terraform apply` created the full resource set in one run.

* **QuickBite Project Development:**
  * Deployed the FastAPI backend image (pushed to ECR in Week 3) onto the Auto Scaling Group and verified stable connectivity to the new Multi-AZ RDS instance.
  * Built React for production with the CloudFront API domain as the API base and synced the static build to the private web S3 bucket, served through CloudFront.
  * Verified `GET /health` through the ALB target group for real-time monitoring of database and server status.
  * Tested the end-to-end cloud flow: browsing the menu, placing orders, and updating status through the live CloudFront URLs.
