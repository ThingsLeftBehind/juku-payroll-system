# Agent Instructions (Internal-only)

You are implementing an internal operations system for a single Japanese cram school branch.
This is a private/internal tool. Do NOT include features intended for selling, multi-tenant SaaS,
marketing, or HQ multi-branch management.

## Non-negotiable constraints
- Do not copy any proprietary UI/text/branding from any existing product.
- Build an original implementation focused on internal workflows.
- Keep the codebase small, clear, and maintainable.
- Prefer simple, reliable logic over complex optimization.

## Required MVP Features
### 1) Core Entities
- Branch (single)
- Users with roles: Admin, Manager, Teacher
- Students
- Parents/Guardians (basic link to students)
- Contracts/Plans (simple monthly plan model)

### 2) Scheduling
- Lesson slots (koma)
- Basic timetable view
- Manual assignment of teachers to slots
- Optional simple auto-suggest (very light heuristic)

### 3) Attendance
- Teacher attendance (clock-in/out)
- Student entry/exit log

### 4) Payroll (highest priority)
Support mixed pay types:
- Hourly wage
- Per-koma wage
- Transport allowance rule (simple fixed or per-day setting)
Payroll must be computed from:
- Approved shifts
- Actual attendance logs
Deliver:
- Monthly payroll summary
- Exportable CSV
- Simple payslip view

### 5) Instruction Notes
- Lightweight instruction report record per lesson slot
- Internal notes only (no parent messaging)

## Explicitly Excluded
- Multi-branch / HQ dashboards
- Lead/CRM, trial funnels, public forms
- Payments (card/direct debit), invoicing automation
- LINE integration
- Online lesson streaming
- Any tenant billing or subscription logic

## Tech Decisions
- Monorepo with Turborepo
- Next.js app for admin operations
- Single web app is fine; do not create separate SaaS portals
- Postgres + Prisma
- Simple RBAC middleware

## Deliverables to generate in code
1) Repository structure:
   - apps/admin-web
   - packages/db (Prisma)
   - packages/core (domain + services)
   - packages/ui (minimal shared components)
   - docs/

2) Prisma schema including:
   - User, Role
   - Student, Parent
   - Teacher
   - ContractPlan, Enrollment
   - ShiftRequest, ShiftAssignment
   - AttendanceTeacher, AttendanceStudent
   - LessonSlot, Schedule
   - PayrollRun, PayrollLine (or equivalent)

3) Admin UI pages (minimal):
   - Dashboard
   - Students
   - Teachers
   - Shifts
   - Attendance
   - Payroll
   - Schedule

4) Core services:
   - PayrollCalcService with tests
   - Basic ScheduleService

5) Seed data + README dev steps

## Quality bar
- Payroll calculation must have unit tests.
- Types must be strict.
- Avoid overengineering.
