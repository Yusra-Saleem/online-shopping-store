# Modern Online Shopping Platform

> Full-stack headless e-commerce platform built with Next.js 15, Sanity CMS, NextAuth authentication, and Stripe payment processing.

## 1. System Overview

An enterprise-grade headless e-commerce platform providing end-to-end shopping workflows: real-time content modeling in Sanity CMS, user session management with NextAuth, dynamic cart state, and PCI-compliant checkout execution via Stripe webhooks.

## 2. Technical Architecture

```
[ Customer Interface ]
        │
        ▼
[ Next.js 15 App Router ] ── (Server Components & Edge Middleware)
        │
        ├──▶ [ Sanity CMS Client ] ── (Product Catalog & Inventory Sync)
        ├──▶ [ NextAuth Engine ] ── (JWT / OAuth User Authentication)
        └──▶ [ Stripe Payment Gateway ] ── (Checkout Sessions & Webhook Handlers)
```

### Technology Stack
- **Framework:** Next.js (App Router, TypeScript)
- **Headless CMS:** Sanity.io (`sanity.client.ts`, `sanity.config.ts`)
- **Payment Gateway:** Stripe API (Stripe Elements, Webhooks)
- **Authentication:** NextAuth.js
- **Styling:** Tailwind CSS, PostCSS
- **CI/CD:** Automated GitHub Actions build pipeline

## 3. Core Capabilities & Security Guardrails

- **Sanitized Credential Architecture:** Environment configuration isolated into `.env.example` templates; zero credentials stored in version control.
- **Headless Content Pipelines:** Live inventory updates directly orchestrated through Sanity Studio without code redeployments.
- **End-to-End Payment Flow:** Stripe checkout sessions with server-side signature verification and webhook transaction validation.
- **Edge Middleware Security:** Protected account and checkout routes enforced via `middleware.ts`.

## 4. Directory Structure

```
online-shopping-store/
├── .env.example              # Sanitized environment template
├── middleware.ts             # Route authentication and session verification
├── sanity.client.ts          # Sanity GROQ query client configuration
├── sanity.config.ts          # Sanity Studio CMS schema configuration
├── src/
│   ├── app/                  # App Router views and API webhook endpoints
│   ├── components/           # Cart slide-over, product grids, checkout forms
│   └── lib/                  # Stripe helpers and authentication providers
└── package.json              # Project dependencies
```

## 5. Getting Started

### Environment Configuration

Create a `.env.local` file based on the provided template:

```bash
cp .env.example .env.local
```

Populate the required credentials:
```env
NEXT_PUBLIC_SANITY_PROJECT_ID=your_project_id
NEXT_PUBLIC_SANITY_DATASET=production
SANITY_API_TOKEN=your_sanity_token
NEXTAUTH_SECRET=your_nextauth_secret
STRIPE_SECRET_KEY=your_stripe_secret_key
NEXT_PUBLIC_STRIPE_PUBLISHABLE_KEY=your_stripe_pub_key
```

### Installation and Run

```bash
npm install
npm run dev
```

Visit [http://localhost:3000](http://localhost:3000).

## 6. Author and License

- **Author:** Yusra Saleem
- **Portfolio:** [yusrasaleem.dev](https://yusrasaleem.dev)
- **License:** Licensed under the [MIT License](LICENSE).
