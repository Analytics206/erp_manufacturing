# 📘 Business Requirements Document (BRD)

## Project Name: Valor ERP

## 1. Overview
Valor ERP is a custom ERP SaaS platform tailored for metalworking companies, designed to manage the complete business workflow from estimates to invoicing. The system will be containerized using Docker for consistent local development and deployment.

## 2. Goals
- Streamline estimate-to-invoice workflows with automated job tracking and inventory management
- Provide real-time business insights through comprehensive reporting dashboards
- Enable remote and asynchronous work with a modern, responsive UI/UX
- Ensure system reliability and scalability through containerization and modular design
- Maintain high code quality through CI/CD pipelines and automated testing

## 3. Business Features

| BRD ID | Feature Description | Phase | Linked PRD Requirement(s) |
|--------|---------------------|-------|---------------------------|
| BRD-001 | Containerized development environment with Docker and Docker Compose for consistent deployment | 1 | DCK-01 to DCK-03 |
| BRD-002 | Authentication and role-based access control | 1 | AUTH-01 to AUTH-03 |
| BRD-003 | Inventory management with CRUD operations | 2 | INV-01 to INV-04 |
| BRD-004 | Estimate creation and management | 3 | EST-01 to EST-05 |
| BRD-005 | Job tracking and management | 4 | JOB-01 to JOB-06 |
| BRD-006 | Time and attendance tracking | 5 | TIME-01 to TIME-04 |
| BRD-007 | Invoicing and payment processing | 6 | INV-01 to INV-03 |
| BRD-008 | Business intelligence and reporting | 7 | RPT-01 to RPT-04 |

## 4. Technical Stack
- **Frontend**: 
  - Next.js with React
  - Tailwind CSS for styling
  - shadcn/ui component library
  - Progressive Web App (PWA) support
- **Backend**: 
  - Firebase Authentication
  - Firestore for document storage
  - Cloud Functions for serverless backend
  - Firebase Storage for file storage
  - Cloud Messaging for notifications
- **Database**: 
  - Firestore (primary for document storage)
  - PostgreSQL (analytics and data warehousing with TimescaleDB extension)
- **Hosting**: 
  - Vercel for frontend hosting
  - Firebase for backend services
- **Development Tools**:
  - VS Code with AI assistance (Cursor, Copilot)
  - Claude Sonnet 4 for UI design assistance
  - Zed for enhanced development experience
- **CI/CD**: 
  - GitHub Actions
  - Automated testing with Jest and Cypress
- **Project Management**:
  - Basecamp for task tracking
  - GitHub for version control and code review

## 5. Timeline
| Phase | Description | Duration (Weeks) | Dependencies |
|-------|-------------|------------------|--------------|
| 1 | Architecture & Foundation | 8-12 | - |
| 2 | Inventory Management | 10-14 | Phase 1 |
| 3 | Estimating System | 12-16 | Phase 2 |
| 4 | Job Management | 12-16 | Phase 3 |
| 5 | Time & Attendance | 8-12 | Phase 4 |
| 6 | Invoicing | 6-10 | Phase 4 |
| 7 | Reporting | 10-14 | Phase 2-6 |
| **Total** | **18-month project** | **66-104** | |

## 6. Team Structure
| Role | Responsibilities | Key Attributes |
|------|------------------|-----------------|
| Product Owner | Defines vision, manages client expectations, creates user stories | Primary point of contact, manages Basecamp |
| Lead Developer | Sole developer responsible for implementation and architectural decisions | Full-stack expertise, works asynchronously |
| Client | Metalworking company, end-user of the system | Provides feedback and requirements |
| Fractional Operator | Assists with operational oversight and process optimization | Part-time role, supports Product Owner |

## 7. Success Metrics
- 80% test coverage for critical paths
- 99.9% system uptime
- Sub-second response time for key operations
- 50% reduction in manual data entry
- 30% improvement in estimate-to-invoice cycle time

## 8. Security & Compliance
- Role-based access control
- Data encryption at rest and in transit
- Regular security audits and penetration testing
- Compliance with industry standards (GDPR, CCPA)
- Audit logging for all critical operations

## 9. Risks & Mitigation
| Risk | Impact | Probability | Mitigation Strategy |
|------|--------|-------------|---------------------|
| Integration complexity | High | Medium | API-first design, contract testing |
| Performance at scale | High | Low | Load testing, caching strategies |
| Data migration challenges | Medium | Medium | Incremental migration, validation tools |
| User adoption | Medium | Medium | Training, intuitive UI, phased rollout |
| Postgres Cost | High | Medium | Start with Firestore, evaluate Postgres ROI |
| AI Tool Learning Curve | Medium | Low | Leverage existing AI expertise, document patterns |
| Async Communication Gaps | Medium | Medium | Clear documentation, regular check-ins |
| Scope Creep | High | Medium | Strict phase gating, change control |

## 10. Appendices
### 10.1 Reference Materials
- **Demo UI**: [Valor ERP Demo](https://valor.appsandsides.com/)
- **Repository**: [GitHub Repository](https://github.com/your-organization/valor-erp)
- **ERP Roadmap**: [ERP Roadmap](/docs/5-roadmap.pdf)

### 10.2 Technical References
- **Product Requirements (PRD)**: [Product Requirements Document](/docs/3-product_requirements.md)
- **System Design**: [System Design Document](/docs/6-system_design.md)
- **API Documentation**: [Link to API docs]
- **Firebase Configuration**: [Link to Firebase setup]
- **Vercel Deployment**: [Link to Vercel setup]

### 10.3 Client Information
- **Industry**: Metal fabrication
- **Team Size**: 2 managers, ~10 workers
- **Primary Use Case**: Estimate creation, job tracking, time & attendance, invoicing

### 10.4 Development Guidelines
- **Code Style**: ESLint + Prettier configuration
- **Git Workflow**: Feature branches with PRs
- **Testing**: Minimum 80% coverage
- **Documentation**: JSDoc for functions, README updates required

### 10.5 AI Tooling
- **Recommended Tools**:
  - Claude Sonnet 4 for UI design
  - GitHub Copilot for code completion
  - Cursor/Zed for enhanced development
  - VS Code with relevant extensions
- **AI Usage Guidelines**:
  - Document all AI-generated code
  - Review and understand all AI suggestions
  - Maintain code quality and consistency

## 11. Executive Summary

The purpose of the Valor ERP project is to develop a custom ERP SaaS platform tailored for a metalworking company. The system will manage customer estimates, job tracking, inventory control, time & attendance, invoicing, and reporting. It will streamline business operations, enable remote and asynchronous work, and prioritize beautiful, modern UI/UX with a developer-empowered, AI-augmented build process.

## 12. Objectives
- Enable efficient estimate-to-invoice workflows.
- Support job tracking and inventory synchronization.
- Simplify timekeeping and payroll preparation.
- Offer clear, actionable reporting dashboards.
- Provide a scalable, modular, and maintainable system.

## 13. Functional Requirements
### Phase 1: Foundation & Architecture
- CI/CD pipeline with linting, tests.
- Tailwind-based responsive UI shell (with dark mode).
- Firebase Authentication & Firestore access control.

### Phase 2: Inventory
- CRUD for SKUs and vendors.
- Bulk import (CSV).
- Custom SKU search/format.

### Phase 3: Estimating
- Create, edit, and calculate estimates.
- Generate/send email quotes via SES.
- Public quote accept/decline portal.
- Inventory reservation.
- Version tracking.

### Phase 4: Jobs
- Status pipeline (queued → finished).
- Job board with filters.
- Inventory sync (reserve/release stock).
- Manual or timer-based employee time logs.
- Job-based invoice generation.

### Phase 5: Time & Attendance
- Daily & job-based clock-ins.
- Breaks, OT thresholds.
- Payroll export (QuickBooks Time-compatible CSV).

### Phase 6: Invoicing
- Branded invoice generation.
- Auto pull from jobs & time entries.
- SES email & downloadable PDF.

### Phase 7: Reporting
- Widgets for revenue, profitability, and utilization.
- Ad-hoc filter builder UI.

## 14. Technical Requirements
- Frontend: Next.js (or developer choice), Tailwind, shadcn/ui.
- Backend: Firebase (Auth, Firestore, Functions). Postgres optional for analytics.
- Hosting: Vercel (dev/staging/prod environments).
- CI/CD: GitHub Actions.
- Email: Amazon SES.

## 15. QA & Acceptance Criteria
- 80% automated test coverage on critical logic.
- Functional UAT by managers.
- Code review before merge.
- Deployed to staging.
- Documentation updated.

## 16. Timeline & Milestones
| Phase | Duration (Weeks) |
|-------|----------------|
| Phase 1: Architecture | 8-12 |
| Phase 2: Inventory | 10-14 |
| Phase 3: Estimating | 12-16 |
| Phase 4: Jobs | 12-16 |
| Phase 5: Time & Attendance | 8-12 |
| Phase 6: Invoicing | 6-10 |
| Phase 7: Reporting | 10-14 |

## 17. Security & Permissions
- Firebase security rules based on role (front desk, manager, technician).
- CAPTCHAs on public forms.
- Audit trails (version history).

## 18. Development Process
### Methodology
- **Semi-Agile with async-first approach**
  - Flexible workflow that accommodates remote, asynchronous work
  - Regular but minimal synchronous check-ins as needed

### Tools & Platforms
- **Basecamp** for project management
  - Kanban-style task tracking
  - Asynchronous communication
  - Document sharing and versioning
- **GitHub Organization**
  - Code hosting and version control
  - Pull request workflow
  - Automated CI/CD pipelines
  - Code review process

### Workflow
1. **Sprint Planning**
   - Product Owner and Fractional Operator prepare user stories
   - Developer self-assigns tasks based on capacity
   - Clear definition of done for each task

2. **Development Cycle**
   - Developer works asynchronously on assigned tasks
   - Regular commits with descriptive messages
   - Pull requests for code review
   - Automated testing on all code changes

3. **Review & Deployment**
   - Asynchronous code reviews
   - Automated deployment to staging on merge to main
   - Client feedback collection through staging environment

4. **Retrospective**
   - Async retro at the end of each sprint
   - Continuous improvement of process
   - Adjustments based on velocity and feedback

## 19. Implementation Considerations
| Factor | Description | Strategy |
|--------|-------------|----------|
| Docker Containerization | Docker and Docker Compose for consistent environments | Create development, testing, and production container configurations |
| Development Workflow | Asynchronous, AI-assisted development | Document patterns and best practices for AI tooling |
| Performance Optimization | Ensuring system remains responsive at scale | Implement caching strategy and regular performance tests |
| Client Training | Ensuring smooth adoption by end users | Develop comprehensive documentation and training materials |

### Key Assumptions
- Developer is proficient with AI-assisted development tools
- Client will provide timely feedback during review cycles
- Core functionality can be achieved with Firebase's free tier
- AI tools will significantly accelerate UI development
- 18-month timeline allows for thorough testing and refinement

# 20. Appendix
- **Demo UI**: [Valor ERP Demo](https://valor.appsandsides.com/)
- **Repository**: [GitHub Repository](https://github.com/your-organization/valor-erp) 
- **Client Industry**: Metal fabrication
- **Technical Documentation**: See [System Design](/docs/6-system_design.md) and [Schema Documentation](/docs/6-schema)