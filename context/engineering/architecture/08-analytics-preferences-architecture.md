# Analytics, Preferences & Notifications Architecture

---
type: Architecture
c4_level: Component
created: 2025-10-20
last_updated: 2025-10-20
status: active
---

## Title

Analytics, User Preferences & Notification System Architecture

## Description

Detailed architecture for the Basic Intelligence, Personal Preferences & Settings, and Real-Time Notification features added to the MVP scope.

## Analytics Module

### Purpose
Provide simple, actionable metrics on task completion and staff workload without complex data warehouse infrastructure.

### Key Metrics
1. **Task Completion Analytics**
   - On-time vs delayed tasks by property
   - Task completion rates by category (cleaning, maintenance, service, compliance)
   - Average time to completion
   - Overdue task counts

2. **Staff Workload Visibility**
   - Active tasks per staff member
   - Completion history and performance
   - Workload distribution across team

3. **Property Performance**
   - Property-level task metrics
   - Cross-property comparisons
   - Trend analysis (daily, weekly, monthly)

### Implementation Approach

**Data Storage**
- All analytics computed from existing Task and User tables
- Optional: TaskAnalytics table for pre-computed aggregates (updated nightly)
- No separate analytics database in MVP

**API Design**
```typescript
// Example API endpoints
GET /api/analytics/tasks
  ?propertyId=<id>
  &startDate=<date>
  &endDate=<date>
  &groupBy=day|week|month

GET /api/analytics/staff-workload
  ?propertyId=<id>
  &userId=<id>

GET /api/analytics/property-comparison
  ?propertyIds[]=<id1>&propertyIds[]=<id2>
```

**Performance Considerations**
- Database indexes on: taskId, userId, propertyId, status, completedAt
- Cache frequently accessed metrics (Redis in production)
- Limit date ranges to prevent expensive queries
- Paginate results for large datasets

## User Preferences System

### Purpose
Store and manage personalized user settings for notifications, UI customization, and task management preferences.

### Preference Categories

**1. Notification Preferences**
- Channel selection: email, push, in-app
- Frequency: instant, digest (hourly/daily), custom schedule
- Quiet hours: start/end times in user's timezone
- Do-not-disturb toggle
- Mention alerts: @username notifications

**2. UI Preferences**
- Task view mode: list, kanban, calendar
- Theme: light, dark, system
- Language: ISO 639-1 code
- Timezone: IANA timezone identifier

**3. Task Filters & Views**
- Default filters (status, priority, category, property)
- Saved custom views with names and filter combinations

### Data Model

**UserPreferences Table**
```prisma
model UserPreferences {
  id        String   @id @default(cuid())
  userId    String   @unique
  user      User     @relation(fields: [userId], references: [id])
  
  // Notification Settings
  notificationEmail     Boolean  @default(true)
  notificationPush      Boolean  @default(true)
  notificationInApp     Boolean  @default(true)
  notificationFrequency String   @default("instant") // instant, digest, custom
  customSchedule        String?  // cron expression
  quietHoursEnabled     Boolean  @default(false)
  quietHoursStart       String?  // HH:MM format
  quietHoursEnd         String?  // HH:MM format
  doNotDisturb          Boolean  @default(false)
  mentionAlerts         Boolean  @default(true)
  
  // UI Settings
  taskViewMode          String   @default("list") // list, kanban, calendar
  theme                 String   @default("system") // light, dark, system
  language              String   @default("en")
  timezone              String   @default("America/New_York")
  
  // Filter Settings (stored as JSON)
  defaultFilters        Json?
  savedViews            Json?
  
  createdAt             DateTime @default(now())
  updatedAt             DateTime @updatedAt
}
```

### API Design

```typescript
// Get user preferences
GET /api/users/me/preferences

// Update user preferences (partial update)
PATCH /api/users/me/preferences
{
  "notificationPush": false,
  "quietHoursEnabled": true,
  "quietHoursStart": "22:00",
  "quietHoursEnd": "08:00"
}

// Reset preferences to default
POST /api/users/me/preferences/reset
```

### Real-Time Synchronization
- Preference changes broadcast via SSE to all active user sessions
- Ensures consistent experience across web and mobile
- Event format: `{ type: 'preferences_updated', data: { userId, preferences } }`

## Notification System

### Purpose
Multi-channel notification delivery system that respects user preferences and provides in-app notification management.

### Notification Types
1. **Task Assigned**: New task assigned to user
2. **Task Overdue**: Task passed due date
3. **Mention**: User @mentioned in task comment
4. **Comment**: New comment on user's task
5. **Feedback**: Guest feedback linked to user's task

### Notification Priority Levels
- **Urgent**: Critical issues requiring immediate attention (health/safety)
- **High**: Time-sensitive tasks (guest complaints, overdue tasks)
- **Medium**: Standard task assignments and updates
- **Low**: Informational notifications (task completed, training available)

### Data Model

**Notification Table**
```prisma
model Notification {
  id          String    @id @default(cuid())
  userId      String
  user        User      @relation(fields: [userId], references: [id])
  taskId      String?
  task        Task?     @relation(fields: [taskId], references: [id])
  
  type        String    // task_assigned, task_overdue, mention, comment, feedback
  priority    String    // low, medium, high, urgent
  title       String
  message     String
  
  read        Boolean   @default(false)
  dismissed   Boolean   @default(false)
  
  deliveredAt DateTime  @default(now())
  readAt      DateTime?
  
  channels    String[]  // which channels it was delivered on: ['email', 'push', 'inApp']
  
  createdAt   DateTime  @default(now())
  
  @@index([userId, read])
  @@index([userId, createdAt])
}
```

### Notification Flow

**1. Event Trigger**
```typescript
// Example: Task assigned
await createNotification({
  userId: task.assignedToId,
  taskId: task.id,
  type: 'task_assigned',
  priority: task.priority === 'urgent' ? 'high' : 'medium',
  title: 'New Task Assigned',
  message: `You've been assigned: ${task.title}`
});
```

**2. User Preference Check**
```typescript
async function shouldNotify(userId: string, channel: string): Promise<boolean> {
  const prefs = await getUserPreferences(userId);
  
  // Check if channel is enabled
  if (channel === 'email' && !prefs.notificationEmail) return false;
  if (channel === 'push' && !prefs.notificationPush) return false;
  
  // Check quiet hours
  if (prefs.quietHoursEnabled && isInQuietHours(prefs)) return false;
  
  // Check do-not-disturb
  if (prefs.doNotDisturb) return false;
  
  return true;
}
```

**3. Multi-Channel Delivery**
```typescript
async function deliverNotification(notification: Notification, userId: string) {
  const channels: string[] = [];
  
  // In-app (always delivered if notification created)
  await broadcastSSE(userId, {
    type: 'notification',
    data: notification
  });
  channels.push('inApp');
  
  // Email (if enabled and within hours)
  if (await shouldNotify(userId, 'email')) {
    await sendEmail({
      to: user.email,
      subject: notification.title,
      body: notification.message
    });
    channels.push('email');
  }
  
  // Push (if enabled and browser supports it)
  if (await shouldNotify(userId, 'push')) {
    await sendBrowserPush(userId, {
      title: notification.title,
      body: notification.message,
      data: { notificationId: notification.id }
    });
    channels.push('push');
  }
  
  // Update notification record with delivery channels
  await updateNotification(notification.id, { channels });
}
```

### In-App Notification Center

**UI Components**
- Bell icon with unread count badge
- Dropdown/panel showing recent notifications
- Mark as read/unread actions
- Dismiss action (hides notification)
- Link to full notification history page
- Filter by type, priority, read status

**API Endpoints**
```typescript
// Get notifications (paginated)
GET /api/notifications
  ?page=1
  &limit=20
  &read=false
  &type=task_assigned

// Mark as read
PATCH /api/notifications/:id/read

// Mark all as read
POST /api/notifications/mark-all-read

// Dismiss notification
PATCH /api/notifications/:id/dismiss

// Delete notification
DELETE /api/notifications/:id
```

**Real-Time Updates**
- SSE broadcasts new notifications to active sessions
- Updates unread count in real-time
- Plays sound/shows browser notification (if permitted)

### Browser Push Notifications

**Implementation**
```typescript
// Request permission
async function requestNotificationPermission() {
  if ('Notification' in window) {
    const permission = await Notification.requestPermission();
    return permission === 'granted';
  }
  return false;
}

// Send notification
async function sendBrowserPush(userId: string, payload: NotificationPayload) {
  // Check if user has active sessions with permission
  const sessions = await getActiveSessions(userId);
  
  for (const session of sessions) {
    if (session.notificationPermission === 'granted') {
      // Send via SSE to trigger browser notification on client
      await broadcastSSE(userId, {
        type: 'push_notification',
        data: payload
      });
    }
  }
}
```

**Client-Side Handling**
```typescript
// Listen for SSE push notification events
sse.addEventListener('push_notification', (event) => {
  const data = JSON.parse(event.data);
  
  new Notification(data.title, {
    body: data.body,
    icon: '/app-icon.png',
    badge: '/badge-icon.png',
    tag: data.notificationId,
    requireInteraction: data.priority === 'urgent'
  });
});
```

## Email Notifications

### SMTP Configuration
- Use standard SMTP for MVP
- Environment variables: SMTP_HOST, SMTP_PORT, SMTP_USER, SMTP_PASS
- Support for TLS/SSL

### Email Templates
- HTML templates for professional appearance
- Include task details, direct links to app
- Unsubscribe link (updates user preferences)
- Responsive design for mobile

### Digest Mode
- Batch notifications if user selects digest mode
- Cron job runs hourly/daily based on user preference
- Single email with list of all pending notifications
- Option to "mark all as read" from email

## Performance & Scalability

### Database Indexing
```sql
-- Notifications
CREATE INDEX idx_notifications_user_read ON notifications(user_id, read);
CREATE INDEX idx_notifications_user_created ON notifications(user_id, created_at DESC);

-- User Preferences
CREATE UNIQUE INDEX idx_user_preferences_user ON user_preferences(user_id);

-- Task Analytics (if using separate table)
CREATE INDEX idx_analytics_property_period ON task_analytics(property_id, period_start, period_end);
CREATE INDEX idx_analytics_user_period ON task_analytics(user_id, period_start, period_end);
```

### Caching Strategy
- Cache user preferences in Redis (TTL: 1 hour)
- Invalidate cache on preference update
- Cache aggregated analytics (TTL: 5 minutes)

### Notification Cleanup
- Archive notifications older than 90 days
- Cron job runs nightly to archive/delete old notifications
- Keep unread notifications indefinitely

## Testing Considerations

### Unit Tests
- User preference CRUD operations
- Notification creation and delivery logic
- Quiet hours calculation
- Analytics aggregation functions

### Integration Tests
- SSE notification delivery
- Email sending
- Browser push notification flow
- Preference synchronization across sessions

### User Acceptance Tests
- Complete notification workflow (create task → notification → delivery)
- Preference changes reflect immediately
- Analytics dashboard accuracy
- Email digest delivery
