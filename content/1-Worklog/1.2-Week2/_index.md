---
title: "Week 2 Worklog"
date: 2026-06-08
weight: 2
chapter: false
pre: " <b> 1.2. </b> "
---

### Week 2 Objectives:

* Understand and practice AWS Storage (Amazon S3) and Database (Amazon RDS) services.
* Gain basic knowledge of AWS Networking (VPC, Subnets, Security Groups).
* Design QuickBite's Database Schema and implement database migrations using Alembic.
* Complete core Business Logic APIs for the ordering flow (Customer -> Kitchen -> Delivery).

### Tasks to be carried out this week:
| Day | Task | Start Date | Completion Date | Reference Material |
| --- | --- | --- | --- | --- |
| 2 | - Learn about Amazon S3: Buckets, Objects, Versioning, and Permissions <br> - **QuickBite DB Design:** <br>&emsp; + Optimize ERD for PostgreSQL/SQLite (Users, Items, Orders, System Config, Audit Logs) <br>&emsp; + Define SQLAlchemy ORM models | 08/06/2026 | 08/06/2026 | - <https://cloudjourney.awsstudygroup.com/> <br> - SQLAlchemy Docs |
| 3 | - **AWS Practice:** <br>&emsp; + Create an S3 Bucket <br>&emsp; + Upload and manage files via AWS Console and AWS CLI <br> - **QuickBite DB Migration:** <br>&emsp; + Integrate Alembic to manage database migrations instead of manual scripts | 09/06/2026 | 09/06/2026 | - <https://cloudjourney.awsstudygroup.com/> <br> - Alembic Docs |
| 4 | - Learn about Amazon RDS: Supported engines, Multi-AZ deployments, Backups <br> - **QuickBite Business Logic (Part 1):** <br>&emsp; + Implement API for Customer to create orders (COD / Mock Payment) <br>&emsp; + Implement API to browse and filter menu items | 10/06/2026 | 10/06/2026 | - <https://cloudjourney.awsstudygroup.com/> <br> - FastAPI Docs |
| 5 | - Learn basic Amazon VPC: Subnets (Public/Private), Route Tables, Security Groups <br> - **QuickBite Business Logic (Part 2):** <br>&emsp; + Implement API for Kitchen staff to accept/prepare orders <br>&emsp; + Implement API for Delivery staff to update delivery status | 11/06/2026 | 11/06/2026 | - <https://cloudjourney.awsstudygroup.com/> <br> - QuickBite README.md |
| 6 | - **AWS Practice:** <br>&emsp; + Launch an Amazon RDS instance (PostgreSQL) <br>&emsp; + Connect to RDS using a local database client <br> - **QuickBite End-to-End Testing:** <br>&emsp; + Implement public order lookup endpoint by `order_code` <br>&emsp; + Test the full order flow end-to-end | 12/06/2026 | 12/06/2026 | - <https://cloudjourney.awsstudygroup.com/> <br> - QuickBite Codebase |


### Week 2 Achievements:

* **AWS & Cloud Foundation:**
  * Mastered the concepts of Amazon S3 and successfully created/managed S3 Buckets using both AWS Console and CLI.
  * Understood the architecture of Amazon RDS and successfully provisioned a PostgreSQL database instance on AWS.
  * Gained foundational knowledge of Amazon VPC, including how Security Groups and Subnets control database access.

* **QuickBite Project Development:**
  * Successfully optimized the ERD and defined SQLAlchemy models for essential entities (Users, Items, Orders, Config, Logs).
  * Replaced manual database initialization (`init_db_sqlite.py`) with **Alembic**, enabling version-controlled database schema migrations.
  * Completed the core ordering flow APIs, supporting order creation with mock e-wallet payment and COD.
  * Finalized the role-based operation flow APIs for `Kitchen` (preparing orders) and `Delivery` (updating delivery status).
  * Successfully implemented and tested the public order lookup feature using the unique `order_code`.