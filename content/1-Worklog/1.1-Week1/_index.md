---
title: "Week 1 Worklog"
date: 2026-06-01
weight: 1
chapter: false
pre: " <b> 1.1. </b> "
---


### Week 1 Objectives:

* Connect and get acquainted with members of First Cloud AI Journey (FCAJ).
* Understand basic AWS services, how to use AWS Management Console & AWS CLI.
* Setup local development environment, refactor QuickBite core architecture, and enforce JWT Authentication & Role-Based Access Control (RBAC).

### Tasks to be carried out this week:
| Day | Task | Start Date | Completion Date | Reference Material |
| --- | --- | --- | --- | --- |
| 2 | - Get acquainted with FCAJ members <br> - Read and take note of internship unit rules and regulations <br> - Review QuickBite repository structure and set up project scope | 06/01/2026 | 06/01/2026 | - Internal Rules <br> - QuickBite README.md |
| 3 | - Learn about AWS overview and service categories: Compute, Storage, Networking, Database <br> - **Refactor Backend Core:** <br>&emsp; + Reorganize `backend/` into Layered Architecture <br>&emsp; + Implement Pydantic `BaseSettings` for `.env` management | 06/02/2026 | 06/02/2026 | - <https://cloudjourney.awsstudygroup.com/> <br> - FastAPI / Pydantic Docs |
| 4 | - Create AWS Free Tier account <br> - Learn AWS Console & install/configure AWS CLI <br> - **Auth & Authorization:** <br>&emsp; + Refactor JWT Authentication flow <br>&emsp; + Implement RBAC dependencies for 4 roles (`Admin`, `Customer`, `Kitchen`, `Delivery`) | 06/03/2026 | 06/03/2026 | - <https://cloudjourney.awsstudygroup.com/> <br> - Python `python-jose` / `passlib` |
| 5 | - Learn basic EC2: Instance types, AMI, EBS, Elastic IP <br> - SSH connection methods to EC2 <br> - **Frontend Integration:** <br>&emsp; + Configure React Vite `.env.local` API base URL <br>&emsp; + Integrate Axios Auth Service for Login/Register | 06/04/2026 | 06/05/2026 | - <https://cloudjourney.awsstudygroup.com/> <br> - React / Vite Docs |
| 6 | - **AWS Practice:** Launch EC2 instance, SSH connection, attach EBS volume <br> - **Testing & Validation:** <br>&emsp; + Verify OpenAPI `/docs` endpoints <br>&emsp; + Test RBAC route protection (403 Forbidden for unauthorized roles) | 06/05/2026 | 06/05/2026 | - <https://cloudjourney.awsstudygroup.com/> <br> - FastAPI Swagger UI |

### Week 1 Achievements:

* **AWS & Cloud Foundation:**
  * Understood core AWS service groups (Compute, Storage, Networking, Database).
  * Successfully set up AWS Free Tier account, AWS Management Console, and AWS CLI (configured Access Key, Secret Key, and Default Region).
  * Successfully launched a test EC2 instance, connected via SSH, and attached an EBS volume.

* **QuickBite Project Development:**
  * Cleaned up and restructured the `backend/` codebase to follow modular Layered Architecture (`core/`, `models/`, `schemas/`, `routers/`, `services/`).
  * Configured secure environment variable handling using Pydantic `BaseSettings` (`config.py`).
  * Completed and validated JWT Authentication and Role-Based Access Control (RBAC) supporting 4 distinct system roles (`Admin`, `Customer`, `Kitchen`, `Delivery`).
  * Successfully connected React (Vite) Frontend with FastAPI Backend APIs, verifying login state persistence and route protection.