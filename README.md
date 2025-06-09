# Valor ERP - Modern Manufacturing Management System

<div align="center">
  <img src="https://img.shields.io/badge/Next.js-14.2.3-000000?style=for-the-badge&logo=nextdotjs" alt="Next.js 14.2.3">
  <img src="https://img.shields.io/badge/React-18.2.0-61DAFB?style=for-the-badge&logo=react" alt="React 18.2.0">
  <img src="https://img.shields.io/badge/Firebase-FFCA28?style=for-the-badge&logo=firebase&logoColor=black" alt="Firebase">
  <img src="https://img.shields.io/badge/Tailwind_CSS-38B2AC?style=for-the-badge&logo=tailwind-css&logoColor=white" alt="Tailwind CSS">
  <img src="https://img.shields.io/badge/TypeScript-3178C6?style=for-the-badge&logo=typescript&logoColor=white" alt="TypeScript">
  <img src="https://img.shields.io/badge/Vercel-000000?style=for-the-badge&logo=vercel&logoColor=white" alt="Vercel">
  <img src="https://img.shields.io/badge/PostgreSQL-4169E1?style=for-the-badge&logo=postgresql&logoColor=white" alt="PostgreSQL">
</div>

## 🌟 Overview

Valor ERP is a cutting-edge, cloud-based Enterprise Resource Planning (ERP) system specifically designed for metalworking companies. This comprehensive solution streamlines business operations from initial estimates to final invoicing, with a strong emphasis on user experience, real-time data synchronization, and AI-assisted development.

**Live Demo**: [Valor ERP Demo](https://valor.appsandsides.com/)

## 🚀 Key Features

| Feature | Description |
|---------|-------------|
| 📊 **Estimating System** | Create detailed estimates with automatic material and labor cost calculations |
| 🏭 **Job Management** | Track jobs through configurable workflow stages with drag-and-drop interface |
| 📦 **Inventory Control** | Real-time SKU tracking with barcode support and multi-location management |
| ⏱️ **Time & Attendance** | Web and mobile time tracking with automated overtime calculations |
| 💰 **Invoicing** | Generate professional invoices with multiple payment method support |
| 📈 **Reporting** | Customizable dashboards with real-time KPIs and analytics |
| 🔒 **Role-Based Access** | Granular permissions for different user roles |
| 📱 **Mobile-Ready** | Progressive Web App (PWA) for access on any device |

## 🛠️ Technology Stack

### Frontend
- **Framework**: Next.js 14 with React 18
- **Styling**: Tailwind CSS with shadcn/ui components
- **State Management**: React Context + SWR
- **Progressive Web App**: Offline-first capabilities
- **Type Safety**: TypeScript

### Backend
- 🔐 **Authentication**: Firebase Auth with JWT
- 🔥 **Primary Database**: Firestore (NoSQL)
- 🐘 **Analytics Database**: PostgreSQL 
- ⚡ **Serverless Functions**: Firebase Cloud Functions
- 📁 **File Storage**: Firebase Storage
- 🔄 **Real-time Updates**: Firestore listeners
- 📲 **Push Notifications**: Firebase Cloud Messaging
- 🐘 **Data Warehouse**: PostgreSQL with TimescaleDB extension

### DevOps & Tools
- **Version Control**: GitHub
- **CI/CD**: GitHub Actions
- **Hosting**: Vercel (Frontend), Firebase (Backend)
- **Containerization**: Docker + Docker Compose
- **AI-Assisted Development**: Claude Sonnet 4, GitHub Copilot, Cursor, Zed
- **Project Management**: Basecamp

## 🏗️ System Architecture

```
┌─────────────────────────────────┐     ┌───────────────────────────────────┐
│          Frontend              │     │            Backend                │
│  ┌─────────────────────────┐   │     │   ┌─────────────────────────┐    │
│  │  Next.js PWA (React 18) │   │     │   │     Firebase Services     │    │
│  └────────────���────────────┘   │     │   │  ┌────────┐ ┌─────────┐  │    │
│  ┌─────────────────────────┐   │     │   │  │  Auth  │ │ Storage │  │    │
│  │  Tailwind + shadcn/ui   │   │     │   │  └────────┘ └─────────┘  │    │
│  └─────────────────────────┘   │◄───►│   │  ┌────────┐ ┌─────────┐  │    │
│  ┌─────────────────────────┐   │     │   │  │Firestore│ │ Cloud   │  │    │
│  │  TypeScript + SWR       │   │     │   │  │         │ │Functions│  │    │
│  └─────────────────────────┘   │     │   │  └────────┘ └─────────┘  │    │
└─────────────────────────────────┘     └───────────────────────────────────┘
        ▲                                                    ▲
        │                                                    │
        ▼                                                    ▼
┌─────────────────────────┐               ┌───────────────────────────────────┐
│     Client Devices      │               │      Development & DevOps         │
│  ┌─────────┐ ┌───────┐  │               │  ┌──────────┐  ┌─────────────┐   │
│  │ Desktop │ │Mobile │  │               │  │  Docker  │  │ GitHub      │   │
│  │ Browser │ │ PWA   │  │               │  │          │  │ Actions     │   │
│  └─────────┘ └───────┘  │               │  └──────────┘  └─────────────┘   │
└─────────────────────────┘               └───────────────────────────────────┘
```

## 📅 Project Timeline

| Phase | Description | Duration | Status |
|-------|-------------|----------|--------|
| 1 | Foundation & Architecture | 8-12 weeks | ✅ Completed |
| 2 | Inventory Management | 10-14 weeks | 🔄 In Progress |
| 3 | Estimating System | 12-16 weeks | ⏳ Planned |
| 4 | Job Management | 12-16 weeks | ⏳ Planned |
| 5 | Time & Attendance | 8-12 weeks | ⏳ Planned |
| 6 | Invoicing | 6-10 weeks | ⏳ Planned |
| 7 | Reporting & Analytics | 10-14 weeks | ⏳ Planned |

**Total Project Duration**: 18 months

## 🚀 Getting Started

### Prerequisites
- Node.js 18+
- npm or yarn
- Firebase CLI
- Docker Desktop (for local development)

### Local Development

1. **Clone the repository**
   ```bash
   git clone https://github.com/your-organization/valor-erp.git
   cd erp-manufacturing
   ```

2. **Install dependencies**
   ```bash
   npm install
   # or
   yarn
   ```

3. **Set up environment variables**
   ```bash
   cp .env.local.example .env.local
   # Update the environment variables in .env.local
   ```

4. **Start the development server**
   ```bash
   npm run dev
   # or
   yarn dev
   ```

5. **Open [http://localhost:3000](http://localhost:3000) in your browser**

### Deployment

1. **Build the application**
   ```bash
   npm run build
   # or
   yarn build
   ```

2. **Deploy to Vercel**
   - Connect your GitHub repository to Vercel
   - Configure environment variables
   - Deploy!

3. **Deploy Firebase Functions**
   ```bash
   firebase login
   firebase deploy --only functions
   ```

## 📚 Documentation

- [Business Requirements (BRD)](docs/2-business_requirements.md)
- [Product Requirements (PRD)](docs/3-product_requirements.md)
- [Requirements Tracker](docs/4-requirements_tracker.md)
- [System Design](docs/6-system_design.md)
- [Schema](docs/6-schema)
- [Tech Stack](docs/5-tech_stack.md)

## 🤝 Contributing

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 📧 Contact

For inquiries, please contact the Valor ERP team at [contact@valorerp.com](mailto:contact@valorerp.com)

---

<div align="center">
  Made with ❤️ by Valor ERP Development Team
</div>
