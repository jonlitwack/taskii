# Integration Architecture

---
type: Architecture
c4_level: System
created: 2025-10-20
last_updated: 2025-10-20
status: active
---

## Title

Taskii Integration Architecture

## Description

External system integrations that feed data into the task orchestration platform.

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
- Email service for notifications (SMTP)
- Browser Push Notifications API for in-app alerts
- SSO providers (Azure AD, Okta, etc.)

## Notification Delivery Architecture

### Multi-Channel Notification Flow
1. **Event Trigger**: Task assignment, mention, deadline, etc.
2. **User Preference Check**: Query UserPreferences for delivery channels
3. **Quiet Hours Check**: Respect do-not-disturb and quiet hours settings
4. **Channel Delivery**:
   - **In-App**: Create Notification record + SSE broadcast to active sessions
   - **Email**: Queue email if user has email notifications enabled
   - **Push**: Send browser push notification if user has granted permission
5. **Delivery Tracking**: Record which channels were used and timestamps

### Preference Synchronization
- UserPreferences changes trigger SSE events to all user sessions
- Ensures consistent experience across web and mobile
- Changes persist immediately to PostgreSQL