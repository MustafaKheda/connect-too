# Connect Too - Service Marketplace Platform

> A subscription-based marketplace platform connecting service providers with customers. Employees list services, users discover and book them - with **ZERO commission on bookings**.

[![Repository Size](https://img.shields.io/github/repo-size/MustafaKheda/connect-too?style=flat-square)](https://github.com/MustafaKheda/connect-too)
[![License](https://img.shields.io/badge/license-MIT-blue.svg?style=flat-square)](LICENSE)
[![Status](https://img.shields.io/badge/status-Planning-yellow.svg?style=flat-square)](README.md)

---

## 📋 Table of Contents

- [Overview](#overview)
- [Business Model](#business-model)
- [Platform Components](#platform-components)
- [Tech Stack](#tech-stack)
- [Getting Started](#getting-started)
- [Project Structure](#project-structure)
- [Key Features](#key-features)
- [Development Phases](#development-phases)
- [Contributing](#contributing)

---

## Overview

**Connect Too** is a next-generation service marketplace that empowers service professionals to grow their business without commission fees. The platform monetizes through employee subscriptions, creating a win-win ecosystem.

### Key Differentiators
✅ **Zero Commission on Bookings** - Service providers keep 100% of earnings  
✅ **Transparent Pricing** - No hidden fees or surprise charges  
✅ **Quality-First** - Rigorous vetting and verification processes  
✅ **Provider-Centric** - Tools designed to help providers succeed  
✅ **Global Scalability** - Built for multi-region, multi-currency operations

---

## Business Model

### Revenue Streams
1. **Employee Subscriptions** (Primary)
   - Starter: $9.99/month - Basic profile, 1 service
   - Professional: $24.99/month - Featured profile, 5 services, advanced analytics
   - Premium: $49.99/month - Premium placement, unlimited services, priority support

2. **Future Revenue** (Post-MVP)
   - Booking insurance/protection plans
   - Advanced analytics and tools
   - Promotional boosts
   - API access for integrations

### Market Positioning
Combines the best practices of:
- **Urban Company** - Service marketplace with quality focus
- **Uber/Rapido** - Efficient matching and supply/demand management
- **Upwork** - Freelancer empowerment and verification
- **Blinkit/Zepto** - Fast operations and on-demand efficiency

---

## Platform Components

### 1. Employee Portal (Mobile App)
Service providers list their offerings, manage availability, accept bookings, and track earnings.

**Key Modules:**
- Authentication & KYC verification
- Profile & service management
- Availability scheduling
- Real-time booking management
- Earnings dashboard & payouts
- Ratings & reviews
- Advanced analytics
- Subscription management

### 2. User Portal (Mobile App)
Customers discover service providers, compare options, book services, and leave reviews.

**Key Modules:**
- Discovery & search
- Provider browsing & filtering
- Detailed booking flow
- Payment integration
- Real-time tracking
- Chat with providers
- Ratings & reviews
- Safety & trust features

### 3. Admin Dashboard (Web)
Manage platform, users, subscriptions, disputes, and analytics.

**Key Modules:**
- User & employee management
- Subscription management
- Dispute resolution
- Financial dashboard
- Analytics & reporting
- Content management
- Support ticketing
- Compliance & GDPR

---

## Tech Stack

### Frontend (Mobile Apps)
- **Framework:** React Native or Flutter
- **State Management:** Redux/Riverpod
- **Navigation:** React Navigation/GoRouter
- **Maps:** Google Maps/Mapbox
- **Payments:** Razorpay SDK
- **Push Notifications:** Firebase Cloud Messaging

### Backend
- **Runtime:** Node.js with Express.js
- **Database:** PostgreSQL (primary), MongoDB (documents)
- **Cache:** Redis
- **Search:** Elasticsearch
- **Message Queue:** RabbitMQ
- **File Storage:** AWS S3
- **APIs:** REST + WebSocket (Socket.io)

### Admin Dashboard (Web)
- **Framework:** React.js
- **State:** Redux
- **UI:** Material-UI / Ant Design
- **Charts:** Recharts / D3.js

### DevOps & Infrastructure
- **Containerization:** Docker & Kubernetes
- **CI/CD:** GitHub Actions
- **Cloud:** AWS / Google Cloud
- **Monitoring:** CloudWatch / DataDog
- **Logging:** ELK Stack

---

## Getting Started

### Prerequisites
- Node.js 16+
- Docker & Docker Compose
- PostgreSQL 12+
- Redis 6+
- Git

### Quick Start

```bash
# Clone repository
git clone https://github.com/MustafaKheda/connect-too.git
cd connect-too

# Copy environment variables
cp .env.example .env

# Start services with Docker
docker-compose up -d

# Install dependencies
npm install

# Run migrations
npm run migrate

# Start development server
npm run dev
```

For detailed setup instructions, see [SETUP.md](docs/SETUP.md)

---

## Project Structure

```
connect-too/
├── PRODUCT_PLAN.md              # Complete feature breakdown
├── ARCHITECTURE.md              # System architecture & APIs
├── DEVELOPMENT_ROADMAP.md       # Phase 1 MVP with 30 issues
├── README.md                    # This file
│
├── backend/
│   ├── services/
│   │   ├── user-service/
│   │   ├── employee-service/
│   │   ├── booking-service/
│   │   ├── payment-service/
│   │   ├── notification-service/
│   │   ├── review-service/
│   │   ├── chat-service/
│   │   └── analytics-service/
│   ├── shared/
│   ├── tests/
│   └── docker-compose.yml
│
├── mobile/
│   ├── employee-app/             # React Native / Flutter
│   └── user-app/                 # React Native / Flutter
│
├── admin/
│   └── dashboard/                # React.js web app
│
├── docs/
│   ├── API_ENDPOINTS.md
│   ├── DATABASE_SCHEMA.md
│   ├── SETUP.md
│   ├── ARCHITECTURE.md
│   └── DEPLOYMENT.md
│
├── .github/
│   ├── workflows/                # CI/CD pipelines
│   └── ISSUE_TEMPLATE/
│
└── docker-compose.yml
```

---

## Key Features

### Phase 1: MVP (Weeks 1-6)
✅ Employee & user authentication  
✅ Employee profile & service management  
✅ Service discovery & search  
✅ Basic booking system  
✅ Subscription management (prepaid)  
✅ Payment integration (Razorpay)  
✅ Basic ratings & reviews  
✅ Real-time notifications  

### Phase 2: Enhancement (Weeks 7-11)
🔄 Postpaid subscriptions  
🔄 Advanced analytics & reporting  
🔄 Recurring bookings  
🔄 Instant payouts  
🔄 Dispute resolution system  
🔄 Admin panel  

### Phase 3: Scaling (Ongoing)
🔮 Video call/consultations  
🔮 AI-powered recommendations  
🔮 Booking insurance  
🔮 Multi-language support  
🔮 Advanced fraud detection  
🔮 Machine learning optimizations  

---

## Development Phases

### Phase 1: MVP (4-6 weeks)
**Goal:** Launch core product with basic functionality

| Week | Focus | Components |
|------|-------|------------|
| 1-2 | Foundation | Backend infra, Auth, Database |
| 3-4 | Core Features | Services, Booking, Mobile apps |
| 5-6 | Polish | Payments, Testing, Launch |

**Deliverables:**
- Functional Employee Portal (React Native/Flutter)
- Functional User Portal (React Native/Flutter)
- All core backend APIs
- Razorpay payment integration
- Basic analytics

See [DEVELOPMENT_ROADMAP.md](DEVELOPMENT_ROADMAP.md) for detailed issues and tasks.

---

## API Overview

All APIs follow REST conventions with JSON payloads.

### Authentication
```
POST /api/v1/auth/register          # User registration
POST /api/v1/auth/login             # User login
POST /api/v1/auth/refresh-token     # Refresh JWT
```

### Employees
```
GET  /api/v1/employees              # List employees
POST /api/v1/employees              # Create profile
GET  /api/v1/employees/:id          # Get profile
PUT  /api/v1/employees/:id          # Update profile
```

### Services
```
GET  /api/v1/services               # List services
POST /api/v1/services               # Create service
GET  /api/v1/services/:id           # Get details
PUT  /api/v1/services/:id           # Update
DELETE /api/v1/services/:id         # Delete
```

### Bookings
```
POST /api/v1/bookings               # Create booking
GET  /api/v1/bookings               # Get user's bookings
PUT  /api/v1/bookings/:id/status    # Update status
DELETE /api/v1/bookings/:id         # Cancel
```

### Payments
```
POST /api/v1/subscriptions          # Subscribe to plan
GET  /api/v1/payments/history       # Payment history
POST /api/v1/payouts/request        # Request payout
```

Full API documentation: [ARCHITECTURE.md](ARCHITECTURE.md)

---

## Database Schema

### Core Tables
- **users** - User authentication & profiles
- **employees** - Extended employee data
- **services** - Service listings
- **bookings** - Booking records
- **subscriptions** - Subscription management
- **payments** - Payment transactions
- **reviews** - Customer reviews
- **messages** - Chat messages
- **availability** - Availability slots

See [docs/DATABASE_SCHEMA.md](docs/DATABASE_SCHEMA.md) for detailed schema.

---

## Success Metrics

### Key Performance Indicators
| Metric | Target | Priority |
|--------|--------|----------|
| Monthly Active Employees | 1000+ | P0 |
| Monthly Active Users | 5000+ | P0 |
| Booking Conversion Rate | >15% | P0 |
| Subscription Renewal Rate | >80% | P0 |
| Platform Rating | >4.5/5.0 | P0 |
| API Uptime | 99.9% | P0 |
| Page Load Time | <2s | P1 |
| Payment Success Rate | >98% | P0 |

---

## Security & Compliance

### Security Measures
✅ OAuth 2.0 + JWT authentication  
✅ End-to-end encryption for sensitive data  
✅ Rate limiting & DDoS protection  
✅ PCI-DSS compliance for payments  
✅ Regular security audits  
✅ Encrypted database at rest & in transit  
✅ 2FA for employees  
✅ RBAC for admin access  

### Compliance
✅ GDPR compliance  
✅ Data deletion on request  
✅ Privacy policy & terms of service  
✅ KYC/AML verification  
✅ Tax reporting (1099/1098)  
✅ Compliance audit logs  

---

## Contributing

### Branch Strategy
- `main` - Production releases
- `develop` - Development base
- `feature/*` - Feature branches
- `bugfix/*` - Bug fixes
- `hotfix/*` - Emergency fixes

### Commit Convention
```
feat: Add new feature
fix: Fix bug
docs: Update documentation
style: Code style changes
refactor: Code refactoring
test: Add/update tests
chore: Build, dependencies
```

### Pull Request Process
1. Create feature branch from `develop`
2. Make changes with proper tests
3. Create PR with description
4. Code review (2 approvals)
5. Merge to `develop`
6. After validation, merge to `main`

---

## Documentation

- **[PRODUCT_PLAN.md](PRODUCT_PLAN.md)** - Complete feature breakdown & specifications
- **[ARCHITECTURE.md](ARCHITECTURE.md)** - System architecture & API specifications
- **[DEVELOPMENT_ROADMAP.md](DEVELOPMENT_ROADMAP.md)** - Phase 1 MVP with GitHub issues
- **[docs/SETUP.md](docs/SETUP.md)** - Development environment setup
- **[docs/API_ENDPOINTS.md](docs/API_ENDPOINTS.md)** - Complete API reference
- **[docs/DATABASE_SCHEMA.md](docs/DATABASE_SCHEMA.md)** - Database design

---

## Roadmap

- [x] Product planning & documentation
- [ ] Phase 1 MVP Development (6 weeks)
  - [ ] Backend core services
  - [ ] Employee mobile app
  - [ ] User mobile app
  - [ ] Payment integration
- [ ] Phase 1 Testing & Launch
- [ ] Phase 2 Enhancement (5 weeks)
- [ ] Phase 3 Scaling

See [DEVELOPMENT_ROADMAP.md](DEVELOPMENT_ROADMAP.md) for detailed timeline.

---

## Team

- **Product Lead:** @MustafaKheda
- **Backend Lead:** TBD
- **Mobile Lead:** TBD
- **DevOps Lead:** TBD

---

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

---

## Contact & Support

- **Email:** support@connecttoo.com
- **Issues:** [GitHub Issues](https://github.com/MustafaKheda/connect-too/issues)
- **Discussions:** [GitHub Discussions](https://github.com/MustafaKheda/connect-too/discussions)

---

## Acknowledgments

- Inspired by Urban Company, Uber, Upwork, and Blinkit
- Built with ❤️ for service professionals
- Special thanks to the open-source community

---

**Last Updated:** 2026-05-09  
**Status:** Planning Phase ✨
