# Juku Internal Ops System

Internal-only operations tool for a single Japanese cram school branch.
This project is NOT intended for commercial distribution.  
Goal is to replace/assist current workflows with a lightweight, maintainable system.

## Scope (Phase 1 MVP)
- Student/Parent basic registry
- Contract/plan management (simple)
- Lesson slots (koma) management
- Teacher profiles
- Shift submission/approval
- Teacher attendance
- Payroll calculation (hourly + per-koma + transport rule)
- Student attendance/entry-exit logging
- Simple instruction report notes
- Basic monthly summary (no payment integration)

## Out of Scope (explicitly excluded)
- Multi-branch HQ features
- Marketing/lead management
- Trial lesson funnels
- Public-facing portal for sales
- Card payment / direct debit integrations
- LINE integration (can be considered later)
- Online lesson platform

## Tech
- TypeScript
- Next.js (App Router)
- Turborepo
- Postgres + Prisma

## Local Development (planned)
1. Install dependencies
   - `pnpm install`
2. Start local database (Docker)
   - `docker compose up -d`
3. Apply migrations & seed
   - `pnpm db:migrate`
   - `pnpm db:seed`
4. Run apps
   - `pnpm dev`

## Notes
This repository should remain minimal and pragmatic.
Prioritize correctness of scheduling, attendance, and payroll rules
over feature breadth.
