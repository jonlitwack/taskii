# System Components

---
type: Architecture
c4_level: Container
created: 2025-10-20
last_updated: 2025-10-20
status: active
---

## Title

Taskii System Components

## Description

The core system components that implement the intelligent task orchestration platform.

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
- **Purpose**: Multi-channel notification delivery with user preferences
- **Implementation**: SSE-based with priority queuing and dismissible notifications
- **Channels**: In-app notifications, email fallback, push notifications
- **Features**:
  - In-app notification center with unread indicators
  - User-configurable preferences per channel
  - Quiet hours and do-not-disturb settings
  - Task mention alerts (@username in comments)
  - Notification grouping by priority

### 5. Analytics & Intelligence Module
- **Purpose**: Basic task completion analytics and workload visibility
- **Capabilities**:
  - Task completion metrics (on-time vs delayed)
  - Property-level and task-type analytics
  - Staff workload visibility (tasks per staff member)
  - Simple reporting dashboards

### 6. User Preferences Engine
- **Purpose**: Manage personalized user settings and preferences
- **Features**:
  - Notification channel preferences (email, push, in-app)
  - Notification frequency settings (instant, digest, custom schedule)
  - Task view preferences (list, kanban, calendar)
  - Language and timezone settings
  - Theme preferences (light/dark mode)
  - Default task filters and saved views
  - Preference synchronization across devices