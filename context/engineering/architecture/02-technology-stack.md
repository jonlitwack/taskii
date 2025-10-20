# Technology Stack

---
type: Architecture
c4_level: System
created: 2025-10-20
last_updated: 2025-10-20
status: active
---

## Title

Taskii Technology Stack

## Description

The technology stack for Taskii builds upon the enterprise standards while scaling for multi-tenant hospitality operations.

## Tech Stack

- **Frontend:** Next.js 15+ with React 19+, TypeScript, CSS modules
- **Backend:** Next.js API routes with TypeScript
- **Database:** PostgreSQL with Prisma ORM v6+ (SQLite for local development)
- **Real-Time:** Server-Sent Events (SSE)
- **AI Integration:** CopilotKit v1+ for intelligent task orchestration
- **Authentication:** SSO integration (OAuth/OpenID Connect)
- **Notifications:** Browser Notifications API, email via SMTP
- **Deployment:** Containerized with Docker, orchestrated with Kubernetes for multi-tenant scalability

## MVP Technology Decisions

For POC/MVP simplicity:
- **Analytics**: Computed on-demand from PostgreSQL database
- **Notifications**: Browser push notifications + email fallback (no external SMS/push services)
- **Preferences**: Stored in PostgreSQL, synced via SSE
- **Reporting**: Server-side aggregation with simple JSON API responses