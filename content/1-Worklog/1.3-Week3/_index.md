---
title: "Week 3 Worklog"
date: 2026-06-15
weight: 3
chapter: false
pre: " <b> 1.3. </b> "
---

### Week 3 Objectives:

* Understand Containerization basics using Docker and Docker Compose.
* Learn about Amazon ECR (Elastic Container Registry) and how EC2 instances pull versioned images from it.
* Containerize the QuickBite full-stack application (FastAPI + React + PostgreSQL + Mailpit).
* Set up local SMTP email simulation with Mailpit for order confirmation and status updates.

### Tasks to be carried out this week:
| Day | Task | Start Date | Completion Date | Reference Material |
| --- | --- | --- | --- | --- |
| 2 | - Learn Docker basics: Images, Containers, Dockerfile, and Docker Compose <br> - **QuickBite Dockerization:** <br>&emsp; + Write `Dockerfile` for FastAPI Backend and React Frontend <br>&emsp; + Configure `docker-compose.yml` for local full-stack development | 15/06/2026 | 15/06/2026 | - Docker Official Docs <br> - QuickBite README.md |
| 3 | - **Local Email Simulation Setup:** <br>&emsp; + Add Mailpit SMTP service to `docker-compose.yml` <br>&emsp; + Implement local email service in FastAPI for order confirmation & status updates | 16/06/2026 | 16/06/2026 | - Mailpit Docs <br> - QuickBite README.md |
| 4 | - Learn about Amazon ECR (Elastic Container Registry): repositories, image tags, and scan-on-push <br> - **Image Versioning Practice:** <br>&emsp; + Tag backend images with semantic versions <br>&emsp; + Document the pull-based deployment model where each EC2 instance authenticates through IAM and pulls the image, instead of shipping source code | 17/06/2026 | 17/06/2026 | - <https://cloudjourney.awsstudygroup.com/> <br> - AWS ECR Docs |
| 5 | - **Docker Compose Networking:** <br>&emsp; + Configure internal service discovery between `frontend`, `backend`, `db`, and `mailpit` containers <br>&emsp; + Add healthcheck directives so `backend` waits for `db` readiness | 18/06/2026 | 18/06/2026 | - Docker Compose Docs |
| 6 | - **AWS Practice & System Verification:** <br>&emsp; + Build and push Docker images to Amazon ECR <br>&emsp; + Test full Docker Compose stack (`docker compose up --build`) <br>&emsp; + Verify email delivery on Mailpit web inbox (`http://localhost:8025`) | 19/06/2026 | 19/06/2026 | - AWS CLI / ECR Docs <br> - QuickBite README.md |


### Week 3 Achievements:

* **AWS & Cloud Foundation:**
  * Mastered container concepts and successfully built custom Docker images for both Backend and Frontend.
  * Configured Amazon ECR (Elastic Container Registry) and successfully pushed versioned container images using AWS CLI.
  * Understood the pull-based image model later used in production: EC2 instances authenticate through an IAM role and pull the versioned image from ECR instead of running from source.

* **QuickBite Project Development:**
  * Successfully set up a full multi-container local stack with **Docker Compose** (`React` -> `FastAPI` -> `PostgreSQL` -> `Mailpit`).
  * Configured local email simulation using Mailpit, successfully testing order creation and status update confirmation emails.
  * Added Compose healthchecks so the backend only starts accepting traffic after the database is ready.
