# Roadmap

Foundation-first: get the app scaffolded and running, then add one thin feature slice
at a time. Each phase should be small enough to ship and demo on its own.

## Phase 0 — Scaffolding
- Initialize Next.js + TypeScript project.
- Set up Tailwind + shadcn/ui.
- Set up Prisma + Postgres connection, initial empty schema, migrations working.
- CI: lint, typecheck, test running on every push.
- Deploy a "hello world" version to confirm the pipeline works end to end.

## Phase 1 — Staff auth
- Add Auth.js with staff login (single role to start).
- Protect the dashboard behind login.
- Basic staff account seeding (no self-signup yet).

## Phase 2 — Agent records
- `Agent` model (name, owner/contact, status, created date).
- Dashboard: list agents, view agent detail page, create/edit agent.

## Phase 3 — Ailments
- `Ailment` model linked to an `Agent` (description, severity, status: open/resolved).
- Add/view ailments from an agent's detail page.

## Phase 4 — Therapies
- `Therapy` model linked to an `Ailment` (type, notes, status).
- Assign a therapy to an ailment; show therapy history on the agent page.

## Phase 5 — Appointments
- `Appointment` model linking an `Agent` + `Therapy`/`Ailment` to a date/time and staff
  member.
- Booking UI: create/view/cancel appointments.
- Dashboard view: upcoming appointments across all agents.

## Phase 6 — Dashboard polish
- Home dashboard: summary counts (open ailments, upcoming appointments), quick links.
- Responsive/visual pass for modern-browser polish (Steve's ask).
- E2E tests (Playwright) covering the core flow: create agent → log ailment → assign
  therapy → book appointment.

## Later / not yet scheduled
- Public/self-service booking for agent owners.
- Notifications/reminders for upcoming appointments.
- Reporting (ailment trends, therapy effectiveness).
- Multi-role permissions beyond a single staff role.
