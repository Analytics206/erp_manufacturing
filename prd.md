# 🧾 Product Requirements Document (PRD)
- Project Name: Valor ERPClient: Metalworking CompanyPrepared By: Product Owner / Project ManagerDate: June 2025

## 🧠 Purpose
This document outlines the specific product requirements for building the Valor ERP system. It provides the necessary details to guide development, align stakeholders, and track progress through delivery.

## 🎯 Goals & Success Criteria
- Provide seamless Estimate → Job → Invoice workflows.
- Centralize job and inventory management.
- Enable remote and mobile-friendly time tracking.
- Offer robust, real-time reporting dashboards.
- Maintain high UI/UX quality and dev experience.

## 📊 Success is measured by
- 80% UAT approval rate for each feature phase.
- Reduction in manual entry and communication overhead.
- Full adoption by client teams within 3 months of launch.

## 🧩 Features & User Stories
### 🔐 Authentication & Roles (Phase 1)
- As a user, I can log in with a secure method (Firebase Auth).
- As an admin, I can set user permissions to limit access by role.

### 📦 Inventory Management (Phase 2)
- As an inventory manager, I can create, edit, and bulk import SKUs.
- As a purchaser, I can link SKUs to vendor profiles.
- As a user, I can filter/search using SKU metadata.

### 📑 Estimating (Phase 3)
- As a sales user, I can generate an estimate using SKUs and labor entries.
- As a user, I can send an estimate via email with tokenized response links.
- As a client, I can accept or reject a quote online.
- As a system, I will reserve inventory when an estimate is drafted.

### 🧱 Job Lifecycle (Phase 4)
- As a technician, I can view jobs assigned to me and track time.
- As a project manager, I can filter jobs by due date, material, or status.
- As a system, I will adjust inventory levels based on job status.

### ⏱ Time & Attendance (Phase 5)
- As an employee, I can clock in/out from web or mobile.
- As a system, I calculate OT and prepare CSV for payroll.

### 🧾 Invoicing (Phase 6)
- As a billing user, I can generate branded invoices from job data.
- As a system, I will send invoices using Amazon SES.

### 📊 Reporting & Dashboards (Phase 7)
- As a manager, I can view KPIs: revenue, profit margin, and utilization.
- As a user, I can build ad-hoc reports using a field/operator/value UI.

## 🖥 UI/UX Requirements
- Responsive layout (desktop, tablet, mobile).
- Tailwind-based modern interface with dark mode toggle.
- Notifications (toasts, alerts).
- CAPTCHA support on public forms.

## ⚙️ Technical Requirements
- Frontend: Next.js or React, Tailwind CSS, shadcn/ui.
- Backend: Firebase (Auth, Firestore, Functions).
- CI/CD: GitHub + Vercel.
- Storage: Firestore + optional Postgres for analytics.
- Email: Amazon SES.

## ✅ Acceptance Criteria (per feature)
- UI passes accessibility checks.
- Unit + integration tests for all core logic.
- UAT passes with >80% manager approval.
- Successfully deployed to staging.
- Documentation and audit logs updated.

## 📅 Milestones & Timeline
Feature Phase | Estimated Duration
--- | ---
Phase 1: Foundation | 1–2 weeks
Phase 2: Inventory | 5–7 weeks
Phase 3: Estimating | 11–14 weeks
Phase 4: Jobs | 10–14 weeks
Phase 5: Time Tracking | 6–8 weeks
Phase 6: Invoicing | 4–7 weeks
Phase 7: Reporting | 8–12 weeks

## 📊 Metrics
- Time to estimate: Target <5 minutes.
- Job creation: Target <3 minutes.
- Invoice approval/issue rate: >95% successful sends.
- Report load time: <2 seconds.

## 🔐 Risk Mitigation
- Firebase fallback security rules in case of misconfiguration.
- Use Postgres where Firestore lacks performant querying.
- Use async communication and sprint retros to identify dev blockers.

## 🔍 Appendices

### BRD Reference

### UI Demo

### [GitHub Repo Access] To be provided

### [Client Industry] Metal Fabrication

