<h1 align="center">📂 Project Portfolio</h1>
<h3 align="center">Full-Stack Software Engineer — Private Repository Showcase</h3>

<p align="center">
  <em>My repositories are private to protect proprietary and commercial code.<br/>
  This portfolio provides comprehensive documentation of each project's scope, architecture, and capabilities.</em>
</p>

---

## Table of Contents

1. [AgriFarm AI — Dairy Farm Management Platform](#1--agrifarm-ai--ai-powered-dairy-farm-management-platform)
2. [HMIS Web — Hospital Management Information System](#2--hmis-web--hospital-management-information-system)
3. [MedCom HMIS — Legacy Healthcare Desktop System](#3--medcom-hmis--legacy-healthcare-desktop-system)
4. [Smart Shift Planner — AI-Driven Gig Economy Scheduler](#4--smart-shift-planner--ai-driven-gig-economy-scheduler)
5. [HealthX Dawa — Pharmaceutical E-Commerce Platform](#5--healthx-dawa--pharmaceutical-e-commerce-platform)
6. [HealthX USSD — Telemedicine & Micro-Insurance USSD Platform](#6--healthx-ussd--telemedicine--micro-insurance-ussd-platform)
7. [HXA STK Push Initiator — M-Pesa Payment Collection System](#7--hxa-stk-push-initiator--m-pesa-payment-collection-system)
8. [HXA WhatsApp Ads Bot — Conversational Booking & Payments Engine](#8--hxa-whatsapp-ads-bot--conversational-booking--payments-engine)
9. [Admark Enterprises — Corporate Branding & Promotional Products Website](#9--admark-enterprises--corporate-branding--promotional-products-website)
10. [Skills & Technology Summary](#-skills--technology-summary)

---

## 1. 🐄 AgriFarm AI — AI-Powered Dairy Farm Management Platform

> **Smart herd management SaaS built specifically for African dairy farmers.**  
> Subscription-based platform with AI-powered diagnostics, production analytics, and mobile money payments.

### Architecture Overview

Distributed microservices architecture with API gateway, dedicated services for each business domain, and a modern React frontend. Full production observability stack with distributed tracing, metrics collection, and centralized logging.

```
┌──────────────────────────────────────────────────────────┐
│                    API GATEWAY                            │
│              (SSL · Rate Limiting · Routing)               │
├──────────────────────────────────────────────────────────┤
│                                                            │
│     Multiple Domain-Specific Microservices                 │
│     (Authentication · Herd Management · Health ·           │
│      Production · AI · Payments · Notifications ·          │
│      Reports · Media)                                      │
│                                                            │
│  ┌──────────────────────────────────────────────────┐     │
│  │              React Frontend (SPA)                 │     │
│  └──────────────────────────────────────────────────┘     │
│                                                            │
├──────────────────────────────────────────────────────────┤
│  PostgreSQL  │  Redis (Cache & Queue)  │  Object Storage  │
└──────────────────────────────────────────────────────────┘
│              Observability & Monitoring Stack              │
└──────────────────────────────────────────────────────────┘
```

### Tech Stack

| Layer | Technology |
|-------|-----------|
| **Frontend** | React 18 + TypeScript + Vite |
| **Backend** | Node.js 20 + Express (Microservices) |
| **Database** | PostgreSQL 16 + Redis 7 |
| **ORM** | Prisma |
| **API Gateway** | Nginx |
| **File Storage** | S3-compatible object storage |
| **Monitoring** | OpenTelemetry + Prometheus + Grafana |
| **Payments** | Stripe + M-Pesa (Safaricom Daraja API) |
| **Notifications** | SMS + Email |
| **AI** | LLM-powered diagnostics + image analysis |
| **Queue** | Redis-backed job queue |
| **Containerization** | Docker + Docker Compose |
| **CI/CD** | GitHub Actions |

### Key Features

- **AI-Powered Diagnostics** — Intelligent health analysis with image and video support
- **Production Analytics** — ML-based anomaly detection and trend analysis
- **Reproductive Management** — Cycle tracking and predictive scheduling
- **Herd Health Scoring** — Automated wellness assessment across the herd
- **Genealogy Tracking** — Full lineage and breeding history
- **Mobile Money Payments** — Native M-Pesa integration for subscriptions
- **Multi-Role Access Control** — Granular permissions across multiple user roles
- **Real-Time Alerts** — SMS notifications for critical events
- **Comprehensive Reporting** — PDF and Excel exports for production, financials, and health
- **SaaS Admin Portal** — Platform management dashboard with subscription tiers

### Platform Scale

- Multiple microservices with independent scaling
- Tiered subscription model (Free through Enterprise)
- 26+ frontend pages covering all farm management workflows
- Full production observability across all services

---

## 2. 🏥 HMIS Web — Hospital Management Information System

> **Cloud-native, multi-tenant Hospital Management SaaS.**  
> Modernizing healthcare IT in East Africa — migrating from legacy Java desktop to production-grade web platform with enterprise licensing.

### Architecture: Multi-Tenant SaaS

```
┌─────────────────────────────────────────────────┐
│              NGINX REVERSE PROXY                  │
│        (Rate Limiting · Security Headers)          │
├─────────────────────────────────────────────────┤
│                                                    │
│  ┌──────────────┐       ┌───────────────────┐     │
│  │   React 19   │◄─────►│    NestJS API     │     │
│  │   Frontend   │  JWT  │   (Fastify)       │     │
│  │  Ant Design  │       │                   │     │
│  │   Zustand    │       │  ┌─────────────┐  │     │
│  └──────────────┘       │  │ Auth Module  │  │     │
│                          │  │ License Mod  │  │     │
│                          │  │ Org Module   │  │     │
│                          │  │ Branch Module│  │     │
│                          │  │ User Module  │  │     │
│                          │  │ SuperAdmin   │  │     │
│                          │  └─────────────┘  │     │
│                          └───────────────────┘     │
│                                                    │
├─────────────────────────────────────────────────┤
│     PostgreSQL 16     │      Redis 7 (Cache)      │
└─────────────────────────────────────────────────┘
```

### Tech Stack

| Layer | Technology |
|-------|-----------|
| **Frontend** | React 19 + Vite + TypeScript + Ant Design 5.x |
| **State Management** | Zustand |
| **Backend** | NestJS + Fastify (TypeScript) |
| **Database** | PostgreSQL 16 |
| **Cache** | Redis 7 |
| **ORM** | Prisma |
| **Auth** | JWT + 2FA (TOTP) + BCrypt (12 rounds) |
| **API Gateway** | Nginx (rate limiting, security headers) |
| **Monitoring** | OpenTelemetry + Winston logging |
| **Containerization** | Docker + Docker Compose |
| **Infrastructure** | Kubernetes-ready (health checks, init containers) |

### Multi-Tenancy Model

```
Platform (Super Admin)
  └── Organization (Hospital Group)
        ├── Branch A (Main Hospital)
        │     ├── Users (doctors, nurses, admin)
        │     └── Clinical & financial data (branch-scoped)
        ├── Branch B (Satellite Clinic)
        │     ├── Users
        │     └── Data (fully isolated)
        └── License Management
```

- **Branch-scoped data isolation** — Complete data separation between branches
- **Branch-aware authentication** — Multi-step login with organization and branch selection
- **Token-scoped access** — Authentication tokens carry organization and branch context

### SaaS Licensing Engine

- Custom license key generation and validation
- Multiple duration types with configurable billing cycles
- Status lifecycle management with grace periods
- Automated expiry reminders and enforcement
- Full audit trail for all license events

### Phase 1 Features (Complete)

| Module | Features |
|--------|----------|
| **Infrastructure** | Container orchestration, structured logging, reverse proxy, health checks, global exception handling |
| **Multi-Tenancy** | Organization + Branch hierarchy, branch-scoped data isolation, branch-aware authentication |
| **Licensing** | License management, key generation, status lifecycle, enforcement guards, grace periods, expiry reminders |
| **Super Admin** | Organization provisioning, branch management, license operations, dashboard + audit log |
| **Authentication** | Branch-aware JWT, password hashing, 2FA via TOTP, account lockout protection |
| **RBAC** | Page-level rights system, role-based user management, branch-scoped permissions |

### Planned Phases

| Phase | Scope |
|-------|-------|
| **Phase 2** | Clinical — EMR, outpatient/inpatient, prescriptions, lab, radiology, pharmacy, triage, nursing |
| **Phase 3** | Financial — Billing, accounts, POS, debtors, insurance claims, financial reports |
| **Phase 4** | Supply Chain — Procurement, inventory, journal entries, purchase orders |

---

## 3. 💊 MedCom HMIS — Legacy Healthcare Desktop System

> **Production Java desktop application running live at Komarock Modern Healthcare, Nairobi.**  
> Comprehensive hospital management covering clinical, financial, and administrative workflows.

### Architecture: Java Swing Desktop Application

```
┌─────────────────────────────────────────────┐
│           JAVA SWING APPLICATION              │
│                                               │
│  ┌───────────┐ ┌───────────┐ ┌───────────┐  │
│  │ Dashboard │ │ Clinical  │ │  Billing  │  │
│  └───────────┘ └───────────┘ └───────────┘  │
│  ┌───────────┐ ┌───────────┐ ┌───────────┐  │
│  │Laboratory │ │ Pharmacy  │ │ Radiology │  │
│  └───────────┘ └───────────┘ └───────────┘  │
│  ┌───────────┐ ┌───────────┐ ┌───────────┐  │
│  │ Accounts  │ │  Payroll  │ │   Stock   │  │
│  └───────────┘ └───────────┘ └───────────┘  │
│  ┌───────────┐ ┌───────────┐ ┌───────────┐  │
│  │Procurement│ │  Triage   │ │  Reports  │  │
│  └───────────┘ └───────────┘ └───────────┘  │
│  ┌───────────┐ ┌───────────────────────────┐ │
│  │  Admin    │ │  System Rights & Settings │ │
│  └───────────┘ └───────────────────────────┘ │
│                                               │
├─────────────────────────────────────────────┤
│          MariaDB (LAN Database)               │
└─────────────────────────────────────────────┘
```

### Tech Stack

| Layer | Technology |
|-------|-----------|
| **Language** | Java (Swing GUI) |
| **Build Tool** | Apache Ant |
| **IDE** | NetBeans |
| **Database** | MariaDB |
| **PDF Generation** | iText / similar |
| **Excel Export** | Apache POI |
| **Printing** | Thermal receipt printer integration |
| **Deployment** | Desktop (LAN with shared database) |

### Modules (16 Total)

| Module | Description |
|--------|-------------|
| **Dashboard** | System overview, quick stats, patient queue |
| **Clinical** | Patient records, doctor clerking, consultation notes |
| **Triage** | Vitals recording, patient prioritization, queue management |
| **Billing** | Invoice generation, bill amendments, waiver management |
| **Accounts** | Financial management, debtors tracking, petty cash |
| **Laboratory** | Test ordering, parameterised results, report generation |
| **Radiology** | Imaging requests, results management |
| **Pharmacy** | Drug dispensing, stock management, prescriptions |
| **Stock** | Hospital-wide inventory management |
| **Procurement** | Purchase orders, supplier management, multi-department requisitions |
| **Payroll** | Employee salary management |
| **Reports** | PDF + Excel comprehensive reporting |
| **Administration** | System configuration, user management |
| **System Rights** | Role-based access control configuration |
| **POS** | Point-of-sale for OPD/inpatient payments |
| **Insurance** | Insurance scheme management & claims |

### Production Deployment

- **Live at:** A healthcare facility in Nairobi, Kenya
- **Users:** Doctors, nurses, pharmacists, lab technicians, billing clerks, administrators

> 🔄 **Currently being migrated** to HMIS Web (Project #2 above) for cloud-native, multi-tenant capability.

---

## 4. 📊 Smart Shift Planner — AI-Driven Gig Economy Scheduler

> **BSc Computer Science Final Year Project.**  
> AI-powered earnings prediction and income guarantee system for UK gig economy drivers.  
> Uses machine learning to optimize shift scheduling and reduce income volatility.

### Architecture: Full-Stack ML Application

```
┌───────────────────────────────────────────────────┐
│                 NGINX REVERSE PROXY                │
├───────────────────────────────────────────────────┤
│                                                     │
│  ┌──────────────────┐    ┌──────────────────────┐  │
│  │   Next.js 14     │    │   FastAPI (Python)    │  │
│  │   Frontend       │◄──►│   Backend            │  │
│  │                  │    │                      │  │
│  │  • Driver Dash   │    │  ┌────────────────┐  │  │
│  │  • Admin Dash    │    │  │ ML Engine      │  │  │
│  │  • Analytics     │    │  │ (scikit-learn) │  │  │
│  │  • Surveys       │    │  ├────────────────┤  │  │
│  └──────────────────┘    │  │ Shift Optimizer│  │  │
│                          │  ├────────────────┤  │  │
│                          │  │ Guarantee Eng. │  │  │
│                          │  ├────────────────┤  │  │
│                          │  │ Demand Forecast│  │  │
│                          │  └────────────────┘  │  │
│                          └──────────────────────┘  │
│                                                     │
├───────────────────────────────────────────────────┤
│              PostgreSQL 16 Database                 │
└───────────────────────────────────────────────────┘
│            GitHub Actions CI/CD Pipeline            │
└───────────────────────────────────────────────────┘
```

### Tech Stack

| Layer | Technology |
|-------|-----------|
| **Frontend** | Next.js 14 + React 18 + TypeScript + Tailwind CSS |
| **State Management** | Zustand |
| **Charts** | Recharts |
| **Backend** | Python 3.12 + FastAPI + Uvicorn |
| **Database** | PostgreSQL 16 |
| **ORM** | SQLAlchemy 2.0 |
| **Migrations** | Alembic |
| **ML Framework** | scikit-learn (RandomForestRegressor) |
| **Data Processing** | pandas + NumPy + SciPy |
| **Authentication** | JWT (python-jose) + bcrypt |
| **Containerization** | Docker + Docker Compose |
| **CI/CD** | GitHub Actions (test → build → deploy) |
| **Reverse Proxy** | Nginx |

### Research Questions

| # | Question | Approach |
|---|----------|----------|
| **RQ1** | How accurate is AI-based shift scheduling for predicting gig driver earnings? | Hybrid ML model + accuracy metrics (MAE, MAPE, RMSE, R²) |
| **RQ2** | Does shift recommendation reduce income volatility? | Before/after volatility analysis with statistical tests |
| **RQ3** | Does an income guarantee mechanism reduce financial stress? | Survey analysis (Likert scale) + top-up activation tracking |

### Machine Learning Pipeline

#### Hybrid Earnings Predictor

Two-layer prediction model combining deterministic business rules with machine learning:

- **Layer 1** — Rule-based model with location-specific base rates, time-of-day multipliers, day-of-week adjustments, and real-time demand scaling
- **Layer 2** — Random Forest model trained on historical data when available, with cross-validation and feature importance analysis

#### Supporting ML Components
- **Demand Forecaster** — Location-typed demand curves with trend analysis and peak hour identification
- **Shift Optimizer** — Evaluates all possible start-time and location combinations to rank optimal shifts
- **Accuracy Analyzer** — Comprehensive metrics (MAE, MAPE, RMSE, R²) with quality thresholds

### Income Guarantee Engine

Automatic safety-net system that calculates top-ups when actual earnings fall below a guaranteed threshold. Tracks eligibility, activation rates, and sustainability metrics.

### Frontend Dashboards

**Driver Dashboard** — Earnings prediction, shift recommendations, income guarantee tracking, volatility analysis, performance trends, and analytics

**Admin Dashboard** — System analytics, model accuracy monitoring, driver management, guarantee overview, survey reports, sustainability metrics, and audit trail

### API Coverage: 57+ Endpoints

Auth · Shifts · Predictions · Analytics · Admin Management · Accuracy Metrics · Surveys · Guarantee Management

### Deployment

- **Development:** Docker Compose (PostgreSQL + FastAPI + Next.js)
- **Production:** VPS with Nginx reverse proxy
- **CI/CD:** GitHub Actions (automated test → build → deploy pipeline)

---

## 5. 💊 HealthX Dawa — Pharmaceutical E-Commerce Platform

> **Full-featured online pharmacy serving both prescription and OTC drug sales in Kenya.**
> Complete e-commerce platform with M-Pesa & PesaPal payments, prescription fulfillment, telehealth consultations, logistics integration, and multi-role admin dashboard.

### Architecture: PHP MVC E-Commerce Platform

```
┌──────────────────────────────────────────────────────────┐
│                    APACHE / NGINX                         │
│              (SSL · .htaccess Routing)                    │
├──────────────────────────────────────────────────────────┤
│                                                          │
│  ┌──────────────┐  ┌──────────────┐  ┌──────────────┐   │
│  │   Customer    │  │    Admin     │  │    API       │   │
│  │   Frontend    │  │  Dashboard   │  │  Endpoints   │   │
│  │  (22 pages)   │  │ (15 modules) │  │  (12 routes) │   │
│  └──────────────┘  └──────────────┘  └──────────────┘   │
│                                                          │
│  ┌──────────────┐  ┌──────────────┐  ┌──────────────┐   │
│  │  M-Pesa STK  │  │  PesaPal v3  │  │ Fargo Courier│   │
│  │   Payment    │  │   Payment    │  │  Logistics   │   │
│  └──────────────┘  └──────────────┘  └──────────────┘   │
│                                                          │
│  ┌──────────────┐  ┌──────────────┐  ┌──────────────┐   │
│  │   Google     │  │  SMS/Email   │  │ Prescription │   │
│  │    OAuth     │  │ Notifications│  │ Fulfillment  │   │
│  └──────────────┘  └──────────────┘  └──────────────┘   │
│                                                          │
├──────────────────────────────────────────────────────────┤
│  MySQL/MariaDB  │  PHP Sessions  │  PHPMailer (SMTP)    │
└──────────────────────────────────────────────────────────┘
```

### Tech Stack

| Layer | Technology |
|-------|------------|
| **Backend** | PHP 7.4+ (Custom MVC architecture) |
| **Database** | MySQL / MariaDB |
| **Frontend** | HTML5 + CSS3 + Bootstrap 5.3 + Vanilla JS |
| **Payments** | M-Pesa STK Push + PesaPal v3 API |
| **Auth** | PHP Sessions + Google OAuth + Facebook OAuth + 2FA (SMS OTP) |
| **Email** | PHPMailer (Microsoft 365 / Exchange SMTP) |
| **SMS** | VasPro SMS API |
| **Logistics** | Fargo Courier API |
| **Icons** | Font Awesome 6.4 |
| **Server** | Apache / Nginx with SSL |

### Customer Features (22 Pages)

| Module | Features |
|--------|----------|
| **Product Shop** | Advanced filtering (category, subcategory, price range, brand, Rx/OTC type), product details, image gallery, reviews |
| **Cart & Checkout** | Hybrid cart (products + services), coupon integration, multiple delivery zones, express & standard options, smart pricing |
| **Prescription Flow** | Upload prescription image, request doctor prescription, Rx/OTC/Mixed order prefixes (RX-, OTC-, MX-), verification workflow |
| **Telehealth** | Doctor, pharmacist, nutritionist, psychologist & wellness consultations with OTP-verified booking |
| **Wellness Packages** | Lab test packages (gender-targeted), home-delivery option, featured wellness programs |
| **Order Tracking** | Dynamic timeline (Submitted → Consultation → Payment → Processing → Ready → Dispatched → Delivered → Completed) |
| **Payments** | M-Pesa STK Push, PesaPal multi-channel, insurance-integrated checkout |
| **Account** | Profile management, saved delivery addresses, wishlist, order history, 2FA opt-in |

### Admin Dashboard (15 Modules)

| Module | Capabilities |
|--------|--------------|
| **Products** | Add/edit/delete, stock management with reorder levels, bulk actions, prescription-required tagging, image uploads |
| **Orders** | Full fulfillment workflow (Pending → Received → Preparing → Ready → Dispatched → Delivered → Completed), SMS notifications, stock deduction |
| **Prescriptions** | Approve/reject, medication assignment from product DB, pricing, dispatch tracking, TAT monitoring |
| **Categories** | Hierarchical categories with icons |
| **Users** | Role-based management (customer, pharmacist, admin, delivery), status & password control |
| **Permissions** | Granular permission system for staff access control |
| **Reports** | Sales analytics (daily/weekly/monthly/yearly), inventory analytics, TAT & delivery performance, user metrics |
| **Fargo Courier** | Shipment creation, real-time tracking, status updates, API integration |
| **M-Pesa Transactions** | Transaction history, callback logs, reconciliation |
| **Email & SMS** | Multi-channel communication with context-aware templates |
| **Logs** | System activity logs and audit trail |

### Payment Integrations

**M-Pesa (Kenya Mobile Money):**
- STK Push for direct mobile payments
- Real-time callback processing with order status updates
- Transaction logging and reconciliation

**PesaPal (Multi-Channel Gateway):**
- Multi-channel support: cards, mobile money, bank transfers
- Webhook-based payment notifications
- Transaction verification and status queries

### Logistics & Delivery

- Multiple delivery zones with dynamic pricing
- Same-day express and standard delivery options
- Courier API integration for shipment tracking
- Multi-stage fulfillment pipeline with TAT monitoring

### Security

- CSRF token validation on all forms
- Prepared statements for SQL injection prevention
- Account lockout protection
- Password hashing with modern algorithms
- SSL/TLS enforcement

---

## 6. 📱 HealthX USSD — Telemedicine & Micro-Insurance USSD Platform

> **Production USSD microservice enabling healthcare access on any phone — including feature phones.**  
> Customers dial a USSD short code to purchase telemedicine consultations, micro-insurance, wellness subscriptions, and health content — all paid via M-Pesa. Built for a telehealth company in Nairobi, Kenya.

### Architecture: USSD Microservice Platform

```
┌──────────────────────────────────────────────────────────────┐
│                    USSD Gateway Provider                      │
│                   (Inbound USSD Callback)                     │
├──────────────────────────────────────────────────────────────┤
│                                                                │
│  ┌────────────┐   ┌──────────────┐   ┌────────────────────┐  │
│  │  Web       │   │  Controller  │   │   USSD Flow        │  │
│  │  Server    │──►│  (Routing)   │──►│   Engine           │  │
│  │            │   │              │   │                    │  │
│  └────────────┘   └──────────────┘   └────────┬───────────┘  │
│                                               │               │
│  ┌────────────┐   ┌──────────────┐   ┌────────┴───────────┐  │
│  │  Dynamic   │   │   Cache      │   │  Payment Service   │  │
│  │  Menu      │◄──│   Manager    │   │  (M-Pesa STK)     │  │
│  │  Builder   │   │              │   └────────┬───────────┘  │
│  └────────────┘   └──────────────┘            │               │
│                                               ▼               │
│  ┌────────────┐   ┌──────────────┐   ┌────────────────────┐  │
│  │  Insurance │   │  Healthcare  │   │  Notification      │  │
│  │  API       │   │  Product     │   │  SMS + WhatsApp    │  │
│  │  Client    │   │  APIs        │   │  + Email           │  │
│  └────────────┘   └──────────────┘   └────────────────────┘  │
│                                                                │
├──────────────────────────────────────────────────────────────┤
│  MariaDB/MySQL (Connection Pool)  │  In-Memory Cache         │
└──────────────────────────────────────────────────────────────┘
│              Observability & Monitoring Stack                  │
└──────────────────────────────────────────────────────────────┘
```

### Tech Stack

| Layer | Technology |
|-------|------------|
| **Runtime** | Node.js + Express |
| **Database** | MariaDB/MySQL (connection pooling) |
| **Caching** | In-memory cache for sessions and menu data |
| **Logging** | Structured logging with daily rotation |
| **Monitoring** | APM + error tracking + distributed tracing |
| **Security** | Security headers + CORS |
| **Payments** | M-Pesa (Safaricom Daraja API — STK Push) |
| **Insurance** | Third-party insurance REST API |
| **SMS** | SMS Gateway |
| **WhatsApp** | Meta WhatsApp Cloud API |
| **Email** | SMTP integration |
| **Scheduling** | Cron-based background jobs |
| **Process Manager** | PM2 |

### USSD Service Offerings

- **Doctor Consultations** — Multiple subscription durations
- **Psychology Services** — Individual, couple, family, and coaching options
- **Nutrition Consultation**
- **Micro-Insurance (Riders)** — Accident and injury coverage with tiered plans
- **Micro-Insurance (General)** — Funeral expense and hospitalization coverage
- **Health Tips Subscription** — SMS-based curated health content
- **Account Settings** — Profile, next of kin, policy history management

### Key Integrations

- **M-Pesa STK Push** — Payment initiation within USSD flow with automatic policy/subscription creation on successful payment
- **Insurance Underwriting API** — Real-time policy creation and management
- **Multi-channel Notifications** — SMS + WhatsApp + Email for confirmations and reminders
- **KYC Collection** — Multi-step identity verification within the USSD session

### Technical Highlights

- **Dynamic Menu Builder** — USSD menus generated from cached service and pricing data
- **Session Management** — Database-backed sessions with configurable expiry
- **Policy Retry Engine** — Automatic retry for failed external API calls
- **Multi-channel Notifications** — Dual SMS + WhatsApp for critical messages
- **Connection Pooling** — Optimized database connections with health monitoring
- **Template System** — Database-stored message templates with variable substitution
- **Background Jobs** — Session expiry, policy reminders, retry processing, renewal campaigns

---

## 7. 💳 HXA STK Push Initiator — M-Pesa Payment Collection System

> **Automated payment collection for HealthX Africa healthcare subscriptions.**  
> Django-based system integrating Safaricom M-Pesa STK Push to silently initiate mobile money payments for healthcare service packages.

### Architecture

```
┌──────────────────────────────────────────────────────────────┐
│                    KONG API GATEWAY                          │
│              (SSL · Rate Limiting · Routing)                 │
├──────────────────────────────────────────────────────────────┤
│                                                              │
│  ┌────────────────────────────────────────────────────────┐  │
│  │              Django Application (Gunicorn)             │  │
│  │                                                        │  │
│  │  ┌──────────┐  ┌──────────┐  ┌───────────────────┐   │  │
│  │  │  Admin   │  │  M-Pesa  │  │  Signal Handlers  │   │  │
│  │  │Dashboard │  │   API    │  │  (Auto-triggers)  │   │  │
│  │  └──────────┘  └──────────┘  └───────────────────┘   │  │
│  │                                                        │  │
│  │  ┌──────────┐  ┌──────────┐  ┌───────────────────┐   │  │
│  │  │ Product  │  │ Payment  │  │  STK Trigger      │   │  │
│  │  │ Catalog  │  │ Records  │  │  (Initiation)     │   │  │
│  │  └──────────┘  └──────────┘  └───────────────────┘   │  │
│  └────────────────────────────────────────────────────────┘  │
│                                                              │
├──────────────────────────────────────────────────────────────┤
│  PostgreSQL 15   │   Nginx (Reverse Proxy)  │  WhiteNoise   │
└──────────────────────────────────────────────────────────────┘
│        Safaricom M-Pesa API  ←→  VasPro SMS Gateway         │
└──────────────────────────────────────────────────────────────┘
```

### Tech Stack

| Layer | Technology |
|-------|-----------|
| **Backend** | Django 5.1.7 + Django REST Framework 3.15.2 |
| **Database** | PostgreSQL 15 (Docker) |
| **Admin UI** | Jazzmin 3.0.1 (Modern Django Admin theme) |
| **App Server** | Gunicorn + WhiteNoise |
| **Reverse Proxy** | Nginx + Kong API Gateway |
| **Payments** | M-Pesa STK Push (Safaricom Daraja API) |
| **SMS Notifications** | VasPro SMS Gateway |
| **Config Management** | python-decouple (Environment variables) |
| **Containerization** | Docker + Docker Compose |

### Healthcare Service Packages

Configurable catalog of healthcare subscription packages across multiple care categories including mental health, maternal care, chronic illness management, family care, and individual care plans — with flexible billing durations.

### Core Workflow

1. **Admin initiates payment** — Enters patient details and selects service package
2. **Auto-trigger** — System automatically initiates M-Pesa STK Push
3. **Patient receives prompt** — Payment request sent directly to patient's phone
4. **Callback processing** — Transaction result processed via webhook
5. **SMS confirmation** — Automated receipt sent on successful payment
6. **Audit trail** — Full transaction logging with status tracking

### Key Components

- **Product Catalog** — Configurable healthcare packages with pricing and duration management
- **Payment Dashboard** — Transaction monitoring with status filtering and search
- **Automated Triggers** — Signal-based payment initiation on record creation
- **Admin Interface** — Branded admin panel with audit trail and reporting

### Security & Integration

- CSRF protection with trusted origin configuration
- OAuth 2.0 authentication for payment API
- Encrypted credentials with timestamp validation
- Environment variable isolation
- Ready for downstream system integration (HIS/ERP)

---

## 8. 💬 HXA WhatsApp Ads Bot — Conversational Booking & Payments Engine

> **End-to-end WhatsApp booking automation for HealthX Africa mental health & wellness services.**  
> Go-based backend that receives Meta WhatsApp Business API messages, guides users through interactive booking flows, and processes payments via M-PESA STK Push and Airtel Money — all within the WhatsApp conversation.

### Architecture

```
┌─────────────────────────────────────────────────────────────┐
│                     WhatsApp Users                          │
│              (Click-to-WhatsApp Meta Ads)                   │
└────────────────────────┬────────────────────────────────────┘
                         │
                         ▼
┌─────────────────────────────────────────────────────────────┐
│               Gin Web Server (:8080)                        │
│                                                             │
│  ┌───────────────────────────────────────────────────────┐  │
│  │            WhatsApp Webhook Handler                   │  │
│  │   • Signature verification (HMAC-SHA256)              │  │
│  │   • Referral/ad attribution extraction                │  │
│  └───────────────────┬───────────────────────────────────┘  │
│                      │                                      │
│  ┌───────────────────▼───────────────────────────────────┐  │
│  │         Message Processor Service                     │  │
│  │   • Text & interactive button routing                 │  │
│  │   • Flow detection (mental_health / wellness)         │  │
│  │   • Conversation step management                      │  │
│  └───────────────────┬───────────────────────────────────┘  │
│                      │                                      │
│  ┌──────────┬────────┴────────┬──────────────────────────┐  │
│  │ Session  │  Template       │  Payment Services        │  │
│  │ Manager  │  Service        │  ┌────────┐ ┌─────────┐  │  │
│  │          │  (JSON-driven)  │  │ M-PESA │ │ Airtel  │  │  │
│  │          │                 │  │  STK   │ │  Money  │  │  │
│  │          │                 │  └────────┘ └─────────┘  │  │
│  └──────────┴─────────────────┴──────────────────────────┘  │
│                                                             │
│  ┌───────────────────────────────────────────────────────┐  │
│  │         Payment Callback Service                      │  │
│  │   • M-PESA & Airtel callback processing               │  │
│  │   • Session state → confirmed                         │  │
│  │   • WhatsApp confirmation delivery                    │  │
│  └───────────────────────────────────────────────────────┘  │
└────────────────────┬────────────────────────────────────────┘
                     │
   ┌─────────────────┼─────────────────┐
   │                 │                 │
   ▼                 ▼                 ▼
PostgreSQL 15    M-PESA API       Airtel Money API
(Sessions &      (Safaricom       (Collection
 Payments)        Daraja)          REST API)
```

### Tech Stack

| Layer | Technology |
|-------|------------|
| **Language** | Go 1.25 |
| **Web Framework** | Gin Gonic v1.11 |
| **Database** | PostgreSQL 15 (Docker) |
| **Migrations** | golang-migrate v4.19 |
| **Logging** | Uber Zap (structured JSON logging) |
| **API Integration** | Meta WhatsApp Business API v21.0 |
| **Payments** | M-PESA STK Push + Airtel Money Collection API |
| **Documentation** | Swagger/OpenAPI (Swaggo auto-generated) |
| **Containerization** | Docker + Docker Compose |
| **Config** | Environment variables with .env auto-loading |

### Service Architecture

| Service | Responsibility |
|---------|----------------|
| **WhatsApp Service** | Meta API communication — text, interactive buttons, images |
| **Message Processor** | Routes incoming messages, detects flow type, manages conversation steps |
| **Session Manager** | Session lifecycle — creation, resumption, expiry handling |
| **Template Service** | JSON-driven message template rendering with variable substitution |
| **Payment Services** | Dual payment provider integration with callback processing |

### Booking Flow

1. **Ad Click** — User taps Click-to-WhatsApp Meta ad → referral data captured for attribution
2. **Flow Detection** — Bot routes user to appropriate service category
3. **Package Selection** — Interactive button menus for service and plan selection
4. **Data Collection** — Conversational KYC collection
5. **Payment** — M-PESA or Airtel STK Push sent to user's phone
6. **Confirmation** — Payment callback processed → session confirmed → WhatsApp receipt sent

### Key Design Decisions

- **JSON-driven templates** — All WhatsApp messages configured in template files — no code changes needed to update copy
- **Smart session resumption** — In-progress sessions resume automatically; completed sessions trigger new booking
- **Dual payment provider** — M-PESA and Airtel Money with unified callback processing
- **Ad attribution tracking** — Full referral capture from Meta ads for campaign ROI analysis
- **Environment-aware pricing** — Non-production environments auto-override for safe testing
- **Clean architecture** — Handlers → Services → Repository → Database

---

## 9. 🏢 Admark Enterprises — Corporate Branding & Promotional Products Website

> **Production corporate website for Admark Enterprises Limited — a promotional products and branding solutions company in Nairobi, Kenya.**  
> Product catalog with category browsing, customer enquiry system, career portal, and partner/client showcase.

### Architecture: PHP Server-Side Rendered Website

```
┌──────────────────────────────────────────────────────────┐
│              APACHE / CPANEL HOSTING                      │
│            (SSL · .htaccess · PHP 7+)                    │
├──────────────────────────────────────────────────────────┤
│                                                          │
│  ┌──────────────┐  ┌──────────────┐  ┌──────────────┐   │
│  │   Product    │  │   Customer   │  │   Career     │   │
│  │   Catalog    │  │   Enquiry    │  │   Portal     │   │
│  │  (Browse &   │  │   System     │  │  (Job List)  │   │
│  │   Search)    │  │  (Email)     │  │              │   │
│  └──────────────┘  └──────────────┘  └──────────────┘   │
│                                                          │
│  ┌──────────────┐  ┌──────────────┐  ┌──────────────┐   │
│  │   Contact    │  │   Partner    │  │   PDF        │   │
│  │   & Maps     │  │   Showcase   │  │   Catalog    │   │
│  │  (Google)    │  │  (Carousel)  │  │   Download   │   │
│  └──────────────┘  └──────────────┘  └──────────────┘   │
│                                                          │
├──────────────────────────────────────────────────────────┤
│        MySQL / MariaDB      │     PHP mail()            │
└──────────────────────────────────────────────────────────┘
```

### Tech Stack

| Layer | Technology |
|-------|------------|
| **Backend** | PHP 7+ (Server-side rendered) |
| **Database** | MySQL / MariaDB |
| **Frontend** | HTML5 + CSS3 + Bootstrap + jQuery |
| **Icons** | Font Awesome |
| **Email** | PHP `mail()` with input sanitization |
| **Carousel** | Owl Carousel + jCarousel |
| **Maps** | Google Maps Embed |
| **Server** | Apache (cPanel hosting) |

### Features

| Module | Description |
|--------|-------------|
| **Homepage** | Hero carousel, top-selling products, category grid, company overview |
| **Product Catalog** | Browse by category with search, product detail pages with enquiry forms |
| **Customer Enquiry** | Quote request form — sends product details + customer info via email to sales team |
| **PDF Catalog** | Downloadable full product catalog (PDF) |
| **Career Portal** | Job listings with detailed position descriptions and application instructions |
| **About Us** | Company vision, mission, and core values |
| **Partners** | Carousel showcasing partner company logos |
| **Our Clients** | Ministry of Health, KENHA, and other notable client logos |
| **Contact Us** | Contact form, office location, embedded Google Maps |

### Product Categories

Computers & Accessories · Auto Items · Bags · Caps & Hats · Clothing · Flash Drives · Keyrings · Mugs · Office Supplies · Pens · Phones & Accessories · Stationery · Technology · Watches & Clocks

### Security Measures

- Prepared statements for database queries
- Input sanitization and validation
- Email validation before form submission
- Environment-based database credentials
- Error logging (not exposed to users)

### Deployment

- **Hosting:** cPanel shared hosting (Apache)
- **Domain:** admark.co.ke
- **Database:** MySQL via cPanel
- **Email:** PHP native mail with server SMTP

---

## 🧰 Skills & Technology Summary

### Languages
![TypeScript](https://img.shields.io/badge/TypeScript-007ACC?style=flat-square&logo=typescript&logoColor=white)
![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=flat-square&logo=javascript&logoColor=black)
![Python](https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=python&logoColor=white)
![PHP](https://img.shields.io/badge/PHP-777BB4?style=flat-square&logo=php&logoColor=white)
![Java](https://img.shields.io/badge/Java-ED8B00?style=flat-square&logo=openjdk&logoColor=white)
![Go](https://img.shields.io/badge/Go-00ADD8?style=flat-square&logo=go&logoColor=white)
![SQL](https://img.shields.io/badge/SQL-4479A1?style=flat-square&logo=postgresql&logoColor=white)

### Frontend
![React](https://img.shields.io/badge/React-20232A?style=flat-square&logo=react&logoColor=61DAFB)
![Next.js](https://img.shields.io/badge/Next.js-black?style=flat-square&logo=next.js&logoColor=white)
![Vite](https://img.shields.io/badge/Vite-646CFF?style=flat-square&logo=vite&logoColor=white)
![Tailwind](https://img.shields.io/badge/Tailwind_CSS-38B2AC?style=flat-square&logo=tailwind-css&logoColor=white)
![Ant Design](https://img.shields.io/badge/Ant_Design-0170FE?style=flat-square&logo=ant-design&logoColor=white)

### Backend
![Node.js](https://img.shields.io/badge/Node.js-339933?style=flat-square&logo=node.js&logoColor=white)
![Express](https://img.shields.io/badge/Express-000000?style=flat-square&logo=express&logoColor=white)
![NestJS](https://img.shields.io/badge/NestJS-E0234E?style=flat-square&logo=nestjs&logoColor=white)
![FastAPI](https://img.shields.io/badge/FastAPI-009688?style=flat-square&logo=fastapi&logoColor=white)
![Gin](https://img.shields.io/badge/Gin-00ADD8?style=flat-square&logo=go&logoColor=white)
![Django](https://img.shields.io/badge/Django-092E20?style=flat-square&logo=django&logoColor=white)

### Databases & ORM
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-316192?style=flat-square&logo=postgresql&logoColor=white)
![MySQL](https://img.shields.io/badge/MySQL-4479A1?style=flat-square&logo=mysql&logoColor=white)
![Redis](https://img.shields.io/badge/Redis-DC382D?style=flat-square&logo=redis&logoColor=white)
![MariaDB](https://img.shields.io/badge/MariaDB-003545?style=flat-square&logo=mariadb&logoColor=white)
![Prisma](https://img.shields.io/badge/Prisma-2D3748?style=flat-square&logo=prisma&logoColor=white)
![SQLAlchemy](https://img.shields.io/badge/SQLAlchemy-D71F00?style=flat-square&logo=python&logoColor=white)

### AI/ML
![OpenAI](https://img.shields.io/badge/OpenAI-412991?style=flat-square&logo=openai&logoColor=white)
![scikit-learn](https://img.shields.io/badge/scikit--learn-F7931E?style=flat-square&logo=scikit-learn&logoColor=white)
![pandas](https://img.shields.io/badge/pandas-150458?style=flat-square&logo=pandas&logoColor=white)
![NumPy](https://img.shields.io/badge/NumPy-013243?style=flat-square&logo=numpy&logoColor=white)

### DevOps & Infrastructure
![Docker](https://img.shields.io/badge/Docker-2496ED?style=flat-square&logo=docker&logoColor=white)
![Nginx](https://img.shields.io/badge/Nginx-009639?style=flat-square&logo=nginx&logoColor=white)
![GitHub Actions](https://img.shields.io/badge/GitHub_Actions-2088FF?style=flat-square&logo=github-actions&logoColor=white)
![Prometheus](https://img.shields.io/badge/Prometheus-E6522C?style=flat-square&logo=prometheus&logoColor=white)
![Grafana](https://img.shields.io/badge/Grafana-F46800?style=flat-square&logo=grafana&logoColor=white)

### Payments
![Stripe](https://img.shields.io/badge/Stripe-008CDD?style=flat-square&logo=stripe&logoColor=white)
![M-Pesa](https://img.shields.io/badge/M--Pesa-4CAF50?style=flat-square&logo=money&logoColor=white)
![Airtel Money](https://img.shields.io/badge/Airtel_Money-ED1C24?style=flat-square&logo=airtel&logoColor=white)
![PesaPal](https://img.shields.io/badge/PesaPal-00457C?style=flat-square&logo=paypal&logoColor=white)

---

## 📬 Contact

- **GitHub:** [github.com/mykendoch](https://github.com/mykendoch)
- **LinkedIn:** [linkedin.com/in/mykendoch](https://www.linkedin.com/in/mykendoch)

---

<p align="center">
  <em>All repositories are private. This portfolio documents the scope, architecture, and capabilities of each project.<br/>
  For code review access or live demos, please reach out directly.</em>
</p>

<p align="center"><strong>"Code is private. Impact is public."</strong></p>
