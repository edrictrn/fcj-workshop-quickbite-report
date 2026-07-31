---
title: "Week 7 Worklog"
date: 2026-07-13
weight: 7
chapter: false
pre: " <b> 1.7. </b> "
---

### Week 7 Objectives:

* Design and initialize database SQL Views on PostgreSQL/SQLite for business analytics.
* Develop reporting APIs to fetch key operational metrics (Revenue, Total Orders, Top Selling Items).
* Implement CSV Export services from the FastAPI backend.
* Integrate the Admin Dashboard and Report pages on the React Frontend.

### Tasks to be carried out this week:
| Day | Task | Start Date | Completion Date | Reference Material |
| --- | --- | --- | --- | --- |
| 2 | - Research reporting query optimization using SQL Views <br> - **Create SQL Views:** <br>&emsp; + Write SQL script for daily/monthly revenue views (`views_postgres.sql`) <br>&emsp; + Create views summarizing top items and order status distribution | 07/13/2026 | 07/13/2026 | - `backend/sql/views_postgres.sql` <br> - QuickBite README.md |
| 3 | - **Develop Reporting Router (`routers/reports.py`):** <br>&emsp; + Build `GET /reports/dashboard` endpoint to retrieve overall metrics <br>&emsp; + Implement detailed analytical endpoints for admin operations | 07/14/2026 | 07/14/2026 | - `backend/routers/reports.py` <br> - FastAPI Docs |
| 4 | - **Implement CSV Export Service:** <br>&emsp; + Build `GET /reports/export/orders` to export order history to CSV <br>&emsp; + Build `GET /reports/export/revenue` for financial CSV reports | 07/15/2026 | 07/15/2026 | - `backend/routers/reports.py` |
| 5 | - **Integrate Admin Dashboard UI (Frontend):** <br>&emsp; + Connect React MetricCards to Report APIs <br>&emsp; + Add Download CSV buttons for Admin report management | 07/16/2026 | 07/16/2026 | - `frontend/src/pages/admin/ReportPage.tsx` <br> - `frontend/src/components/MetricCard.tsx` |
| 6 | - **Testing & Data Validation:** <br>&emsp; + Seed mock database records (`seed_postgres.sql`) and verify reporting metric accuracy <br>&emsp; + Validate CSV file formats in Microsoft Excel and Google Sheets | 07/17/2026 | 07/17/2026 | - `backend/sql/seed_postgres.sql` |


### Week 7 Achievements:

* **Database & Cloud Foundation:**
  * Defined and executed SQL Views on Amazon RDS PostgreSQL to optimize report query performance.
  * Synchronized SQL View definitions between local SQLite and cloud PostgreSQL.

* **QuickBite Project Development:**
  * Completed the Reporting Router (`routers/reports.py`) supporting dashboard metrics and CSV exports.
  * Successfully integrated the Admin Dashboard and Report Page (`ReportPage.tsx`) on the React Frontend.