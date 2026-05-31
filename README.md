# 🍳 OrderFlow

> A SaaS platform for home-based food businesses and cloud kitchens to manage orders, track revenue, and serve customers — all through a branded online storefront.

### 🌐 [Live Demo → orderflow-cncscth4fncpe5g3.francecentral-01.azurewebsites.net](https://orderflow-cncscth4fncpe5g3.francecentral-01.azurewebsites.net)

> 🔜 A custom domain is coming soon.

> 🛍️ To explore a storefront and place a test order, sign up for an account and visit:
> `https://orderflow-cncscth4fncpe5g3.francecentral-01.azurewebsites.net/store/your-username`

---

## 📌 Overview

OrderFlow is a multi-tenant order management system built specifically for home-based food businesses and cloud kitchens in Egypt. Each kitchen gets its own branded storefront, a real-time operations dashboard, and smart order management tools — all under one platform.

---

## 🎬 Demo



https://github.com/faresmoustafa1/orderflow/Screen Recording 2026-05-31 072609.mp4



---

## 📸 Screenshots

| Dashboard | Storefront |
|---|---|
| ![Dashboard](screenshots/dashboard.png) | ![Storefront](screenshots/store.png) |

| Finance | Menu Management |
|---|---|
| ![Finance](screenshots/finance.png) | ![Menu](screenshots/menu.png) |

---

## ✨ Features

### 🧑‍🍳 Kitchen Dashboard
- **Daily & Weekly Order Views** — see exactly what needs to be cooked and when
- **Item-level Progress Tracking** — mark each dish as prepared individually
- **Order Status Flow** — Pending → Ready for Pickup → Completed
- **Reschedule Orders** — change delivery date/time directly from the dashboard

### 🛍️ Public Storefront
- Every kitchen gets a unique URL: `/store/{username}`
- Customers can browse the menu, select items/packages, choose delivery date & time
- Integrated with the kitchen's working hours and off-days calendar

### 📋 Menu & Package Management
- Add, edit, and delete menu items with price and cost
- Create bundles/packages with a discounted price
- Toggle item availability — disabling an item auto-disables related packages

### 📅 Schedule Management
- Set working hours per day for the next 7 days
- Mark specific days as off — reflected instantly on the public storefront
- Prevents customers from booking orders outside working hours

### 📊 Finance Dashboard
- Revenue and profit charts (daily, weekly, monthly, yearly)
- Item performance breakdown — which dishes sell most and earn most
- Frozen pricing at order time ensures historical accuracy

### 🔐 Authentication
- JWT-based session cookies (no DB hit on every request)
- Multi-tenant data isolation — each kitchen only sees its own data
- Signup, login, logout, and settings update with token refresh

---

## 🛠️ Tech Stack

| Layer | Technology |
|---|---|
| **Backend** | Python, FastAPI, SQLAlchemy ORM |
| **Database** | SQLite (MVP) |
| **Authentication** | JWT (PyJWT) |
| **Frontend** | Jinja2 Templates, Vanilla JS |
| **Styling** | Custom CSS (per page) |
| **Server** | Uvicorn + ProxyHeaders Middleware |

---

## 🗂️ Project Structure

```
order_flow/
├── __init__.py          # Package initializer
├── main.py              # All FastAPI routes and business logic
├── models.py            # SQLAlchemy database models
├── database.py          # DB engine, session, and base config
├── static/
│   ├── css/             # Per-page stylesheets
│   ├── js/              # Per-page JavaScript
│   ├── images/          # Background assets
│   └── sounds/          # Notification sounds
└── templates/           # Jinja2 HTML templates
    ├── dashboard.html
    ├── weekly_dashboard.html
    ├── finance.html
    ├── history.html
    ├── menu.html
    ├── schedule.html
    ├── store.html
    ├── settings.html
    ├── login.html
    └── signup.html
```

---

## 🔧 Backend — What I Built

### 🏗️ System Architecture & Database Design
Designed the entire multi-tenant data model from scratch using SQLAlchemy ORM. Every resource (menus, orders, packages, schedules) is scoped per user, ensuring complete data isolation between kitchens without a separate database per tenant — a clean and scalable single-DB multi-tenancy pattern.

### 🔐 Authentication System
Implemented a stateless JWT-based auth system using HTTP-only cookies. Tokens are validated on every protected request without hitting the database, keeping the system fast and scalable. Handled token refresh and secure logout flows.

### 📦 Order Management Engine
Built the full order lifecycle from placement to completion — including item-level progress tracking, order rescheduling, and status transitions. Implemented **price & cost freezing at order time**, meaning historical financial data stays accurate even if menu prices change later.

### 🛍️ Public Storefront API
Designed and built all public-facing endpoints that power each kitchen's storefront — menu listing, package availability, schedule visibility, and order submission — all filtered by username with no auth required from the customer side.

### 📅 Schedule & Availability System
Built a 7-day rolling schedule system that lets kitchen owners set working hours and toggle off-days. These constraints are enforced on the backend, preventing customers from placing orders outside available time slots.

### 📊 Finance & Analytics API
Built the finance endpoints that aggregate revenue and profit data across daily, weekly, monthly, and yearly timeframes — with per-item breakdowns showing best-selling and most profitable dishes.

### ☁️ Cloud Deployment on Azure
Deployed the full application to **Azure App Service** — configured the production environment, handled environment variables and secrets, set up the server with Uvicorn behind Azure's reverse proxy using `ProxyHeadersMiddleware` to correctly handle forwarded requests.

---

## 🧑‍💻 Team

| Role | Contributor |
|---|---|
| **Backend Development** | [Your Name](https://github.com/your-username) |
| **Frontend Development** | [Iman](https://github.com/iman-username) |

---

## 🗺️ Roadmap

- [ ] Password hashing (bcrypt)
- [ ] Database migrations with Alembic
- [ ] Mobile responsive design improvements
- [ ] WhatsApp integration
- [ ] Push notifications for new orders
- [ ] Customer order history portal
- [ ] Pagination on history and order lists
- [ ] Custom domain
- [ ] PostgreSQL support for production deployment
