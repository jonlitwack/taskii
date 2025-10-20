# Infrastructure Architecture

---
type: Architecture
c4_level: System
created: 2025-10-20
last_updated: 2025-10-20
status: active
---

## Title

Taskii Infrastructure Architecture

## Description

The deployment, security, and scalability architecture for the platform.

## Deployment Architecture

### Development Environment
- SQLite database for rapid prototyping
- Local CopilotKit runtime
- Single-instance SSE server

### Production Environment
- PostgreSQL cluster with read replicas
- Load-balanced Next.js application servers
- Redis for SSE connection management
- Kubernetes orchestration for multi-tenant isolation

## Security Considerations

- **Data Isolation**: Property-level data segregation
- **Authentication**: SSO with role-based access
- **API Security**: JWT tokens with property context
- **Audit Logging**: All task changes and user actions logged

## Scalability Decisions

- **Database**: PostgreSQL over SQLite for concurrent multi-property operations
- **Caching**: Redis for session management and frequently accessed property data
- **Horizontal Scaling**: Stateless API design enables container scaling
- **Real-Time**: SSE with Redis pub/sub for cross-instance broadcasting