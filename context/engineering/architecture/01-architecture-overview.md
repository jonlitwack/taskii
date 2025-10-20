# Taskii Architecture Overview

---
type: Architecture
c4_level: System
created: 2025-10-20
last_updated: 2025-10-20
status: active
---

## Title

Taskii - Intelligent Task Orchestration Platform for Hospitality

## Description

Taskii is an intelligent task orchestration platform that automatically translates brand standards, guest feedback, and operational signals into property-specific tasks for hotel and travel brands. The system marries the operational requirements outlined in the project brief with enterprise standards for scalable, AI-enhanced task management.

## Architectural Principles

### 1. Intelligent Task Generation
- **Decision**: Implement AI-driven task creation using CopilotKit runtime integration
- **Rationale**: Aligns with project brief's requirement for automatic task generation from guest feedback, occupancy patterns, and brand standards
- **Standards Alignment**: Follows CopilotKit integration patterns from enterprise standards

### 2. Real-Time Multi-Property Updates
- **Decision**: Use Server-Sent Events (SSE) for real-time synchronization across properties and user sessions
- **Rationale**: Supports portfolio-level dashboards and immediate task updates as required in the brief
- **Standards Alignment**: Extends SSE implementation from enterprise standards to handle multi-tenant property data

### 3. Type-Safe Data Layer
- **Decision**: Prisma ORM with PostgreSQL for production scalability
- **Rationale**: Project requires complex relationships (properties, tasks, users, feedback) beyond simple todo items
- **Standards Alignment**: Builds upon Prisma database layer standards, upgrading from SQLite to PostgreSQL

### 4. Role-Based Access Control
- **Decision**: Implement hierarchical permissions (Corporate Admin → Property Manager → Frontline Staff)
- **Rationale**: Essential for multi-property management and data security as outlined in brief
- **Standards Alignment**: Extends basic authentication patterns to support SSO and role hierarchies