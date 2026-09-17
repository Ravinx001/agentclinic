# Mission

AgentClinic is a health clinic for AI agents. It gives staff a reliable dashboard to
manage a roster of AI agents, diagnose their "ailments," prescribe "therapies," and
book appointments for treatment — the same workflows a real clinic runs, applied to
agents instead of patients.

## Who it's for

- **Staff** who manage the clinic day to day: reviewing agents, scheduling appointments,
  tracking treatment history.
- **Agents** (and the people responsible for them) who are the clinic's patients —
  each with a profile, a history of ailments, and therapies applied over time.

## Target audience

AgentClinic itself (the project, not the in-app persona above) exists to serve:

- **Course students** learning spec-driven development with AI coding agents — the
  clinic's scope and phased roadmap should stay legible as a teaching example, not
  grow so complex it obscures the workflow being taught.
- **Developers giving AI coding demos at conference booths** — the app should be easy
  to stand up quickly, demo end-to-end in a few minutes, and show a clear, visually
  compelling result at each phase.

## Core capabilities (from stakeholder input)

- **Engineering (Mary):** a reliable site on a popular, TypeScript-based stack, with a
  dashboard giving agents and staff easy access.
- **Product (Susan):** agents as first-class records, each with ailments (problems),
  therapies (treatments), and the ability to book appointments.
- **Marketing (Steve):** an attractive site that works well in a modern browser.

## What "done" looks like for v1

Staff can register an agent, log an ailment against it, assign a therapy, and book an
appointment to carry it out — all visible from a single dashboard, on a fast and
reliable TypeScript stack, in a UI that looks good in current browsers.

## Out of scope (for now)

- Public-facing/self-service booking for agent owners (staff-mediated only, initially).
- Billing/payments.
- Multi-clinic / multi-tenant support.
