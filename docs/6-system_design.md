# Valor ERP - System Design Document
| [README.md](README.md) | Return to project details README.md |

## Overview

Valor ERP is a comprehensive Enterprise Resource Planning system specifically designed for metalworking companies, built with a modern tech stack and AI-assisted development practices. This document outlines the system architecture, technical decisions, and implementation details that guide the development and maintenance of the Valor ERP platform.

## Document Purpose

This document serves as a technical reference for developers, architects, and technical stakeholders, focusing on:

1. System architecture and component interactions
2. Technical implementation decisions with AI-assisted development
3. Data models and database design
4. API specifications
5. Security and performance considerations
6. Deployment architecture with Vercel and Firebase
7. AI tooling and development workflow

## System Architecture

### High-Level Architecture

```
[Users]──┬────────────────────────────┐
        │                            │
        ▼                            ▼
   [Customers] ←──── [Estimates] ─────→ [Jobs]
        │                             │
        │                             │
        ▼                             ▼
  [Invoices]                    [TimeEntries]
        │                             │
        ▼                             ▼
    [Payments]                  [Employees]
        │                             │
        ▼                             ▼
    [Vendors] ─────→ [InventoryItems] ──┬────→ [PurchaseOrders]
                                       │
                                       ▼
                                  [StockMovements]
```

### Technology Stack

### Core Technologies
| Component | Technology | Description |
|-----------|------------|-------------|
| Frontend | Next.js 15.3, React 19.1 | Modern, responsive web interface with SSR/SSG |
| Styling | Tailwind CSS, shadcn/ui | Utility-first CSS with accessible components |
| State Management | React Context, SWR | Client-side state and data fetching |
| Authentication | Firebase Authentication | Secure auth with JWT and RBAC |
| Document Database | Firestore | Real-time NoSQL document database |
| Analytics Database | PostgreSQL | Analytics and data warehousing with TimescaleDB |
| File Storage | Firebase Storage | Secure file uploads and management |
| Backend | Firebase Cloud Functions | Serverless backend services |
| Hosting | Vercel (frontend) | Edge-optimized frontend hosting |
| CI/CD | GitHub Actions | Automated testing and deployment |
| Containerization | Docker, Docker Compose | Consistent development environments |
| Monitoring | Firebase Performance Monitoring | Real user monitoring |
| Push Notifications | Firebase Cloud Messaging | Real-time user notifications |

### Development Tooling
| Category | Tools |
|----------|-------|
| IDE | VS Code with Cursor |
| AI Assistance | Claude Sonnet 4, GitHub Copilot |
| Code Editor | Zed (for enhanced development) |
| Project Management | Basecamp, GitHub Projects |
| API Testing | Postman, Insomnia |
| Documentation | Markdown, Swagger |
| Design | Figma (with AI plugins) |

### AI-Assisted Development
- **UI/UX Design**: Claude Sonnet 4 for component generation
- **Code Completion**: GitHub Copilot for real-time suggestions
- **Code Review**: AI-assisted pull request reviews
- **Documentation**: Automated API documentation
- **Testing**: AI-generated test cases

## Data Model

### Core Entities

1. **Users**
   - id (PK), name, email, role, password_hash, created_at, active
   
2. **Customers**
   - id (PK), user_id (FK), name, email, phone, billing_address, shipping_address

3. **Estimates**
   - id (PK), customer_id (FK), user_id (FK), description, status, amount, created_at

4. **Jobs**
   - id (PK), estimate_id (FK), customer_id (FK), title, status, budget, completion_percentage

5. **InventoryItems**
   - id (PK), vendor_id (FK), name, sku, stock_quantity, minimum_stock_level, unit_price

6. **Invoices**
   - id (PK), customer_id (FK), job_id (FK), amount, status, due_date

7. **Vendors**
   - id (PK), name, contact_name, phone, email, address

8. **PurchaseOrders**
   - id (PK), vendor_id (FK), inventory_item_id (FK), quantity, cost, order_date

9. **StockMovements**
   - id (PK), inventory_item_id (FK), quantity_change, reason, date, related_job_id

## System Architecture

### Development Approach
- **Semi-Agile with Async-First Workflow**
  - Basecamp for project management
  - GitHub for version control and CI/CD
  - Minimal synchronous meetings
  - Asynchronous code reviews and demos
  - Bi-weekly sprint planning and retrospectives

### AI Integration Strategy
1. **Code Generation**
   - Component scaffolding with AI
   - Test case generation
   - Documentation auto-generation

2. **Quality Assurance**
   - Automated code reviews
   - Performance optimization suggestions
   - Security vulnerability scanning

3. **Developer Experience**
   - AI pair programming
   - Context-aware code completion
   - Automated refactoring suggestions

## System Components

### 1. Authentication & Authorization
- **Firebase Authentication** for user management
- Role-based access control (Admin, Manager, Technician, Front Desk)
- Session management with configurable timeout policies
- Multi-factor authentication for sensitive operations

### 2. Inventory Management
- Real-time SKU tracking with custom attributes
- Bulk import/export functionality (CSV/Excel)
- Multi-location inventory tracking
- Barcode/QR code generation and scanning
- Version history and audit logging

### 3. Estimating System
- Dynamic estimate generation with line items
- Automated material and labor cost calculations
- Client approval workflows with digital signatures
- Inventory reservation system
- Conversion rate and profitability tracking

### 4. Job Management
- Visual job board with drag-and-drop interface
- Configurable workflow stages
- Real-time inventory updates
- File attachments and internal notes
- Job costing and profitability tracking

### 5. Time & Attendance
- Web and mobile time tracking
- Automated overtime calculations
- Payroll system integration (CSV/API)
- Labor cost tracking against jobs

### 6. Invoicing & Payments
- Branded invoice generation
- Multiple payment method support
- Automated payment tracking and reminders
- Receipt generation

### 7. Reporting & Analytics
- Real-time KPI dashboards
- Custom report builder
- Data export (PDF, Excel, CSV)
- Historical trend analysis

## Security Architecture

### Authentication & Authorization
- **Firebase Authentication** with JWT and secure cookies
- **Role-based access control (RBAC)** with custom claims
- **Session management** with configurable timeouts
- **Multi-factor authentication** for admin operations
- **SSO integration** with enterprise providers

### Data Protection
- **Encryption in transit**: TLS 1.3+ for all communications
- **Encryption at rest**: Firestore and Firebase Storage encryption
- **Field-level security**: Firestore security rules
- **Data retention policies**: Automated cleanup of old data
- **Backup strategy**: Daily automated backups with 30-day retention

### Compliance & Monitoring
- **GDPR/CCPA compliance**: Data subject requests handling
- **Audit logging**: All sensitive operations logged
- **Security monitoring**: Real-time alerting for suspicious activities
- **Penetration testing**: Quarterly security assessments
- **Vulnerability scanning**: Dependabot for dependency updates

## Performance Considerations

### Frontend Optimization
- **Code splitting** with dynamic imports
- **Image optimization** with Next.js Image component
- **Client-side caching** with SWR
- **PWA** for offline capabilities
- **Web Vitals monitoring** with RUM
- **Bundle analysis** for size optimization

### Database Optimization
- **Serverless architecture** with auto-scaling
- **Firestore indexing** strategy
- **PostgreSQL partitioning** for time-series data
- **TimescaleDB** for efficient time-series analytics
- **Query optimization** with composite indexes
- **Caching layer** with Redis (if needed)
- **Cold start mitigation** for Cloud Functions
- **Connection pooling** for database connections

### AI-Assisted Optimization
- **Performance insights** from Firebase Monitoring
- **Automated code splitting** suggestions
- **Bundle size optimization** recommendations
- **Database query optimization** suggestions

## Deployment Architecture

### Development Environment
- **Docker-based** with docker-compose
- **Hot-reloading** for all services
- **Mock services** for external APIs
- **Automated testing** with Jest and Cypress
- **Pre-commit hooks** with Husky
- **AI-assisted code reviews**

### Staging Environment
- **Vercel Preview Deployments** for each PR
- **Firebase staging project**
- **Automated E2E tests**
- **Performance benchmarking**
- **UAT sign-off** process
- **Smoke testing** automation

### Production Environment
- **Vercel Edge Network** for global CDN
- **Firebase production project**
- **Automated blue-green deployments**
- **Feature flags** for controlled rollouts
- **Real-user monitoring**
- **Automated rollback** on failures
- **SLA monitoring** with status page

## Monitoring & Maintenance

### Logging & Observability
- **Centralized logging** with Firebase Logging
- **Structured logging** with severity levels
- **Log retention**: 30 days standard, 1 year for audit logs
- **Real-time alerting** for critical errors
- **Distributed tracing** for requests

### Performance Monitoring
- **Real User Monitoring (RUM)**
- **Custom performance metrics**
- **Database query analysis**
- **API performance** with response time percentiles
- **Frontend Web Vitals** tracking
- **AI-powered anomaly detection**

### Backup & Disaster Recovery
- **Daily automated backups**
- **Point-in-time recovery** capability
- **Disaster recovery** runbook
- **Quarterly DR drills**
- **Geographic redundancy** for critical data
- Automated database backups
- Point-in-time recovery
- Disaster recovery procedures
- Regular backup testing

## Future Enhancements

### Short-term
- Mobile application development
- Advanced analytics dashboard
- Enhanced reporting capabilities

### Medium-term
- Machine learning for demand forecasting
- Predictive maintenance scheduling
- Automated inventory optimization

### Long-term
- IoT integration for equipment monitoring
- Blockchain for supply chain transparency
- AI-powered customer service chatbot

## Appendix

### API Documentation
- Swagger/OpenAPI specification
- Authentication requirements
- Rate limiting details
- Error handling

### Deployment Guide
- Infrastructure as Code (Terraform)
- Environment setup
- Configuration management
- Scaling considerations

### Development Guidelines
- Code style and standards
- Git workflow
- Code review process
- Testing requirements

---
*This document is a living document and should be updated as the system evolves.*