# Accedo

![Next.js](https://img.shields.io/badge/Next.js-15-000000?logo=nextdotjs&logoColor=white)
![TypeScript](https://img.shields.io/badge/TypeScript-strict-3178C6?logo=typescript&logoColor=white)
![Tailwind CSS](https://img.shields.io/badge/Tailwind_CSS-4-06B6D4?logo=tailwindcss&logoColor=white)
![Supabase](https://img.shields.io/badge/Supabase-backend-3FCF8E?logo=supabase&logoColor=white)
![Vercel](https://img.shields.io/badge/Vercel-deployed-000000?logo=vercel&logoColor=white)
![WCAG 2.1 AA](https://img.shields.io/badge/WCAG-2.1_AA-7C3AED)
![Status](https://img.shields.io/badge/status-in_development-BFFF4B?labelColor=1a1a1a)

> Verified job board for people with disabilities in Chile.

Accedo is a job platform where every listing's accessibility is checked before it goes live. No tokenism, no "inclusive" claims that only exist on paper — applicants see exactly what accommodations a company offers before they apply.

## Why Accedo exists

Traditional job boards let any company tag a posting as "inclusive" with no verification. People with disabilities apply blind, only to discover during the process that the workplace, the interview, or the role were never actually accessible.

Accedo flips that. Companies complete a structured accessibility form, and listings are reviewed before publication. Verification works in three tiers:

- **Declared** — the company filled out the accessibility form.
- **Validated** — the listing was manually reviewed by the Accedo team.
- **Certified** — the company passed a full accessibility audit.

## Features

- Job listings with real, verified accessibility information
- Applicant profiles with reasonable-accommodation needs and optional LSCh (Chilean Sign Language) video CVs
- Accessibility-aware search and filters
- Application tracking for applicants
- Company dashboard for posting and managing listings
- Admin panel for manual company and listing verification
- Blog with resources on disability employment and Ley 21.015
- WCAG 2.1 AA compliance, full keyboard navigation, and LSCh video support

## Tech stack

| Layer | Technology |
|---|---|
| Framework | Next.js 15 (App Router) |
| Language | TypeScript (strict) |
| Styling | Tailwind CSS 4 |
| Animation | Motion |
| Backend | Supabase (Auth + PostgreSQL + Storage) |
| Email | Resend |
| Hosting | Vercel |

## Getting started

### Prerequisites

- Node.js 18.18 or later
- A Supabase project
- A Resend account (for transactional email)

### Installation

```bash
# Clone the repository
git clone https://github.com/paskuvan/accedo.git
cd accedo

# Install dependencies
npm install

# Set up environment variables
cp .env.example .env.local
# Then fill in .env.local with your own keys
```

### Environment variables

Create a `.env.local` file in the project root:

```bash
NEXT_PUBLIC_SUPABASE_URL=your_supabase_project_url
NEXT_PUBLIC_SUPABASE_ANON_KEY=your_supabase_anon_key
SUPABASE_SERVICE_ROLE_KEY=your_supabase_service_role_key
RESEND_API_KEY=your_resend_api_key
NEXT_PUBLIC_APP_URL=http://localhost:3000
```

### Database setup

1. Create a new project in [Supabase](https://supabase.com).
2. Open the SQL Editor and run `supabase-schema.sql`.
3. Create the storage buckets and run the storage policies (see `SETUP.md`).
4. Generate TypeScript types:

   ```bash
   npx supabase gen types typescript --project-id YOUR_PROJECT_ID --schema public > src/types/database.ts
   ```

### Run the development server

```bash
npm run dev
```

Open [http://localhost:3000](http://localhost:3000) in your browser.

For full step-by-step setup instructions, see [`SETUP.md`](./SETUP.md).

## Project structure

```
src/
├── app/
│   ├── (public)/      Public routes (home, listings, blog)
│   ├── (auth)/        Login and registration
│   ├── (dashboard)/   Applicant, company, and admin dashboards
│   └── api/           Route handlers
├── components/
│   ├── ui/            Base UI primitives
│   ├── layout/        Navbar, footer
│   ├── jobs/          Job-related components
│   └── blog/          Blog components
├── lib/
│   ├── supabase/      Supabase clients (browser, server, middleware)
│   └── validators/    Zod schemas
└── types/             Generated database types
```

## Accessibility

Accessibility is the core of this product, not an afterthought. The project commits to:

- WCAG 2.1 AA as the minimum standard
- Full keyboard navigation
- Screen reader testing (NVDA, JAWS, VoiceOver)
- Subtitles and LSCh video versions for audiovisual content
- Minimum contrast ratios of 4.5:1 for body text and 3:1 for large text
- User-configurable high contrast, larger text, and reduced motion

If you find an accessibility barrier, please open an issue — it is treated as a bug.

## Scripts

| Command | Description |
|---|---|
| `npm run dev` | Start the development server |
| `npm run build` | Build for production |
| `npm run start` | Run the production build |
