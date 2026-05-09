# Technical Architecture & API Specifications

## System Architecture

### High-Level Overview
```
┌─────────────────────────────────────────────────────────────┐
│                   Client Layer (Mobile/Web)                  │
│  ┌──────────────────┐  ┌──────────────────┐  ┌────────────┐ │
│  │ Employee App     │  │ User App         │  │ Admin Web  │ │
│  │ (React Native)   │  │ (React Native)   │  │ (React)    │ │
│  └──────────────────┘  └──────────────────┘  └────────────┘ │
└────────────────────────┬────────────────────────────────────┘
                         │
                         ▼
┌─────────────────────────────────────────────────────────────┐
│                    API Gateway & Load Balancer               │
│              (Kong / AWS API Gateway / Nginx)                │
└────────────────────────┬────────────────────────────────────┘
                         │
        ┌────────────────┼────────────────┐
        │                │                │
        ▼                ▼                ▼
┌──────────────────┐ ┌──────────────────┐ ┌──────────────────┐
│  Auth Service    │ │ Rate Limiter     │ │ Request Logger   │
│                  │ │ & Cache          │ │ & Monitoring     │
└──────────────────┘ └──────────────────┘ └──────────────────┘
        │                │                │
        └────────────────┼────────────────┘
                         │
        ┌────────────────┼────────────────┬────────────────┐
        │                │                │                │
        ▼                ▼                ▼                ▼
┌──────────────────┐ ┌──────────────────┐ ┌──────────────┐ ┌──────────────┐
│  User Service    │ │ Employee Service │ │ Booking Svc  │ │ Payment Svc  │
│  (Port 3001)     │ │ (Port 3002)      │ │ (Port 3003)  │ │ (Port 3004)  │
└──────────────────┘ └──────────────────┘ └──────────────┘ └──────────────┘
        │                │                │                │
    Node.js          Node.js           Node.js           Node.js
    Express          Express           Express           Express
        │                │                │                │
        └────────────────┼────────────────┴────────────────┘
                         │
        ┌────────────────┼────────────────┐
        │                │                │
        ▼                ▼                ▼
   PostgreSQL         Redis            Elasticsearch
    (Primary)        (Cache)            (Search)
        │                │                │
        └────────────────┼────────────────┘
                         │
                    AWS S3 / File Storage
                    Payment Gateway (Razorpay)
                    Email/SMS Services
                    Maps & Location APIs
```

---

## Core API Endpoints

### Authentication & User Service (Port 3001)

#### Auth Endpoints
```
POST   /api/v1/auth/register          - User registration
POST   /api/v1/auth/login             - User login
POST   /api/v1/auth/verify-otp        - OTP verification
POST   /api/v1/auth/refresh-token     - Refresh JWT token
POST   /api/v1/auth/logout            - User logout
POST   /api/v1/auth/forgot-password   - Password reset request
POST   /api/v1/auth/reset-password    - Reset password with token
```

#### User Profile Endpoints
```
GET    /api/v1/users/me               - Get current user profile
PUT    /api/v1/users/me               - Update user profile
POST   /api/v1/users/avatar           - Upload avatar
GET    /api/v1/users/:id              - Get user profile by ID
DELETE /api/v1/users/me               - Delete account
POST   /api/v1/users/verify-kyc       - Submit KYC documents
GET    /api/v1/users/kyc-status       - Get KYC verification status
```

---

### Employee Service (Port 3002)

#### Employee Profile Endpoints
```
GET    /api/v1/employees              - Get all employees (paginated)
POST   /api/v1/employees              - Create employee profile
GET    /api/v1/employees/:id          - Get employee profile
PUT    /api/v1/employees/:id          - Update employee profile
GET    /api/v1/employees/:id/services - Get employee's services
GET    /api/v1/employees/search       - Search employees (with filters)
```

#### Service Endpoints
```
GET    /api/v1/services               - Get all services
POST   /api/v1/services               - Create service listing
GET    /api/v1/services/:id           - Get service details
PUT    /api/v1/services/:id           - Update service
DELETE /api/v1/services/:id           - Delete service
GET    /api/v1/services/search        - Search services by category/location
```

#### Availability Endpoints
```
GET    /api/v1/employees/:id/availability    - Get availability
POST   /api/v1/employees/:id/availability    - Set availability
PUT    /api/v1/employees/:id/availability/:avail_id - Update slot
DELETE /api/v1/employees/:id/availability/:avail_id - Remove slot
GET    /api/v1/employees/:id/availability/calendar  - Get calendar view
```

---

### Booking Service (Port 3003)

#### Booking Endpoints
```
POST   /api/v1/bookings               - Create booking
GET    /api/v1/bookings               - Get user's bookings
GET    /api/v1/bookings/:id           - Get booking details
PUT    /api/v1/bookings/:id/status    - Update booking status
PUT    /api/v1/bookings/:id           - Reschedule booking
DELETE /api/v1/bookings/:id           - Cancel booking
GET    /api/v1/employees/:id/bookings - Get employee's bookings
POST   /api/v1/bookings/:id/complete  - Mark booking as completed
```

#### Booking History Endpoints
```
GET    /api/v1/bookings/history       - Get booking history
GET    /api/v1/bookings/stats         - Get booking statistics
GET    /api/v1/bookings/recurring     - Get recurring bookings
POST   /api/v1/bookings/:id/recurring - Create recurring booking
```

---

### Payment Service (Port 3004)

#### Subscription Endpoints
```
GET    /api/v1/subscriptions          - Get all subscription plans
GET    /api/v1/subscriptions/:id      - Get subscription details
POST   /api/v1/employees/:id/subscribe - Subscribe to plan
PUT    /api/v1/subscriptions/:id      - Upgrade/downgrade plan
DELETE /api/v1/subscriptions/:id      - Cancel subscription
GET    /api/v1/subscriptions/status   - Get current subscription status
```

#### Payment Endpoints
```
POST   /api/v1/payments/initialize    - Initialize payment
POST   /api/v1/payments/webhook       - Payment gateway webhook
GET    /api/v1/payments/history       - Get payment history
POST   /api/v1/payments/refund        - Request refund
GET    /api/v1/invoices/:id           - Get invoice
```

#### Payout Endpoints
```
POST   /api/v1/payouts/request        - Request payout
GET    /api/v1/payouts/history        - Get payout history
GET    /api/v1/payouts/balance        - Get available balance
PUT    /api/v1/payouts/:id            - Update payout method
```

---

### Ratings & Reviews (Port 3005)

#### Review Endpoints
```
POST   /api/v1/reviews                - Create review
GET    /api/v1/reviews                - Get reviews (paginated)
GET    /api/v1/employees/:id/reviews  - Get employee reviews
PUT    /api/v1/reviews/:id            - Update review
DELETE /api/v1/reviews/:id            - Delete review
POST   /api/v1/reviews/:id/respond    - Respond to review
POST   /api/v1/reviews/:id/report     - Report review
```

---

### Messaging Service (Port 3006)

#### Chat Endpoints
```
GET    /api/v1/messages               - Get conversations
POST   /api/v1/messages               - Send message
GET    /api/v1/messages/:conversation_id - Get chat history
PUT    /api/v1/messages/:id           - Edit message
DELETE /api/v1/messages/:id           - Delete message
WS     /api/v1/ws/chat                - WebSocket for real-time chat
```

---

### Analytics Service (Port 3007)

#### Dashboard Endpoints
```
GET    /api/v1/analytics/dashboard    - Get dashboard metrics
GET    /api/v1/analytics/employees    - Employee analytics
GET    /api/v1/analytics/users        - User analytics
GET    /api/v1/analytics/bookings     - Booking analytics
GET    /api/v1/analytics/revenue      - Revenue analytics
POST   /api/v1/analytics/reports      - Generate custom report
```

---

### Admin Service (Port 3008)

#### Admin Endpoints
```
GET    /api/v1/admin/users            - List all users
PUT    /api/v1/admin/users/:id/status - Suspend/activate user
GET    /api/v1/admin/employees/:id/verify - Verify employee
GET    /api/v1/admin/disputes         - List disputes
POST   /api/v1/admin/disputes/:id/resolve - Resolve dispute
GET    /api/v1/admin/analytics        - Platform analytics
POST   /api/v1/admin/notifications    - Send bulk notifications
```

---

## Database Design (Detailed)

### Tables Overview

1. **users** - Core user information
2. **employees** - Extended employee data
3. **services** - Service listings
4. **bookings** - Booking records
5. **subscriptions** - Subscription plans and user subscriptions
6. **payments** - Payment transactions
7. **reviews** - Customer reviews
8. **messages** - Chat messages
9. **availability** - Employee availability slots
10. **notifications** - Notification history
11. **subscription_plans** - Available subscription tiers
12. **kyc_documents** - KYC verification documents

---

## Deployment Strategy

### Development Environment
- Local Docker containers
- Local PostgreSQL + MongoDB
- Nodemon for auto-reload

### Staging Environment
- AWS ECS (Elastic Container Service)
- RDS PostgreSQL
- MongoDB Atlas
- Redis ElastiCache
- CloudFront CDN

### Production Environment
- Kubernetes (EKS)
- Multi-region deployment
- Auto-scaling based on load
- Blue-green deployment strategy
- Disaster recovery plan

---

## Security Measures

1. **API Security**
   - OAuth 2.0 + JWT
   - Rate limiting (100 req/min per user)
   - CORS configuration
   - Request validation & sanitization

2. **Data Security**
   - End-to-end encryption for sensitive data
   - Database encryption at rest
   - SSL/TLS for data in transit
   - PCI-DSS compliance for payments

3. **Authentication & Authorization**
   - 2FA for employees
   - Role-based access control (RBAC)
   - Session management
   - API key management

4. **Monitoring & Logging**
   - ELK Stack for centralized logging
   - DataDog for monitoring
   - CloudTrail for audit logs
   - Real-time alerts

---

## Performance Optimization

### Caching Strategy
- Redis for session management
- Redis for frequently accessed data (employee profiles, services)
- CDN for static assets
- API response caching (5-30 min based on endpoint)

### Database Optimization
- Indexed queries
- Connection pooling (PgBouncer)
- Query optimization
- Read replicas for analytics

### Frontend Optimization
- Code splitting
- Lazy loading
- Image optimization
- Offline support (React Native)

---

## Scalability Plan

### Phase 1 (0-10K users)
- Single server deployment
- PostgreSQL with basic replication
- Redis single instance
- Manual scaling

### Phase 2 (10K-100K users)
- Kubernetes with auto-scaling
- Database sharding (by geography/user_id)
- Redis cluster
- Load balancing

### Phase 3 (100K+ users)
- Multi-region deployment
- Global CDN
- Database sharding across regions
- Advanced caching strategies

---

**Last Updated:** 2026-05-09
