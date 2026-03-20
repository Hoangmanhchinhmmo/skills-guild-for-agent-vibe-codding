# Build a Full E-commerce Store

> **What you'll build:** A medium-scale online store handling 100–500 products, complete with category management, real-time inventory tracking, a flexible coupon system, and a bold, colorful storefront inspired by modern Shopify themes. Payments are handled through **three gateways** — Stripe, VNPay, and PayPal — so your store works for customers worldwide.
>
> Each milestone produces a **fully working result**. You can stop after any milestone and have a real, deployable store.

---

## Tech Stack

| Layer | Technology | Deployment |
|-------|-----------|------------|
| **Frontend** | Next.js (React) + Tailwind CSS | Vercel |
| **Backend** | Node.js (Express) | Docker |
| **Database** | MongoDB Atlas | Cloud (free tier) |
| **Payments** | Stripe + VNPay + PayPal | API integrations |
| **Email** | SendGrid / Resend | API integration |
| **Images** | Cloudinary | Cloud (free tier) |

---

## Features

Everything you'll implement across the three milestones:

- [ ] **Authentication + OAuth** — Email/password and social login (Google, GitHub)
- [ ] **Product Catalog** — Full CRUD, search, filtering, and sorting
- [ ] **Shopping Cart + Checkout** — Persistent cart with multi-step checkout flow
- [ ] **Order Management** — Order tracking, status updates, order history
- [ ] **Admin Dashboard** — Product management, revenue stats, analytics charts
- [ ] **Coupons & Discounts** — Percentage, fixed-amount, and free-shipping codes
- [ ] **Reviews & Ratings** — Star ratings, written reviews, average score display
- [ ] **Email Notifications** — Order confirmation, shipping updates, password reset
- [ ] **Responsive Mobile-First Design** — Looks great on every screen size
- [ ] **SEO-Optimized Product Pages** — Meta tags, structured data, social sharing

---

## Milestones

The workflow is split into three milestones. Each one builds on the last, and each one ends with something you can actually use.

### Milestone 1 — MVP Store

Get a working storefront with real payments in the shortest path possible.

**What you'll do:**
- Project setup and folder structure
- MongoDB schema design and seed data
- REST API for products and categories
- Storefront UI with product listing and detail pages
- Shopping cart with persistent state
- Stripe checkout integration

**Result:** A functional store where customers can browse products, add them to a cart, and pay with Stripe.

-> [Start Milestone 1](ecommerce/milestone-1-mvp.md)

---

### Milestone 2 — Full Features

Add everything that makes a store production-worthy.

**What you'll do:**
- User authentication with JWT + OAuth (Google, GitHub)
- Order management system with status tracking
- Admin dashboard with revenue charts and product CRUD
- Coupon and discount engine
- Customer reviews and ratings
- VNPay and PayPal payment integrations
- Transactional email notifications (SendGrid/Resend)

**Result:** A feature-complete store with user accounts, an admin panel, three payment methods, and automated emails.

-> [Start Milestone 2](ecommerce/milestone-2-features.md)

---

### Milestone 3 — Production Launch

Harden, optimize, and deploy to the real world.

**What you'll do:**
- SEO optimization (meta tags, Open Graph, JSON-LD structured data)
- Responsive design polish and mobile-first refinements
- Dockerize the backend
- Deploy frontend to Vercel, backend via Docker
- Security hardening (rate limiting, input sanitization, CORS, HTTPS)

**Result:** A production-ready e-commerce store, live on the internet, optimized for search engines and mobile users.

-> [Start Milestone 3](ecommerce/milestone-3-launch.md)

---

## All Skills Used

This workflow covers approximately 25 skills from the Skills Guild. Here's where each one appears:

| # | Skill | Milestone |
|---|-------|-----------|
| 1 | Project scaffolding (Next.js + Express) | 1 |
| 2 | Environment configuration (.env, config files) | 1 |
| 3 | MongoDB schema design | 1 |
| 4 | Database seeding with sample data | 1 |
| 5 | REST API design (Express routes + controllers) | 1 |
| 6 | API error handling and validation | 1 |
| 7 | React component architecture | 1 |
| 8 | Tailwind CSS styling and theming | 1 |
| 9 | State management (cart logic) | 1 |
| 10 | Third-party API integration (Stripe) | 1 |
| 11 | Authentication with JWT | 2 |
| 12 | OAuth integration (Google, GitHub) | 2 |
| 13 | Role-based access control (admin vs. customer) | 2 |
| 14 | Complex data relationships (orders, reviews) | 2 |
| 15 | Dashboard UI with charts and data tables | 2 |
| 16 | Coupon/discount business logic | 2 |
| 17 | File/image upload (Cloudinary) | 2 |
| 18 | Payment gateway integration (VNPay, PayPal) | 2 |
| 19 | Transactional email setup (SendGrid/Resend) | 2 |
| 20 | SEO meta tags and structured data (JSON-LD) | 3 |
| 21 | Open Graph and social sharing optimization | 3 |
| 22 | Responsive design and mobile-first CSS | 3 |
| 23 | Docker containerization | 3 |
| 24 | Deployment automation (Vercel + Docker host) | 3 |
| 25 | Security hardening (rate limiting, CORS, sanitization) | 3 |

---

## Prerequisites

Before you start, make sure you have:

- **Claude Code** installed and working on your machine
- **Basic understanding** of frontend (HTML, CSS, React basics) and backend (REST APIs, databases) concepts — you don't need to be an expert, but you should know what these terms mean
- **MongoDB Atlas account** — free tier is more than enough ([create one here](https://www.mongodb.com/cloud/atlas/register))
- **Stripe account** — free test mode, no credit card needed ([sign up here](https://dashboard.stripe.com/register))
- **Node.js 18+** and **npm** installed locally

VNPay and PayPal accounts are only needed in Milestone 2. You can start without them.

---

Ready to build? Pick your starting point:

| I want to... | Go to |
|--------------|-------|
| Start from scratch | [Milestone 1 — MVP Store](ecommerce/milestone-1-mvp.md) |
| I already have a basic store and want to add features | [Milestone 2 — Full Features](ecommerce/milestone-2-features.md) |
| My store is feature-complete and I need to ship it | [Milestone 3 — Production Launch](ecommerce/milestone-3-launch.md) |
