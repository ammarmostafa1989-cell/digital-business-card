# CardLux - Premium Digital Business Card Platform

> **GitHub Pages:** Live card → [`index.html`](./index.html)  
> `https://YOUR_USERNAME.github.io/digital-business-card/`

منصة بطاقات أعمال رقمية فاخرة للمحترفين وشركات العقارات في الإمارات.

A world-class digital business card platform built for luxury professionals, executives, and premium real estate companies in the UAE.

## Tech Stack

- **Frontend:** Next.js 15, React 19, TypeScript, Tailwind CSS, Framer Motion
- **Backend:** Next.js API Routes (Full Stack)
- **Database:** PostgreSQL with Prisma ORM
- **Auth:** JWT with HTTP-only cookies
- **i18n:** next-intl (Arabic RTL + English LTR)

## Features

- Premium landing page (Hero, Features, Demo, Pricing, FAQ, Contact)
- User authentication (register, login, forgot password)
- Dashboard & card builder
- Public cards at `/card/[slug]`
- QR codes, vCard export, analytics, admin panel
- SEO, dark/light mode, Arabic + English

## Getting Started

### Prerequisites

- Node.js 18+
- PostgreSQL database
- Git

### Installation

```bash
git clone https://github.com/YOUR_USERNAME/digital-business-card.git
cd digital-business-card

npm install

cp .env.example .env
# Edit .env with your DATABASE_URL and JWT_SECRET

npm run db:push
npm run db:seed
npm run dev
```

Open [http://localhost:3000](http://localhost:3000)

### Environment Variables

Copy `.env.example` to `.env` and set at minimum:

| Variable | Description |
|----------|-------------|
| `DATABASE_URL` | PostgreSQL connection string |
| `JWT_SECRET` | Random secret for auth tokens (required in production) |
| `NEXT_PUBLIC_APP_URL` | Public app URL (e.g. `https://yourdomain.com`) |

See `.env.example` for all optional variables (SMTP, S3, Stripe, etc.).

> **Security:** Never commit `.env` to GitHub. Only `.env.example` is tracked.

### Demo Accounts (after seed)

| Role  | Email              | Default Password |
|-------|--------------------|------------------|
| Admin | admin@cardlux.com  | value of `SEED_ADMIN_PASSWORD` |
| User  | demo@cardlux.com   | value of `SEED_DEMO_PASSWORD` |

Demo cards: `/card/demo-gold`, `/card/demo-dark`, `/card/demo-realestate`

## Upload to GitHub

### First time

```bash
cd digital-business-card

git init
git add .
git commit -m "Initial commit: CardLux digital business card platform"
git branch -M main
git remote add origin https://github.com/YOUR_USERNAME/YOUR_REPO.git
git push -u origin main
```

### Before every push

```bash
git status
# Make sure .env is NOT listed (it must stay local only)

git add .
git commit -m "Your message"
git push
```

### GitHub repository settings

1. Set repository to **Private** if it contains business logic you don't want public
2. Add **Secrets** for deployment (Settings → Secrets and variables → Actions):
   - `DATABASE_URL`
   - `JWT_SECRET`
3. CI runs automatically on push via `.github/workflows/ci.yml`

## Deployment

### Vercel (recommended)

1. Import the GitHub repository on [vercel.com](https://vercel.com)
2. Add environment variables from `.env.example`
3. Deploy — `postinstall` runs `prisma generate` automatically
4. Run `npm run db:push` once against your production database

### Other platforms

Compatible with Cloudflare Pages, DigitalOcean, Railway, Render, and VPS.

## Project Structure

```
src/
├── app/[locale]/     # Localized pages
├── app/card/[slug]/  # Public card pages
├── app/api/          # API routes
├── components/       # UI components
├── lib/              # Auth, DB, analytics, QR, vCard
└── messages/         # en.json, ar.json
prisma/
├── schema.prisma
└── seed.ts
```

## Scripts

| Command | Description |
|---------|-------------|
| `npm run dev` | Start development server |
| `npm run build` | Production build |
| `npm run lint` | Run ESLint |
| `npm run db:push` | Sync schema to database |
| `npm run db:seed` | Seed demo data |
| `npm run db:studio` | Open Prisma Studio |

## License

Private — All rights reserved.
