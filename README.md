<div align="center">

# BakeSmart AI

### AI-Powered Production & Waste Management Platform for Bakeries

[![Next.js](https://img.shields.io/badge/Next.js-15-black?style=for-the-badge&logo=next.js)](https://nextjs.org/)
[![React](https://img.shields.io/badge/React-19-61DAFB?style=for-the-badge&logo=react)](https://react.dev/)
[![Prisma](https://img.shields.io/badge/Prisma-6-2D3748?style=for-the-badge&logo=prisma)](https://www.prisma.io/)
[![PostgreSQL](https://img.shields.io/badge/PostgreSQL-Neon-336791?style=for-the-badge&logo=postgresql)](https://neon.tech/)
[![Tailwind CSS](https://img.shields.io/badge/Tailwind-4-06B6D4?style=for-the-badge&logo=tailwindcss)](https://tailwindcss.com/)
[![Clerk](https://img.shields.io/badge/Auth-Clerk-6C47FF?style=for-the-badge)](https://clerk.com/)
[![Gemini](https://img.shields.io/badge/AI-Gemini_2.5_Flash-4285F4?style=for-the-badge&logo=google)](https://ai.google.dev/)

**BakeSmart AI** is a full-stack SaaS bakery management platform that gives bakery owners and production managers a real-time command center — from daily production planning and sales tracking to AI-powered waste forecasting, multi-branch operations, and an intelligent production planner that tells your team exactly what to bake, shift by shift.

🔗 **[Live Demo →](https://bake-smart-ai.vercel.app)** &nbsp;|&nbsp; [Features](#features) · [Tech Stack](#tech-stack) · [Architecture](#architecture) · [Getting Started](#getting-started)

</div>

---

> 📸 **Dashboard Preview**
>
> ![BakeSmart AI Dashboard Preview](https://i.imgur.com/YOUR_DIRECT_GIF_LINK_HERE.gif)

---

## Overview

Running a bakery means making hundreds of production decisions every day: how many croissants to bake for Monday, which branch is running low on baguettes, what percentage of last week's output ended up as waste. **BakeSmart AI** centralizes all of it into one intelligent dashboard.

Built with a **Next.js App Router** architecture, a **Prisma + PostgreSQL (Neon)** backend, and **Google Gemini 2.5 Flash** for natural language AI, BakeSmart is designed for real-world production use — with multi-tenant isolation, streaming AI responses, and a futuristic UI featuring particle field animations and neural network overlays.

---

## What This Project Demonstrates

| Skill Area                 | Implementation                                                                       |
| -------------------------- | ------------------------------------------------------------------------------------ |
| **Full-Stack Development** | Next.js App Router, server components, API routes, SSR-first data fetching           |
| **Database Design**        | Multi-tenant PostgreSQL schema with production, sales, waste, and branch models      |
| **AI Integration**         | Streaming LLM responses with live bakery data context injected into prompts          |
| **Data Visualization**     | Custom chart system with bar, line, and area modes — no third-party chart library    |
| **Auth & Security**        | Multi-tenant data isolation via Clerk + `tenantId`-scoped Prisma queries             |
| **UX Engineering**         | Futuristic UI with particle fields, neural network overlay, page transitions         |
| **Product Thinking**       | AI production planner with risk scoring, waste rate analysis, and demand forecasting |

---

## Features

### Dashboard & KPIs

- **4 live KPI cards** — Units Produced, Units Sold, Waste Units, and Products — each with a 7-day interactive sparkline
- **Hover interactivity** on any sparkline bar to see the exact value for that day with a date label
- **Trend percentage** vs. previous 7-day period shown on every card
- **Production vs Sales chart** with switchable Bar / Line / Area modes and 1W / 4W / 1Y time ranges

### AI Production Planner

- **Day-by-day planning** across a 7-day forward window — pick any day and get AI recommendations
- **Historical recommendations** built from same-weekday sales (last 12 weeks), adjusted for recent trend and waste rate
- **3-tier risk scoring** per product: Low / Medium (≥5% waste) / High (≥8% waste) — sorted high-risk first
- **Editable quantities** — adjust any product up or down, reset individual items or all at once
- **Dynamic risk counters** that decrease in real time when any quantity is set to zero
- **Streaming AI briefing note** generated for each selected day — contextual, actionable
- **One-click apply** to push the plan to the production schedule

### Operations Overview

- **Branch selector** — toggle individual branches on/off to filter all charts and stats
- **Weather badge** per branch with live temperature from WeatherAPI
- **Production efficiency bar** showing sell-through rate across active branches
- **Waste summary** split by production waste vs. sales waste with percentage breakdown

### Waste Tracking

- Log waste events linked to specific products with quantity and waste type
- Waste rate per product calculated over a rolling 30-day window
- Visual breakdown in operations overview with progress bars

### Sales & Production Logging

- Record sales and production entries against any product
- Date-scoped entries feed into all charts and AI recommendations
- Recent sales table on the dashboard with product name, date, and quantity

### Revenue Analytics

- Estimated revenue calculated from per-product prices
- Revenue chart with the same time-range selector as the main dashboard
- Breakdown by product — sorted by revenue, with unit count and price per unit

### UI/UX & Design System

- **Futuristic visual layer** — particle field canvas, neural network overlay, cursor glow, page transitions (Framer Motion)
- **Themeable brand colors** — 10 primary + 8 secondary presets including the signature amber/brown palette
- **Live background lighting** that shifts with the selected brand color
- **Dark mode support** with comprehensive Tailwind utility remapping

---

## Tech Stack

| Category           | Technology                            |
| ------------------ | ------------------------------------- |
| **Framework**      | Next.js (App Router)                  |
| **UI Library**     | React 19                              |
| **Styling**        | Tailwind CSS 4                        |
| **Database**       | PostgreSQL via Neon Serverless        |
| **ORM**            | Prisma 6 with Neon adapter            |
| **Authentication** | Clerk 7                               |
| **AI / LLM**       | Google Gemini 2.5 Flash               |
| **Animations**     | Framer Motion                         |
| **Weather API**    | WeatherAPI + Nominatim geocoding      |
| **Icons**          | React Icons (Material Design), Lucide |
| **Theme**          | Next Themes                           |

---

## Architecture

```
bake-smart-ai/
├── src/
│   ├── app/
│   │   ├── (app)/
│   │   │   ├── layout.tsx                   # Sidebar + TopBar + ParticleField + NeuralOverlay
│   │   │   ├── dashboard/page.tsx           # KPIs, charts, recent sales
│   │   │   ├── ai-predictor/page.tsx        # AI production planner
│   │   │   ├── operations/page.tsx          # Branch overview + efficiency
│   │   │   ├── production/page.tsx          # Log production entries
│   │   │   ├── sales/page.tsx               # Log sales entries
│   │   │   ├── waste/page.tsx               # Waste logging
│   │   │   ├── revenue/page.tsx             # Revenue analytics
│   │   │   └── advanced-analytics/page.tsx  # AI insights
│   │   ├── sign-in/[[...sign-in]]/          # Custom Clerk sign-in page
│   │   ├── sign-up/[[...sign-up]]/          # Custom Clerk sign-up page
│   │   ├── welcome/                         # Animated loading splash screen
│   │   └── api/
│   │       ├── chat/route.ts                # Google Gemini streaming AI endpoint
│   │       ├── predictor/route.ts           # AI production recommendations
│   │       └── ...                          # CRUD routes
│   ├── components/
│   │   ├── chart.tsx                        # Custom bar/line/area chart
│   │   ├── neural-network-overlay.tsx       # Full-screen animated node graph
│   │   ├── particle-field.tsx               # Canvas particle background
│   │   └── ...
│   ├── contexts/
│   │   └── theme-context.tsx                # Brand color system + CSS variables
│   ├── hooks/
│   │   └── use-cursor-glow.ts               # Brand-colored cursor glow
│   └── lib/
│       ├── prisma.ts
│       └── chart-utils.ts
├── prisma/
│   └── schema.prisma
└── proxy.ts                                 # Clerk auth middleware
```

---

## Getting Started

### Prerequisites

- Node.js 18+
- PostgreSQL database (or [Neon](https://neon.tech/) serverless — recommended)
- [Clerk](https://clerk.com/) account for authentication
- Google Gemini 2.5 Flash API Key
- WeatherAPI key for branch weather badges

### Installation

```bash
git clone https://github.com/RiaVirk/bake-smart-ai.git
cd bake-smart-ai
npm install
```

### Environment Variables

Create a `.env` file:

```env
DATABASE_URL="postgresql://..."

NEXT_PUBLIC_CLERK_PUBLISHABLE_KEY=pk_...
CLERK_SECRET_KEY=sk_...
NEXT_PUBLIC_CLERK_SIGN_IN_URL=/sign-in
NEXT_PUBLIC_CLERK_SIGN_UP_URL=/sign-up
NEXT_PUBLIC_CLERK_AFTER_SIGN_IN_URL=/welcome
NEXT_PUBLIC_CLERK_AFTER_SIGN_UP_URL=/welcome

ANTHROPIC_API_KEY=sk-ant-...

NEXT_PUBLIC_WEATHER_API_KEY=...
```

### Database Setup

```bash
npx prisma generate
npx prisma db push
```

### Run

```bash
npm run dev
# Open http://localhost:3000
```

---

## Key Engineering Decisions

**Custom chart system** — No Recharts or Chart.js. Built from scratch with SVG and HTML for full control over styling and performance.

**Server-first data fetching** — Dashboard metrics computed server-side with Prisma. Fast first render, no client-side waterfalls.

**Multi-tenant by design** — Every query scoped by `tenantId` at the database layer, not retrofitted middleware.

**Streaming AI responses** — Chat assistant and production briefings stream token-by-token so users see results immediately.

**Risk scoring on real data** — Risk levels (≥8% = high, ≥5% = medium) calculated from actual 30-day waste rates per product.

---

## Roadmap

- [x] AI production planner with per-product risk scoring
- [x] Multi-branch operations overview with weather integration
- [x] Streaming Google Gemini chat assistant
- [x] Custom chart system (bar / line / area)
- [x] Futuristic UI layer (particles, neural overlay, transitions)
- [x] Custom sign-in / sign-up pages with bakery branding
- [ ] Product and branch creation UI _(in progress)_
- [ ] Push notifications for waste risk alerts
- [ ] Mobile-optimized layout
- [ ] CSV / PDF export for production plans
- [ ] Multi-user per bakery account

---

## Author

**Maria Virk** — Digital Manager & Full-Stack Developer

- 🌐 [mariavirk.com](https://www.mariavirk.com)
- 💼 [linkedin.com/in/maria-virk](https://linkedin.com/in/maria-virk)
- 💻 [@RiaVirk](https://github.com/RiaVirk)
- 📧 [virkmariaofficial@gmail.com](mailto:virkmariaofficial@gmail.com)

---

## License

MIT License — see [LICENSE](LICENSE) for details.

---

<div align="center">

Built with Next.js · Prisma · Clerk · Anthropic Claude · Tailwind CSS · Framer Motion

</div>
