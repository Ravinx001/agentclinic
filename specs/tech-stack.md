# Tech Stack

A single Next.js application, chosen for being a popular, well-supported TypeScript
stack that covers frontend, backend, and deployment in one codebase (per Mary's ask
for a reliable, mainstream stack).

## Application

- **Framework:** Next.js (App Router), TypeScript throughout.
- **UI:** React + Tailwind CSS + shadcn/ui for dashboard components (tables, forms,
  calendars/scheduling widgets).
- **State/data fetching:** React Server Components + Server Actions where possible;
  TanStack Query for client-side data that needs it.

## Data

- **Database:** PostgreSQL.
- **ORM:** Prisma (schema-first, generates TypeScript types end to end).
- **Migrations:** Prisma Migrate.

## Auth

- **Library:** Auth.js (NextAuth) for staff login. Start with email/password or a
  single SSO provider; expand later if needed.

## Testing & quality

- **Unit/integration:** Vitest + React Testing Library.
- **E2E:** Playwright (covers "works well in a modern browser" from Steve's ask).
- **Linting/formatting:** ESLint + Prettier, TypeScript strict mode.

## Deployment

- **Target:** Vercel (first-party Next.js hosting) or an equivalent Node host.
- **Database hosting:** managed Postgres (e.g. Neon/Supabase/RDS) — decide at
  deployment-setup time, not before.

## Conventions

- All new code is TypeScript, no implicit `any`.
- Prefer server-side data access (Server Components/Actions) over client-side fetch
  calls unless real-time interactivity requires it.
- Keep the dashboard and any future public surface in the same app until there's a
  concrete reason to split them.
