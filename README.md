# Black Market Supply & Demand

### Full-Stack E-Commerce Application — Technical Case Study

Black Market Supply & Demand is a production full-stack e-commerce application built around a larger independent brand and commerce concept.

Rather than functioning as a static storefront, the application implements real transactional workflows including authentication, persistent shopping carts, inventory validation, payments, order processing, customer accounts, and protected administrative functionality.

> **Commercial Project — Production Source Code Private**
>
> Black Market Supply & Demand is an independently developed application and an active commercial project. This public repository documents the architecture, technologies, engineering challenges, and development of the platform. The production source repository remains private.

## Technology Stack

### Front End
- Next.js
- React
- TypeScript
- Responsive web interface

### Back End & Data
- Next.js server-side functionality
- PostgreSQL
- Prisma ORM
- Authentication and session management
- Role-based authorization

### Commerce & Payments
- Stripe Checkout
- Stripe webhooks
- Persistent shopping cart
- Inventory validation
- Inventory reservation and release
- Order processing

### Development & Deployment
- Git
- GitHub
- Production deployment
- Environment-based configuration
- Production build and deployment troubleshooting

---

## Core Application Features

### Authentication & Authorization

The application provides authenticated customer accounts while separating normal customer functionality from protected administrative functionality.

Key capabilities include:

- User registration and login
- Persistent authenticated sessions
- Role-based authorization
- Protected administrative routes
- Auth-aware navigation
- Customer account functionality

### Product & Storefront

The storefront is connected to application data rather than being a static product mockup.

Functionality includes:

- Database-driven product information
- Product options and purchasing controls
- Product availability validation
- Responsive storefront interface

### Persistent Shopping Cart

Authenticated users can maintain a persistent shopping cart connected to application data.

The cart supports:

- Adding products
- Product options
- Quantity controls
- Removing items
- Price calculations
- Inventory-aware quantity validation

### Inventory Management

Inventory required additional business logic beyond basic product CRUD operations.

The system accounts for:

- Physical inventory quantity
- Reserved inventory
- Available inventory
- Purchase quantity validation
- Overselling protection
- Inventory reservation and release

### Stripe Payment Workflow

Stripe Checkout handles the payment portion of the transaction while the application maintains its own commerce and order data.

The workflow includes:

1. Customer builds a cart
2. Application validates inventory
3. Checkout session is created
4. Customer completes payment through Stripe
5. Stripe sends payment events to the application
6. Webhook processing updates the appropriate application data
7. Order information becomes available through the customer's account

### Orders & Customer Accounts

Customer functionality includes:

- Persistent account data
- Order creation
- Order history
- Transaction-related information

### Administration

Administrative functionality is separated from the public storefront and normal customer experience.

Current administrative capabilities include:

- Protected admin dashboard
- User management
- Category management
- Product and inventory-related administration
- Role-based access controls

---

## High-Level Architecture

```text
Customer
   │
   ▼
Next.js / React Interface
   │
   ├──── Authentication & Authorization
   │
   ├──── Storefront / Cart
   │
   ├──── Customer Account
   │
   └──── Admin Dashboard
   │
   ▼
Application / Server Logic
   │
   ├──── Prisma ORM
   │        │
   │        ▼
   │    PostgreSQL
   │
   └──── Stripe Checkout
            │
            ▼
       Stripe Payment
            │
            ▼
       Stripe Webhook
            │
            ▼
       Order / Inventory
```

---

## Engineering Challenges

### 1. Persistent Cart State

A shopping cart becomes significantly more complex when it must persist across authenticated sessions.

The application needed to coordinate:

- User identity
- Product selections
- Product options
- Quantities
- Pricing
- Inventory availability
- Database persistence

### 2. Preventing Overselling

Simply storing a product quantity is not enough for a transactional commerce system.

The application uses inventory logic that distinguishes between inventory quantity and reserved inventory so that available inventory can be validated before purchases proceed.

### 3. External Payment Processing

Stripe introduced an external system into the application workflow.

Instead of assuming a browser redirect means a payment succeeded, webhook processing allows the application to respond to payment events from Stripe and coordinate those events with application data.

### 4. Authentication and Administrative Security

The application contains functionality that should not be available to normal users.

Authentication and authorization logic therefore needed to protect customer data and administrative functionality while maintaining the appropriate user experience for each role.

### 5. Production Deployment

Moving the application from local development into production required troubleshooting and validating:

- Production builds
- Environment configuration
- Database connectivity
- Authentication behavior
- Stripe integration
- Deployment configuration

---

## V1 Production Workflow

The first production version establishes the core commerce lifecycle:

```text
Browse Product
      ↓
Select Options
      ↓
Add to Cart
      ↓
Validate Inventory
      ↓
Checkout
      ↓
Stripe Payment
      ↓
Webhook Processing
      ↓
Order
      ↓
Customer Order History
```

## Project Status

### V1 — Deployed September 2026

The first production version successfully established the application's core full-stack commerce architecture.

Development continues beyond V1.

### Post-V1 Engineering Roadmap

Planned areas of continued development include:

- Automated end-to-end testing
- CI/CD improvements
- Production observability and error monitoring
- Product analytics
- Transactional email
- Caching and rate limiting
- Background jobs and scheduled processes
- Object storage where appropriate
- Search improvements as the product catalog grows

---

## What This Project Demonstrates

This project demonstrates practical experience with:

- Full-stack application development
- Next.js and React
- TypeScript
- Relational database design
- PostgreSQL
- Prisma ORM
- Authentication and authorization
- Role-based access control
- E-commerce business logic
- Persistent application state
- Inventory management
- Third-party payment integration
- Stripe Checkout
- Webhooks
- Debugging and troubleshooting
- Git-based development
- Production deployment

---

## Screenshots

Application screenshots and additional architecture documentation will be added to this case study as development continues.

---

## About the Developer

**Sean Reed**

Full-Stack Developer | Microsoft 365 & SharePoint Professional | Designer

I build software that combines technical engineering with strong user experience and visual design. My background includes full-stack development, Microsoft 365, SharePoint Online, enterprise IT, and professional design.

**Portfolio:** https://sreedthecoder.com/home  
**GitHub:** https://github.com/sreedartwork

---

*Black Market Supply & Demand is an independently developed project. Production source code is maintained in a private repository.*
