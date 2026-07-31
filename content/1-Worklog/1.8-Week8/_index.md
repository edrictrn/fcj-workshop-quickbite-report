---
title: "Week 8 Worklog"
date: 2026-07-20
weight: 8
chapter: false
pre: " <b> 1.8. </b> "
---

### Week 8 Objectives:

* Build an Operation Log / Audit Trail system to record every significant administrative and staff action.
* Implement a dynamic System Configuration module (delivery fee, tax rate, service hours).
* Build the Admin-facing UI for configuration management and log viewing.

### Tasks to be carried out this week:
| Day | Task | Start Date | Completion Date | Reference Material |
| --- | --- | --- | --- | --- |
| 2 | - Research audit-logging patterns for web applications <br> - **Design the Audit Log Schema:** <br>&emsp; + Define the `OperationLog` model storing action, user_id, details, and timestamp <br>&emsp; + Build a `log_utils.py` helper for automatic logging | 20/07/2026 | 20/07/2026 | - `backend/log_utils.py` <br> - `backend/models/system.py` |
| 3 | - **Wire the Audit Logger into Routers:** <br>&emsp; + Automatically log actions such as order status changes, menu updates, and system-config changes <br>&emsp; + Build a `GET /logs` endpoint to query the log list | 21/07/2026 | 21/07/2026 | - `backend/routers/logs.py` |
| 4 | - **Develop Dynamic System Settings (`routers/settings.py`):** <br>&emsp; + Build read/write APIs for system configuration (delivery fee, VAT, opening/closing hours) <br>&emsp; + Ensure new orders calculate delivery fee and tax correctly against the current configuration | 22/07/2026 | 22/07/2026 | - `backend/routers/settings.py` <br> - `backend/settings_utils.py` |
| 5 | - **Frontend Integration:** <br>&emsp; + Build `LogsPage.tsx` to view the operation history <br>&emsp; + Build `SettingsPage.tsx` so Admins can adjust delivery fee and operational configuration | 23/07/2026 | 23/07/2026 | - `frontend/src/pages/admin/LogsPage.tsx` <br> - `frontend/src/pages/admin/SettingsPage.tsx` |
| 6 | - **Operational Flow Testing:** <br>&emsp; + Change the delivery fee on `SettingsPage` and confirm new orders apply the updated value <br>&emsp; + Verify the audit log records the correct user and action | 24/07/2026 | 24/07/2026 | - QuickBite Codebase |


### Week 8 Achievements:

* **Operations & System Governance:**
  * Completed the `log_utils.py` utility, automating the audit trail for every administrative action on the system.
  * Improved transparency and made incident investigation faster once the system runs in production.

* **QuickBite Project Development:**
  * Completed the dynamic configuration system (`settings_utils.py`), letting Admins adjust delivery fee, tax, and opening/closing hours without restarting the server.
  * Successfully integrated the `LogsPage.tsx` and `SettingsPage.tsx` screens on the React Frontend.
