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
9. [Skills & Technology Summary](#-skills--technology-summary)

---

## 1. 🐄 AgriFarm AI — AI-Powered Dairy Farm Management Platform

> **Smart herd management SaaS built specifically for African dairy farmers.**  
> Subscription-based platform with AI-powered disease diagnosis, milk anomaly detection, and M-Pesa mobile payments.

### Architecture: 12 Microservices

```
┌──────────────────────────────────────────────────────────┐
│                    NGINX API GATEWAY                      │
│              (SSL · Rate Limiting · Routing)               │
├──────────────────────────────────────────────────────────┤
│                                                            │
│  ┌─────────┐ ┌─────────┐ ┌──────────┐ ┌──────────────┐   │
│  │  Auth    │ │  Cow    │ │  Health  │ │ Reproduction │   │
│  │ Service  │ │ Service │ │ Service  │ │   Service    │   │
│  │ :3001   │ │ :3002   │ │ :3003   │ │   :3005     │   │
│  └─────────┘ └─────────┘ └──────────┘ └──────────────┘   │
│                                                            │
│  ┌─────────┐ ┌─────────┐ ┌──────────┐ ┌──────────────┐   │
│  │  Milk   │ │ Notif.  │ │   AI     │ │   Payment    │   │
│  │ Service │ │ Service │ │ Service  │ │   Service    │   │
│  │ :3004   │ │ :3006   │ │ :3007   │ │   :3008     │   │
│  └─────────┘ └─────────┘ └──────────┘ └──────────────┘   │
│                                                            │
│  ┌─────────┐ ┌─────────┐ ┌──────────────────────────┐    │
│  │ Report  │ │ Media   │ │      React Frontend      │    │
│  │ Service │ │ Service │ │         :3000            │    │
│  │ :3009   │ │ :3010   │ │                          │    │
│  └─────────┘ └─────────┘ └──────────────────────────┘    │
│                                                            │
├──────────────────────────────────────────────────────────┤
│  PostgreSQL 16  │  Redis 7 (Cache/Queue)  │  MinIO (S3)  │
└──────────────────────────────────────────────────────────┘
│           OpenTelemetry → Prometheus → Grafana + Loki     │
└──────────────────────────────────────────────────────────┘
```

### Tech Stack

| Layer | Technology |
|-------|-----------|
| **Frontend** | React 18 + TypeScript + Vite |
| **Backend** | Node.js 20 + Express (12 microservices) |
| **Database** | PostgreSQL 16 + Redis 7 |
| **ORM** | Prisma |
| **API Gateway** | Nginx (SSL termination, rate limiting) |
| **File Storage** | MinIO (S3-compatible object storage) |
| **Monitoring** | OpenTelemetry + Prometheus + Grafana + Loki |
| **Payments** | Stripe + M-Pesa (Safaricom Daraja API) |
| **SMS/Notifications** | Africa's Talking API |
| **AI Models** | OpenAI GPT-4o + Anthropic Claude |
| **Queue** | BullMQ (Redis-backed job queue) |
| **Containerization** | Docker + Docker Compose |
| **CI/CD** | GitHub Actions |

### Microservices Breakdown

| Service | Port | Responsibilities |
|---------|------|-----------------|
| **auth-service** | 3001 | JWT authentication, user management, subscription enforcement, account lockout |
| **cow-service** | 3002 | Cow profiles, genealogy tree tracking, lifecycle management |
| **health-service** | 3003 | Disease records, vaccinations, deworming schedules, dry cow tracking |
| **milk-service** | 3004 | Milk recording, production analytics, AI-powered anomaly detection |
| **reproduction-service** | 3005 | Heat cycle tracking, insemination records, pregnancy monitoring, calving management |
| **notification-service** | 3006 | Email + SMS notifications via Africa's Talking API |
| **ai-service** | 3007 | Claude/OpenAI chatbot, health predictions, image/video analysis |
| **payment-service** | 3008 | Stripe + M-Pesa integration, subscription billing |
| **report-service** | 3009 | PDF + Excel report generation (Puppeteer/PDFKit) |
| **media-service** | 3010 | Image/video uploads, processing (Sharp), MinIO storage |

### Key Features

- **AI-Powered Disease Advisor** — Chat with an AI veterinarian; upload photos/videos of sick cows for diagnosis
- **Milk Anomaly Detection** — ML-based detection of unusual milk production patterns
- **Heat Cycle Prediction** — AI predicts optimal insemination timing
- **Herd Health Score** — Automated scoring of overall herd wellness
- **Genealogy Tracking** — Full lineage tracking (dam, sire, maternal grandmothers)
- **M-Pesa Mobile Payments** — Kenya's most popular payment method, integrated natively
- **Multi-Role Access Control** — FARMER, FARM_MANAGER, FARM_WORKER, ADMIN roles
- **Real-Time SMS Alerts** — Vaccination reminders, calving alerts, health warnings
- **Comprehensive Reporting** — PDF and Excel reports for milk production, financials, herd health
- **Super Admin Portal** — SaaS management dashboard for platform administration

### Subscription Tiers (SaaS Model)

| Tier | Price (KES/mo) | Cows | AI Chats | History |
|------|----------------|------|----------|---------|
| Free | 0 | 10 | 3/month | 7 days |
| Basic | 1,500 | 50 | 20/month | 90 days |
| Professional | 4,500 | 300 | Unlimited | Unlimited |
| Enterprise | 12,000 | Unlimited | Unlimited | Unlimited + API |

### Frontend (26 Pages)

Dashboard · Cow Profiles · Health Records · Reproduction Tracking · Milk Recording · Analytics (Sales, Revenue, Profit/Loss) · AI Advisor · Payment & Subscription · Reports · Super Admin Portal · User Management · Settings

### Observability Stack

Full production-grade monitoring with OpenTelemetry instrumentation across all 12 services, Prometheus metrics collection, Grafana dashboards, and Loki log aggregation.

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
        │     └── All clinical/financial data (branch-scoped)
        ├── Branch B (Satellite Clinic)
        │     ├── Users
        │     └── Data (fully isolated)
        └── License (MONTHLY/QUARTERLY/ANNUAL/LIFETIME)
```

- **Branch-scoped data isolation** — Every table has a `branchId` foreign key
- **Branch-aware authentication** — Login flow: Select Org → Select Branch → Enter Credentials
- **JWT payload** includes `organizationId` + `branchId` for automatic scoping

### SaaS Licensing Engine

- License formats: `HMIS-XXXX-XXXX-XXXX-XXXX`
- Duration types: MONTHLY / QUARTERLY / ANNUAL / LIFETIME
- Status lifecycle: `ACTIVE → GRACE_PERIOD → EXPIRED / SUSPENDED`
- **LicenseGuard** — Global NestJS guard blocks all requests when license is expired
- Phone-home validation (hourly cron) with 5-minute Redis cache
- Automated expiry reminders: 30 / 15 / 7 / 3 / 1 days before expiry
- Full audit trail for all license events

### Phase 1 Features (Complete)

| Module | Features |
|--------|----------|
| **Infrastructure** | Docker Compose orchestration, OpenTelemetry + Winston logging, Nginx reverse proxy, health checks (K8s-ready), global exception filters, request ID middleware |
| **Multi-Tenancy** | Organization + Branch hierarchy, branch-scoped data isolation, branch-aware login, per-branch username uniqueness |
| **Licensing** | License CRUD, key generation, status lifecycle, LicenseGuard, grace periods, phone-home, expiry reminders, audit trail |
| **Super Admin** | Organization provisioning (one-click), branch management, license issuance/renewal/suspension, dashboard + audit log |
| **Authentication** | Branch-aware JWT (access + refresh tokens), BCrypt password hashing, 2FA via TOTP, account lockout (5 attempts / 30 min) |
| **RBAC** | Page-name-based rights system (SystemPage model), admin-only user CRUD, branch-scoped user management |

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

- **Live at:** Komarock Modern Healthcare, Nairobi, Kenya
- **Users:** Doctors, nurses, pharmacists, lab technicians, billing clerks, administrators
- **Contact:** P.O Box 23728-00100 Nairobi | Tel: 0730 96 30 00

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

#### Hybrid Earnings Predictor (2-Layer Model)

**Layer 1 — Deterministic Multiplier Model:**
- UK-calibrated base rates by location (£12–£28/hr across 14 location categories)
- Time-of-day multipliers (24-hour curve, peak 20:00–21:00 at 2.3×)
- Day-of-week multipliers (Saturday highest at 1.35×)
- Real-time demand scaling (0.8× – 1.5×)

**Layer 2 — RandomForestRegressor (when historical data exists):**
- Hyperparameters: `n_estimators=100, max_depth=8, random_state=42`
- Features: hour, day_of_week, location, demand_level
- Validation: 5-fold cross-validation with R² scoring
- Outputs: Feature importance analysis for interpretability

#### Demand Forecaster
- Location-typed demand curves (downtown, airport, residential, etc.)
- Trend analysis via `scipy.stats.linregress`
- Peak hour identification with `numpy.argmax`
- Statistical summary: mean, std, skewness, kurtosis

#### Shift Optimizer
- Evaluates all 24 start hours × 14 locations in vectorized NumPy pass
- Ranks shift windows by predicted total earnings
- Generates personalized multi-location recommendations

#### Accuracy Analyzer
- Metrics: MAE, MAPE, RMSE, R²
- Thresholds: Excellent (MAPE ≤10%) · Good (≤15%) · Acceptable (≤20%) · Poor (>20%)

### Income Guarantee Engine

```
Guarantee Threshold: 90% of predicted earnings
Top-Up Formula: max(0, predicted × 0.9 − actual)
Eligibility: Minimum shift hours + compliance checks
Activation: Automatic when driver meets threshold
```

- Tracks: Guarantee log, activation rates, total disbursements
- Sustainability metrics: Cost-benefit analysis, break-even calculations, scenario planning

### Database Schema (8 Tables)

| Table | Purpose |
|-------|---------|
| `users` | Admin + driver accounts with role-based access |
| `shifts` | Shift records with earnings, predictions, status |
| `shift_details` | Location, type, duration, hourly rate per shift |
| `surveys` | Worker feedback (Likert 1–5 scale + open text) |
| `survey_questions` | Fixed question templates (earnings, safety, schedule) |
| `eligibility_metrics` | Calculated guarantee eligibility scores per driver |
| `worker_daily_summary` | Aggregated daily earnings and statistics |
| `ml_predictions` | Generated predictions and model outputs |

### Driver Dashboard (9 Tabs)

1. **Earnings Prediction** — AI predicts hourly earnings by time/location
2. **Shift Recommendations** — Personalized optimal shifts ranked by potential earnings
3. **Income Guarantee** — 90% earnings guarantee with automatic top-up calculation
4. **Guarantee Eligibility** — Track qualification status (hours + compliance metrics)
5. **Volatility Analysis** — Statistical comparison: stability with vs. without guarantee
6. **Performance Tracking** — Earnings trends, top locations, efficiency metrics
7. **Earnings Analytics** — Actual vs. predicted detailed comparison charts
8. **Survey Feedback** — Submit Likert-scale research surveys
9. **Activity Log** — Personal action history and audit trail

### Admin Dashboard (9 Tabs)

1. **System Analytics** — Total drivers, shifts, earnings, guarantee activations
2. **Model Accuracy** — Prediction accuracy metrics vs. target thresholds
3. **Driver Management** — CRUD, suspend/reactivate, bulk-import, password reset
4. **Admin Management** — Admin account creation with full audit trail
5. **Guarantee Overview** — Aggregate stats, activation rates, total disbursements
6. **Shifts Overview** — Platform-wide shift breakdown by status
7. **Survey Reports** — Aggregated feedback with anonymized export capability
8. **Sustainability Dashboard** — Cost-benefit analysis, break-even, scenario planning
9. **Activity Log** — Complete audit trail of all admin actions

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
- STK Push — prompt payment directly from customer's phone
- Transaction logging with retry logic (max 3 retries)
- Callback handling with order status auto-update
- Payment audit trail & reconciliation

**PesaPal (Multi-Channel Gateway):**
- API v3 with OAuth token management
- IPN (Instant Payment Notification) webhooks
- Transaction verification & status queries
- Support for cards, mobile money, and bank transfers

### Logistics & Delivery

| Feature | Details |
|---------|---------|
| **Delivery Zones** | Nairobi same-day express + nationwide 24-48hr standard + HQ pickup |
| **Dynamic Pricing** | Per-zone delivery fees with express premiums |
| **Fargo Courier** | API integration for shipment creation and real-time tracking |
| **Fulfillment Pipeline** | 7-stage lifecycle with timestamps and TAT calculation |
| **Address Management** | Multiple saved addresses per user with zone association |

### Security

- CSRF token validation on all forms
- Prepared statements (MySQLi) — SQL injection prevention
- Account lockout after 5 failed attempts (15-minute cooldown)
- Login history and suspicious activity monitoring
- Password hashing with PHP `PASSWORD_DEFAULT`
- SSL/TLS enforcement

### Database Schema (21+ Tables)

Users · Products · Categories · Orders · Order Items · Cart · Wishlist · Prescriptions · File Uploads · Delivery Zones · M-Pesa Transactions · M-Pesa Callbacks · Payment Audit Log · Payment Analytics · Payment Reconciliation · OTP Requests · Login History · Security Audit Log · Pharmacy Settings · Pharmacy License

---

## 6. 📱 HealthX USSD — Telemedicine & Micro-Insurance USSD Platform

> **Production USSD microservice enabling healthcare access on any phone — including feature phones.**  
> Customers dial `*384*8888#` to purchase telemedicine consultations, micro-insurance, wellness subscriptions, and health content — all paid via M-Pesa. Built for a telehealth company in Nairobi, Kenya.

### Architecture: USSD Microservice Platform

```
┌──────────────────────────────────────────────────────────────┐
│                    Africa's Talking USSD                       │
│                   POST /api/v1/ussd/callback                  │
├──────────────────────────────────────────────────────────────┤
│                                                                │
│  ┌────────────┐   ┌──────────────┐   ┌────────────────────┐  │
│  │   Express   │   │  Controller  │   │   USSD Service     │  │
│  │  Middleware │──►│  (Routing)   │──►│  (Flow Engine)     │  │
│  │  Helmet     │   │              │   │  1500+ lines       │  │
│  │  CORS       │   └──────────────┘   └────────┬───────────┘  │
│  │  Morgan     │                               │               │
│  └────────────┘                               ▼               │
│                                                                │
│  ┌────────────┐   ┌──────────────┐   ┌────────────────────┐  │
│  │  MenuBuilder│   │ CacheManager │   │  Payment Service   │  │
│  │ (Dynamic   │◄──│ (5-min TTL)  │   │  (M-Pesa STK)     │  │
│  │  Menus)    │   │ Plans/Prices │   └────────┬───────────┘  │
│  └────────────┘   └──────────────┘            │               │
│                                               ▼               │
│  ┌────────────┐   ┌──────────────┐   ┌────────────────────┐  │
│  │   Britam   │   │  HealthX     │   │  Notification      │  │
│  │  Insurance │   │  Boda/       │   │  SMS + WhatsApp    │  │
│  │   API      │   │  Mwananchi   │   │  + Email           │  │
│  └────────────┘   └──────────────┘   └────────────────────┘  │
│                                                                │
├──────────────────────────────────────────────────────────────┤
│  MariaDB/MySQL (Connection Pool)  │  Node-Cache (Sessions)   │
└──────────────────────────────────────────────────────────────┘
│       OpenTelemetry + Sentry + New Relic + DataDog            │
└──────────────────────────────────────────────────────────────┘
```

### Tech Stack

| Layer | Technology |
|-------|------------|
| **Runtime** | Node.js + Express v5.1 |
| **Database** | MariaDB/MySQL (mysql2/promise, 10–100 connection pool) |
| **Caching** | node-cache (15-min TTL for sessions, 5-min for menus) |
| **Logging** | Winston (daily rotation) + Pino (multi-transport) |
| **APM** | OpenTelemetry (OTLP → Jaeger/Grafana Tempo) |
| **Error Tracking** | Sentry |
| **Monitoring** | New Relic + DataDog StatsD |
| **Security** | Helmet (security headers) + CORS |
| **Payments** | Safaricom M-Pesa (Daraja API — STK Push) |
| **Insurance** | Britam REST API (token + subscription key auth) |
| **SMS** | VasPro SMS Gateway |
| **WhatsApp** | Meta WhatsApp Cloud API v22.0 |
| **Email** | Nodemailer |
| **Scheduling** | node-cron |
| **Process Manager** | PM2 |

### USSD Menu Structure (7 Services)

```
*384*8888#
├── 1: Doctor Consultation (one-time, monthly, quarterly, yearly)
├── 2: Psychology Services (individual, couple, family, life coaching)
├── 3: Nutrition Consultation
├── 4: HealthX Boda Insurance (BodaBoda riders — accident/injury)
│   └── Plans: Hustler (Basic) · Champee (Standard) · Bazu (Premium)
│   └── Benefits: Accidental death, hospitalization cash, ambulance
│   └── Flows: Buy → KYC → M-Pesa → Policy | Renew | Claim | Opt-out
├── 5: HealthX Mwananchi Insurance (General public — funeral/health)
│   └── Final expense: KES 25K–500K | Hospitalization: KES 500–2,500/day
├── 6: Afya Daily (SMS-based curated health tips subscription)
└── 7: Settings (Profile, Next of Kin, Policy History)
```

### Key Integrations

| Integration | Details |
|-------------|----------|
| **M-Pesa STK Push** | Payment prompt → callback → automatic policy creation. Transaction logging with retry (max 3). Account refs: `BODABASIC`, `MWANANCHISTANDARD`, etc. |
| **Britam Insurance** | REST API for underwriting. Products: Morio (Boda), Mwananchi (Family). Token + subscription key auth. Fallback to local policy on API failure. |
| **HealthX Boda API** | Rider registration → policy number + coverage dates. Header-based auth (client_id/secret). Policy cancellation for opt-outs. |
| **HealthX Mwananchi API** | Family insurance registration. Britam-backed funeral expense + hospitalization coverage. |
| **VasPro SMS** | Direct SMS delivery for notifications, claim instructions, renewal reminders. DB-cached templates with variable substitution. |
| **WhatsApp Cloud API** | Meta Graph API v22.0 for Business template messages. Dual-channel with SMS for critical notifications. |
| **Email (Nodemailer)** | Purchase confirmations, claim receipts. Async (non-blocking to USSD response). |

### Payment & Policy Flow

```
User selects insurance plan
  → KYC collection (Name → ID → DOB → Gender)
  → Confirmation screen with plan details
  → M-Pesa STK Push sent to phone
  → User completes payment on M-Pesa
  → Callback received at /api/v1/ussd/mpesa/callback
  → Policy created via Britam/HealthX API
  → SMS + Email + WhatsApp confirmation
  → Policy stored in DB with coverage dates
```

### KYC & Session Management

- Multi-step validation: Full Name → ID (6–9 digits) → DOB (DDMMYYYY) → Gender
- Existing KYC cached to skip re-entry for returning users
- Session tracking with 15-min expiry (database-backed, survives app restart)
- Menu code parsing (0 = back, 00 = main menu) with state preservation
- Full audit logging of all USSD interactions

### Database Schema (8 USSD Tables)

| Table | Purpose |
|-------|----------|
| `customer_kyc` | User KYC data (name, ID, DOB, gender, verification) |
| `customer_nok` | Next of Kin information |
| `ussd_session_progress` | Active session state tracking |
| `customer_policies` | Policies created from M-Pesa callbacks |
| `pending_purchases` | Intermediate records awaiting payment |
| `ussd_transactions` | M-Pesa transaction logs |
| `ussd_logs` | Audit trail of all interactions |
| `sms_templates` | Templated SMS messages (cached at startup) |

### Monitoring & Observability

- **OpenTelemetry** — Distributed tracing across all operations
- **Sentry** — Error tracking with full context
- **New Relic** — Application performance monitoring
- **DataDog** — StatsD metrics (ussd.requests.total, ussd.request.duration)
- **Winston** — Daily-rotated file logging + separate error logs
- **Pino** — Structured JSON logging (multi-transport)

### Automated Background Jobs

| Job | Purpose |
|-----|----------|
| **Session Expiry Cron** | Expires inactive USSD sessions |
| **Policy Reminder Cron** | Sends renewal reminders x days before expiry |
| **Policy Recovery Cron** | Retries failed Britam API calls / policy creations |
| **Insurance Reminders** | Product-specific renewal campaigns |

### Notable Technical Features

- **Dynamic Menu Builder** — USSD menus generated from DB-cached service/plan/pricing data (5-min refresh)
- **Policy Retry Engine** — Automatic retry for failed API calls with date preservation across retries
- **Dual-Channel Notifications** — SMS + WhatsApp for critical messages (claim instructions, confirmations)
- **Connection Pooling** — 10–100 MariaDB connections with health monitoring
- **Template Variables** — `{policy_number}`, `{coverage_end}`, `{phone}` in DB-stored templates
- **Admin Endpoints** — Cache clear/refresh, manual reminder triggers, policy recovery

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

| Package | Duration | Price (KSH) |
|---------|----------|-------------|
| Mental Health Services | 12 / 3 / 1 months | 8,995 / 2,995 / 1,995 |
| Maternal Care (Nurture Mama) | 12 months | 9,000 |
| Chronic Illness Management | 12–13 months | 16,000 |
| Family Care Plans | 12 / 3 / 1 months | 8,995 / 3,595 / 1,395 |
| Individual Care Plans | 12 / 3 / 1 months | 2,995 / 995 / 795 |

### Core Workflow

1. **Admin creates STK Trigger** — Enters patient phone, MRN, product, and amount
2. **Signal auto-fires** — Django `post_save` signal initiates M-Pesa STK Push
3. **OAuth + STK Push** — Fetches access token, generates encrypted password, calls Safaricom API
4. **Patient receives prompt** — Silent push to patient's phone for payment confirmation
5. **Callback processing** — M-Pesa posts transaction result to webhook endpoint
6. **SMS confirmation** — On success, sends payment receipt via VasPro SMS API
7. **Audit trail** — Full transaction logging with status tracking (Pending → Completed/Failed)

### Data Models

| Model | Purpose |
|-------|---------|
| **Product** | Healthcare service catalog (name, price, duration, department) |
| **MpesaPayment** | Transaction records (receipt, status, amounts, timestamps) |
| **StkTrigger** | Payment initiation records (phone, MRN, product, served_by) |

### Admin Dashboard Features

- **Product Management** — Configure healthcare packages with pricing and duration
- **Payment Dashboard** — Track all M-Pesa transactions with status filtering (Pending/Completed/Failed)
- **Search & Filter** — By phone number, receipt ID, request ID, date range
- **Audit Trail** — Auto-tracks which admin initiated each payment request
- **Custom Jazzmin Theme** — Branded orange accent color scheme with HealthX branding

### API Endpoints

| Endpoint | Method | Purpose |
|----------|--------|---------|
| `/stk-push/` | POST | Create STK Trigger (admin-initiated) |
| `/callback/` | POST | M-Pesa callback webhook receiver |
| `/test-token/` | GET | Verify M-Pesa access token (debug) |

### Security & Integration

- **CSRF protection** with trusted origins for `pay.healthxafrica.com`
- **OAuth 2.0** authentication for Safaricom API
- **Base64 encrypted passwords** with timestamp validation
- **Environment variable isolation** via python-decouple
- **External API integration ready** — Stub for forwarding to HIS/ERP systems

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

### Service Architecture (6 Services)

| Service | Responsibility |
|---------|----------------|
| **WhatsApp Service** | Meta API communication — text, interactive buttons, images |
| **Message Processor** | Routes text & button responses, detects flow type, manages conversation steps |
| **Session Manager** | Creates/resumes sessions, 1-hour expiry, auto-new after completed bookings |
| **Template Service** | Loads & renders WhatsApp message templates from JSON with variable substitution |
| **M-PESA Service** | OAuth token caching (55 min), STK Push initiation, 1 KES test mode |
| **Airtel Service** | OAuth + RSA-SHA256 message signing, STK Push, validation/process/enquiry callbacks |
| **Payment Callback Service** | Processes payment results, updates sessions, sends WhatsApp confirmations |

### Booking Flow

1. **Ad Click** — User taps Click-to-WhatsApp Meta ad → referral data captured (source, headline, media)
2. **Flow Detection** — Bot detects "wellness" keyword → routes to wellness flow; otherwise mental health
3. **Package Selection** — Interactive button menu:
   - Mental Health: Single Session (KES 1,250) or 4-Session Bundle (KES 3,750)
   - Wellness: JITUNZE / USTAWI / IMARIKA / BORESHA / SHUJAA / JIPENDE (KES 2,195–12,495)
4. **Data Collection** — Bot collects full name and ID number via conversation
5. **Payment** — User taps "Pay Now" → M-PESA or Airtel STK Push sent to phone
6. **Confirmation** — Callback received → session marked confirmed → WhatsApp receipt sent

### Data Models

| Model | Key Fields |
|-------|------------|
| **SessionBooking** | user_phone, flow_category (mental_health/mental_wellness), current_step, package_type, full_name, id_number, referral tracking (source_type, source_id, headline, media URLs), session_details (JSONB) |
| **Payment** | user_phone, session_id (FK), checkout_request_id (UNIQUE), amount, mpesa_receipt_number, status (pending/completed/failed/cancelled), metadata (JSONB) |

### API Endpoints

| Method | Endpoint | Purpose |
|--------|----------|----------|
| GET | `/whatsapp/webhook` | Meta webhook verification (challenge-response) |
| POST | `/whatsapp/webhook` | Receive incoming messages, button clicks & status updates |
| POST | `/mpesa/callback` | M-PESA STK Push payment confirmation |
| POST | `/payments/validate` | Airtel pre-transaction validation |
| POST | `/payments/process` | Airtel post-PIN transaction processing |
| POST | `/payments/enquiry` | Airtel transaction status enquiry |
| POST | `/airtel/initiate` | Initiate Airtel STK Push |
| GET | `/health` | Health check |
| GET | `/swagger/*` | Auto-generated API documentation |

### Key Design Decisions

- **JSON-driven templates** — All WhatsApp messages (text, buttons, images, footers) configured in `whatsapp_templates.json` — no code changes needed to update copy
- **Smart session resumption** — In-progress sessions resume automatically; completed sessions trigger new booking; sessions expire after 1 hour of inactivity
- **Dual payment provider** — M-PESA and Airtel Money with unified callback processing
- **Ad attribution tracking** — Full referral capture from Meta ads (source type, headline, body, media) stored per session for campaign ROI analysis
- **Environment-aware pricing** — Non-production environments auto-override to KES 1 for safe testing
- **Repository pattern** — Clean separation: Handlers → Services → Repository → PostgreSQL

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
