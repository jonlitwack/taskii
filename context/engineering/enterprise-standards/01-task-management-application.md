# Task Management Application (Taskii)

---
type: Architecture
c4_level: System
created: 2025-10-16
last_updated: 2025-10-16
status: active
---

## Title

Task Management Application (Taskii)

## Description

A task management web application built for rapid prototyping during a 2-day GenAI-driven workshop. The application allows users to create and manage todo items with AI-powered assistance through CopilotKit integration, featuring a sidebar chat interface for interactive help and task management.

## Tech Stack

- **Frontend:** Next.js 15.5.5 with React 19.1.0, TypeScript, CSS modules
- **Backend:** Next.js API routes with TypeScript
- **Database:** SQLite with Prisma ORM v6.17.1
- **APIs:** REST API for todo CRUD operations, CopilotKit runtime integration
- **AI Integration:** CopilotKit React components (@copilotkit/react-core, @copilotkit/react-ui, @copilotkit/runtime v1.10.6)
- **Development Tools:** ESLint v9, TypeScript v5, Turbopack, Prisma migrations and seeding

## Integrations

- [Prisma Database Layer](./02-prisma-database-layer.md) (ORM and database management)
- [CopilotKit Runtime](./03-copilotkit-integration.md) (AI assistance framework)

## Dependencies

- Next.js v15.5.5+
- React v19.1.0+
- Node.js v18+
- Prisma v6.17.1+
- CopilotKit v1.10.6+
- TypeScript v5+

## Contracts

- REST API contract for todo operations ([todos-api.md](../contracts/todos-api.md))
- CopilotKit integration interface ([copilotkit-contract.md](../contracts/copilotkit-contract.md))

## Related Items

- [00-collaboration-workflow.md](../rules/00-collaboration-workflow.md)
- [01-user-requirements.md](../requirements/01-user-requirements.md)
- [01-tech-stack-decisions.md](../decisions/01-tech-stack-decisions.md)</content>
