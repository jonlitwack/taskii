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
- **Notification**: Real-time alerts with priority levels, read/unread status, delivery timestamps
- **UserPreferences**: User-specific settings for notifications, UI preferences, filters
- **TaskAnalytics**: Aggregated metrics for task completion, staff workload, property performance

### Relationships
- Tasks belong to Properties and are assigned to Users
- GuestFeedback triggers Task creation
- TrainingMaterials are attached to Task types
- Users have completion history for training and tasks
- Notifications are sent to Users and linked to Tasks
- UserPreferences belong to Users with preference categories
- TaskAnalytics aggregates data from Tasks and Users

## Schema Details

### UserPreferences Schema
```typescript
{
  id: string
  userId: string
  
  // Notification Preferences
  notificationChannels: {
    email: boolean
    push: boolean
    inApp: boolean
  }
  notificationFrequency: 'instant' | 'digest' | 'custom'
  customSchedule?: string // cron expression
  quietHoursEnabled: boolean
  quietHoursStart?: string // HH:MM format
  quietHoursEnd?: string // HH:MM format
  doNotDisturb: boolean
  mentionAlerts: boolean
  
  // UI Preferences
  taskViewMode: 'list' | 'kanban' | 'calendar'
  theme: 'light' | 'dark' | 'system'
  language: string // ISO 639-1 code
  timezone: string // IANA timezone
  
  // Filter Preferences
  defaultFilters: {
    status?: string[]
    priority?: string[]
    category?: string[]
    propertyId?: string
  }
  savedViews: Array<{
    name: string
    filters: object
  }>
}
```

### Notification Schema
```typescript
{
  id: string
  userId: string
  taskId?: string
  type: 'task_assigned' | 'task_overdue' | 'mention' | 'comment' | 'feedback'
  priority: 'low' | 'medium' | 'high' | 'urgent'
  title: string
  message: string
  read: boolean
  dismissed: boolean
  deliveredAt: Date
  readAt?: Date
  channels: string[] // which channels it was sent on
}
```

### TaskAnalytics Schema
```typescript
{
  id: string
  propertyId?: string
  userId?: string
  taskType?: string
  
  // Metrics
  totalTasks: number
  completedTasks: number
  onTimeTasks: number
  delayedTasks: number
  avgCompletionTime: number // in minutes
  
  // Time period
  periodStart: Date
  periodEnd: Date
  aggregationType: 'daily' | 'weekly' | 'monthly'
}
```