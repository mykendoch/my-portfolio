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
6. [Skills & Technology Summary](#-skills--technology-summary)

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

## 🧰 Skills & Technology Summary

### Languages
![TypeScript](https://img.shields.io/badge/TypeScript-007ACC?style=flat-square&logo=typescript&logoColor=white)
![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=flat-square&logo=javascript&logoColor=black)
![Python](https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=python&logoColor=white)
![PHP](https://img.shields.io/badge/PHP-777BB4?style=flat-square&logo=php&logoColor=white)
![Java](https://img.shields.io/badge/Java-ED8B00?style=flat-square&logo=openjdk&logoColor=white)
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
