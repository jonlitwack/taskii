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

## Tech Stack

- **Frontend:** Next.js 15+ with React 19+, TypeScript, CSS modules
- **Backend:** Next.js API routes with TypeScript
- **Database:** PostgreSQL with Prisma ORM v6+
- **Real-Time:** Server-Sent Events (SSE)
- **AI Integration:** CopilotKit v1+ for intelligent task orchestration
- **Authentication:** SSO integration (OAuth/OpenID Connect)
- **Deployment:** Containerized with Docker, orchestrated with Kubernetes for multi-tenant scalability

## System Components

### 1. Task Orchestration Engine
- **Purpose**: Core intelligence layer that generates tasks from various signals
- **Components**:
  - Guest Feedback Processor: Analyzes reviews and triggers service recovery tasks
  - Occupancy Pattern Analyzer: Generates cleaning and staffing tasks based on booking data
  - Brand Standards Engine: Cascades corporate standards to property-specific tasks
  - Compliance Monitor: Creates regulatory compliance tasks

### 2. Multi-Property Management Layer
- **Purpose**: Handles portfolio-wide operations and property isolation
- **Features**:
  - Property context switching
  - Cross-property analytics
  - Template inheritance from corporate to property level

### 3. Training Integration Module
- **Purpose**: Embeds training within task workflows
- **Capabilities**:
  - Just-in-time training triggers
  - Skill gap identification
  - Certification tracking

### 4. Real-Time Notification System
- **Purpose**: Persistent banner system for critical alerts
- **Implementation**: SSE-based with priority queuing and dismissible notifications

## Data Model Extensions

Building upon the enterprise standards' Todo entity:

### Core Entities
- **Property**: Represents hotels/resorts with location, brand affiliation, manager assignments
- **Task**: Extended from Todo with categories (cleaning, maintenance, service, compliance), priorities, due dates, attachments
- **User**: Staff members with roles, property assignments, skill profiles
- **GuestFeedback**: Reviews, complaints, surveys linked to tasks
- **TrainingMaterial**: Documents, videos attached to task types
- **Notification**: Real-time alerts with priority levels

### Relationships
- Tasks belong to Properties and are assigned to Users
- GuestFeedback triggers Task creation
- TrainingMaterials are attached to Task types
- Users have completion history for training and tasks

## Integration Points

### Guest Feedback Sources
- Google Reviews API integration
- Survey platforms (SurveyMonkey, etc.)
- Property management systems (PMS) integration

### Operational Data
- Booking system APIs for occupancy patterns
- Health inspection databases
- Maintenance scheduling systems

### Communication
- Email service for fallback notifications
- SMS/Push notification services
- SSO providers (Azure AD, Okta, etc.)

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

## Monitoring and Analytics

- **Task Completion Metrics**: On-time vs delayed by property and task type
- **User Engagement**: Training completion rates, task acceptance rates
- **Operational Intelligence**: Predictive alerts for staffing gaps, maintenance needs
- **Guest Satisfaction Correlation**: Link task completion to review score improvements

## Migration Path

The architecture extends the enterprise standards' prototype:

1. **Phase 1**: Enhance data model from Todo to full Task entity
2. **Phase 2**: Add property management and user roles
3. **Phase 3**: Integrate guest feedback sources
4. **Phase 4**: Implement AI-driven task generation
5. **Phase 5**: Deploy real-time notification system

This approach ensures the system evolves from the proven standards while meeting the hospitality industry's complex requirements.