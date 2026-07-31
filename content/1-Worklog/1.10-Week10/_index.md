---
title: "Week 10 Worklog"
date: 2026-08-03
weight: 10
chapter: false
pre: " <b> 1.10. </b> "
---

### Week 10 Objectives:

* Conduct End-to-End (E2E) testing across all application roles (`Customer`, `Kitchen`, `Delivery`, `Admin`).
* Review the Terraform destroy procedure and cost-sensitive resources, without tearing down the live demo environment yet.
* Record the end-to-end product demo video and compile QuickBite project documentation.
* Complete and submit the final internship report for the First Cloud AI Journey (FCAJ).

### Tasks to be carried out this week:
| Day | Task | Start Date | Completion Date | Reference Material |
| --- | --- | --- | --- | --- |
| 2 | - **End-to-End System Testing:** <br>&emsp; + Execute automated test script `e2e_local.py` for full backend validation <br>&emsp; + Perform manual E2E tests: Customer orders -> Kitchen prepares -> Delivery fulfills -> Admin inspects analytics | 08/03/2026 | 08/03/2026 | - `backend/scripts/e2e_local.py` <br> - `backend/tests/` |
| 3 | - **Review Terraform Destroy & Cost-Sensitive Resources:** <br>&emsp; + Confirm the destroy order (main stack, then bootstrap) and the demo-lifecycle settings (force_destroy, force_delete, disabled deletion protection) in `docs/cleanup.md` <br>&emsp; + Check AWS Cost Explorer for the cost-sensitive components: NAT Gateways, Multi-AZ RDS, the ALB, the two EC2 instances, CloudWatch Logs, and CloudFront traffic | 08/04/2026 | 08/04/2026 | - `docs/cleanup.md` <br> - AWS Cost Explorer |
| 4 | - **Finalize Technical Documentation:** <br>&emsp; + Update main `README.md`, cloud deployment architecture diagrams, and OpenAPI specs <br>&emsp; + Consolidate demo accounts and API endpoint references | 08/05/2026 | 08/05/2026 | - `README.md` <br> - `docs/deploy-walkthrough.md` |
| 5 | - **Record Product Demo Video:** <br>&emsp; + Record full demo walkthrough spanning React Frontend UI and AWS Backend infrastructure <br>&emsp; + Highlight key features: order placement, `order_code` lookup, Mailpit confirmation email, Admin Dashboard, and CSV Export | 08/06/2026 | 08/06/2026 | - QuickBite Codebase |
| 6 | - **Final Submission & Portfolio Closure:** <br>&emsp; + Review all 10 Hugo Markdown worklogs for consistency <br>&emsp; + Package codebase, video demo link, and submit final FCAJ internship report | 08/07/2026 | 08/07/2026 | - FCAJ Portal |


### Week 10 Achievements:

* **AWS & Cloud Foundation:**
  * Reviewed and confirmed the Terraform destroy plan and demo-lifecycle settings, keeping the environment live for the final demo rather than tearing it down early.
  * Verified the stable, production-ready Cloud-Native deployment for QuickBite on AWS through the E2E test run.

* **QuickBite Project Development:**
  * Validated business logic via `e2e_local.py` and confirmed end-to-end workflow stability.
  * Completed the video demo, deployment documentation (`docs/aws-deployment.md`, `docs/cleanup.md`), and successfully submitted the 10-week internship deliverables.
