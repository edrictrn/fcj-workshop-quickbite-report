---
title: "Week 4 Worklog"
date: 2026-06-22
weight: 4
chapter: false
pre: " <b> 1.4. </b> "
---

### Week 4 Objectives:

* Deploy an initial Amazon RDS (PostgreSQL) instance to validate the application against a real cloud database.
* Configure Amazon S3 storage for menu images, kept private from the start instead of public buckets.
* Implement backend-mediated image upload so the object storage credentials never reach the browser.
* Migrate local database schema and seed data to the live AWS RDS instance.

### Tasks to be carried out this week:
| Day | Task | Start Date | Completion Date | Reference Material |
| --- | --- | --- | --- | --- |
| 2 | - Learn about Cloud Database Architecture & Security Groups for Amazon RDS <br> - **RDS Provisioning:** <br>&emsp; + Provision a first Amazon RDS PostgreSQL instance to validate connectivity <br>&emsp; + Configure VPC Subnet Groups and Inbound Security Rules (TCP 5432 from the app tier only) | 22/06/2026 | 22/06/2026 | - <https://cloudjourney.awsstudygroup.com/> <br> - AWS RDS Docs |
| 3 | - **Database Cloud Migration:** <br>&emsp; + Configure FastAPI database connection to point to AWS RDS endpoint <br>&emsp; + Run Alembic migrations to apply schema and seed initial data onto Amazon RDS | 23/06/2026 | 23/06/2026 | - Alembic Docs <br> - QuickBite README.md |
| 4 | - Learn about S3 Block Public Access, bucket policies, and why direct-to-client uploads widen the attack surface <br> - **S3 Storage Setup:** <br>&emsp; + Create a private Amazon S3 bucket for menu item images with Block Public Access enabled <br>&emsp; + Confirm no bucket policy or ACL grants public read/write | 24/06/2026 | 24/06/2026 | - AWS S3 Docs <br> - QuickBite README.md |
| 5 | - **Backend-Mediated Image Upload:** <br>&emsp; + Integrate `boto3` SDK into FastAPI Backend <br>&emsp; + Implement `POST /menu/{id}/image` so the backend validates type/size and writes the object to the private bucket using its own IAM permissions | 25/06/2026 | 25/06/2026 | - Boto3 Docs <br> - FastAPI Docs |
| 6 | - **Testing & Validation:** <br>&emsp; + Test image upload flow from React Frontend through the FastAPI endpoint into the private bucket <br>&emsp; + Confirm the object is not reachable via a direct public S3 URL <br>&emsp; + Perform health checks on the RDS connection | 26/06/2026 | 26/06/2026 | - QuickBite Codebase |


### Week 4 Achievements:

* **AWS & Cloud Foundation:**
  * Provisioned and configured a first Amazon RDS PostgreSQL instance with restrictive VPC Security Group rules, as a stepping stone toward the Multi-AZ instance built later with Terraform.
  * Created a private S3 bucket with Block Public Access enabled for menu images, avoiding public ACLs and public bucket policies from day one.
  * Learned why direct client-to-S3 uploads (presigned URLs) were not the right fit here, since QuickBite instead routes uploads through the backend so the object storage permissions stay on the server side.

* **QuickBite Project Development:**
  * Successfully migrated the local database schema to Amazon RDS using Alembic migrations.
  * Integrated `boto3` SDK into FastAPI so the backend itself uploads validated images to the private bucket.
  * Connected React Frontend menu management to the new upload endpoint; images are served back through the API rather than a public S3 URL.
  * Verified end-to-end cloud data persistence between FastAPI, Amazon RDS, and Amazon S3.
