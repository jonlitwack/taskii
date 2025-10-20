# Data Architecture

---
type: Architecture
c4_level: Component
created: 2025-10-20
last_updated: 2025-10-20
status: active
---

## Title

Taskii Data Architecture

## Description

The data model extensions that support the hospitality task orchestration requirements.

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