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
