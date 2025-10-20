# Demo Flows - 1-Day POC

## Overview
This document outlines the detailed demonstration flows for the Taskii POC. Each flow shows the step-by-step user journey through key features.

**Demo Duration**: 10-15 minutes total
**Personas**: Property Manager (Sarah), Frontline Staff (Mike), Corporate Admin (Alex)

---

## Demo Flow 1: Guest Review → Automated Task Generation (Priority 1)

**Goal**: Show how guest feedback automatically translates into actionable tasks

**Persona**: Property Manager (Sarah)
**Duration**: 3-4 minutes

### Setup
- Pre-loaded guest reviews for "Downtown Hotel" property
- One negative review about "Room 305 - Bathroom cleanliness issue"

### Step-by-Step Flow

#### 1. View Guest Reviews Dashboard
**Screen**: Reviews Dashboard (`/reviews`)

**UI Elements**:
- List of recent guest reviews
- Each review shows:
  - Guest name (anonymized: "Guest J.S.")
  - Rating (1-5 stars)
  - Review text
  - Date submitted
  - Property name
  - Status badge (New, Task Created, Resolved)

**Demo Data**:
```
⭐⭐ Guest J.S. - 2 days ago - Downtown Hotel
"Room 305 had cleanliness issues in the bathroom. Hair in the shower
and the toilet wasn't properly cleaned. Otherwise nice stay."
[Status: New]
```

**Action**: Sarah clicks on the review to view details

---

#### 2. Review Detail View
**Screen**: Review Detail (`/reviews/:id`)

**UI Elements**:
- Full review text
- Guest information (anonymous)
- Property and room details
- Sentiment analysis indicator (🔴 Negative, 🟡 Neutral, 🟢 Positive)
- Key issues detected (highlighted): "cleanliness", "bathroom"
- Action buttons:
  - "Generate Task" (primary button)
  - "Mark as Acknowledged"
  - "Contact Guest" (disabled for POC)

**Action**: Sarah clicks "Generate Task"

---

#### 3. AI-Assisted Task Generation Modal
**Screen**: Modal overlay on Review Detail

**UI Elements**:
- Pre-filled form with AI-suggested values:
  - **Task Title**: "Deep clean Room 305 bathroom"
  - **Category**: Cleaning (auto-selected)
  - **Priority**: High (auto-selected based on review rating)
  - **Description**: "Guest reported cleanliness issues in Room 305 bathroom: hair in shower, toilet not properly cleaned. Perform deep clean and inspection."
  - **Assigned To**: (dropdown) - Housekeeping staff
  - **Due Date**: Today by 2:00 PM (auto-calculated)
  - **Linked Training**: "Bathroom Cleaning Protocol" (auto-attached)
  - **Property**: Downtown Hotel (auto-filled)
  - **Room**: 305 (auto-detected)

- Info banner: "Task details automatically generated from review analysis"
- Buttons: "Create Task", "Edit Details", "Cancel"

**Action**: Sarah reviews the pre-filled data and clicks "Create Task"

---

#### 4. Task Created Confirmation
**Screen**: Toast notification + redirect to Tasks view

**UI Elements**:
- Success toast: "✓ Task created and assigned to Mike Rodriguez"
- Review status updates to "Task Created"
- Task appears in Tasks dashboard

**Result**: Task is now visible to assigned staff member

---

## Demo Flow 2: Staff Task Completion with Training (Priority 1)

**Goal**: Show how staff complete tasks with embedded training

**Persona**: Frontline Staff (Mike Rodriguez - Housekeeping)
**Duration**: 3-4 minutes

### Setup
- Mike logs in (user switcher in UI)
- Task "Deep clean Room 305 bathroom" is assigned to him

### Step-by-Step Flow

#### 1. Staff Dashboard
**Screen**: Staff Dashboard (`/dashboard/staff`)

**UI Elements**:
- Welcome message: "Welcome back, Mike"
- Notification badge: "1 new task"
- Today's tasks section:
  - Pending tasks (3)
  - In Progress (1)
  - Completed today (2)
- Task list with cards showing:
  - Task title
  - Priority badge (High/Medium/Low)
  - Due time
  - Property/Location
  - Training required indicator (📚)

**Demo Data**:
```
🔴 HIGH PRIORITY
Deep clean Room 305 bathroom
Due: Today at 2:00 PM
Location: Downtown Hotel - Room 305
📚 Training required
[View Details]
```

**Action**: Mike clicks "View Details" on the high-priority task

---

#### 2. Task Detail View
**Screen**: Task Detail (`/tasks/:id`)

**UI Elements**:
- Task information:
  - Title: "Deep clean Room 305 bathroom"
  - Description (including context from guest review)
  - Priority: High
  - Due: Today 2:00 PM
  - Assigned to: Mike Rodriguez
  - Created by: Sarah (Property Manager)
  - Property: Downtown Hotel
  - Room: 305

- Linked Review section:
  - "This task was created from a guest review"
  - Preview of review snippet
  - Link to full review

- Required Training section:
  - ⚠️ Banner: "You must review training materials before completing this task"
  - Training module: "Bathroom Cleaning Protocol"
  - Status: Not Started
  - [View Training Material] button

- Task actions (disabled until training complete):
  - [Start Task] button (grayed out)
  - Status: Pending

**Action**: Mike clicks "View Training Material"

---

#### 3. Training Material View
**Screen**: Training Modal overlay

**UI Elements**:
- Modal title: "Bathroom Cleaning Protocol"
- Training content:
  - Video placeholder: "Deep Cleaning Best Practices (3:24)" with thumbnail
  - Checklist:
    ```
    ✓ Bathroom Deep Cleaning Checklist:
    □ Spray all surfaces with approved cleaner
    □ Clean toilet bowl, seat, and base thoroughly
    □ Scrub shower/tub, paying attention to corners
    □ Remove any hair from drains and surfaces
    □ Clean mirrors and fixtures
    □ Mop floor
    □ Restock amenities
    □ Final inspection
    ```
  - PDF link: "Full Cleaning Standards Guide.pdf"

- Completion confirmation:
  - Checkbox: "☑ I have reviewed this training material"
  - [Mark as Complete] button

**Action**: Mike reviews the content, checks the box, and clicks "Mark as Complete"

---

#### 4. Start and Complete Task
**Screen**: Task Detail (updated state)

**UI Elements**:
- Training section now shows: ✓ "Bathroom Cleaning Protocol - Completed"
- [Start Task] button now enabled

**Action**: Mike clicks "Start Task"

**UI Update**:
- Task status changes to "In Progress"
- Timer starts: "Started 1 minute ago"
- New section appears: "Task Completion"
  - Notes field (required): "Add completion notes..."
  - Photo upload (optional): "Attach photo" (can skip for POC)
  - [Complete Task] button

**Action**: Mike types in notes:
```
"Completed deep clean of Room 305 bathroom. Shower thoroughly scrubbed,
all hair removed from drains, toilet fully sanitized. Restocked amenities.
Room is ready for inspection."
```

**Action**: Mike clicks "Complete Task"

---

#### 5. Task Completion Confirmation
**Screen**: Toast notification + Dashboard redirect

**UI Elements**:
- Success toast: "✓ Task completed successfully"
- Notification sent to property manager
- Task moves to "Completed" section
- Completion timestamp recorded
- Stats update: "Completed today: 3"

---

## Demo Flow 3: Multi-Property Dashboard & Analytics (Priority 1)

**Goal**: Show portfolio-level visibility and task analytics

**Persona**: Property Manager (Sarah) or Corporate Admin (Alex)
**Duration**: 2-3 minutes

### Step-by-Step Flow

#### 1. Portfolio Dashboard
**Screen**: Main Dashboard (`/dashboard`)

**UI Elements**:
- Property Selector (top nav):
  - Dropdown: "All Properties" | "Downtown Hotel" | "Seaside Resort" | "Airport Inn"
  - Currently: "All Properties"

- Summary Cards (top row):
  ```
  [Total Tasks Today]     [Completed]        [Overdue]         [Staff Active]
        24                   18                 3                  12
  ```

- Property Performance Table:
  ```
  Property          Active Tasks    Completed Today    Overdue    Avg Completion
  Downtown Hotel         8                6              1         2.3 hours
  Seaside Resort        10                8              2         3.1 hours
  Airport Inn            6                4              0         1.8 hours
  ```

- Task Distribution Chart:
  - Pie chart showing tasks by category:
    - Cleaning: 45%
    - Maintenance: 25%
    - Guest Service: 20%
    - Compliance: 10%

- Recent Activity Feed:
  ```
  2 minutes ago    Mike Rodriguez completed "Deep clean Room 305 bathroom"
  15 minutes ago   Sarah Chen assigned task to Mike Rodriguez
  23 minutes ago   New review received for Downtown Hotel (⭐⭐ 2 stars)
  1 hour ago       Lisa Park completed "Fix TV in Room 201"
  ```

**Action**: Sarah clicks "Downtown Hotel" in the property selector

---

#### 2. Single Property View
**Screen**: Dashboard filtered to Downtown Hotel

**UI Elements**:
- Property name in header: "Downtown Hotel"
- Filtered summary cards:
  ```
  [Active Tasks]     [Completed Today]    [Overdue]    [Staff on Duty]
        8                   6                 1              4
  ```

- Tasks by Status:
  - Pending: 4 tasks
  - In Progress: 3 tasks
  - Completed Today: 6 tasks
  - Overdue: 1 task

- Staff Workload (for this property):
  ```
  Staff Member        Active Tasks    Completed Today    Status
  Mike Rodriguez           2                1            On Duty
  Lisa Park                1                2            On Duty
  James Chen               3                1            On Duty
  Maria Garcia             2                2            On Duty
  ```

- Quick Actions:
  - [Create New Task]
  - [View All Reviews]
  - [Generate Report]

**Action**: Sarah clicks on "Overdue: 1 task" to see details

---

#### 3. Filtered Task List
**Screen**: Tasks view with filter applied

**UI Elements**:
- Filter badges: "Property: Downtown Hotel" × "Status: Overdue" ×
- One overdue task shown:
  ```
  🔴 OVERDUE (Due: Yesterday 5:00 PM)
  Replace broken towel rack - Room 412
  Assigned to: James Chen
  Category: Maintenance
  Created: 3 days ago
  [View Details] [Reassign]
  ```

**Action**: Sarah clicks "Reassign" and selects different staff member

**Result**:
- Task reassigned successfully
- Notification sent to new assignee
- Overdue count updates

---

## Demo Flow 4: Notification System (Priority 2)

**Goal**: Show in-app notifications and preferences

**Persona**: Staff Member (Mike)
**Duration**: 2 minutes

### Step-by-Step Flow

#### 1. Notification Center
**Screen**: Any page with notification bell icon

**UI Elements**:
- Bell icon in top nav with badge: "🔔 3"
- Clicking bell opens dropdown:

```
Notifications (3 unread)

[Mark all as read]  [Settings]

🆕 2 minutes ago
Task completed: "Deep clean Room 305"
Marked as complete by Mike Rodriguez

🆕 15 minutes ago
New task assigned: "Deep clean Room 305 bathroom"
Due today at 2:00 PM
[View Task]

🆕 1 hour ago
Reminder: Task "Restock Room 201" is due in 1 hour
[View Task]

• 2 hours ago
Training completed: "Bathroom Cleaning Protocol"

• Yesterday
Task completed: "Fix TV in Room 201"
```

**Action**: Mike clicks "Settings"

---

#### 2. Notification Preferences
**Screen**: Settings Modal (`/settings/notifications`)

**UI Elements**:
- Simple preference toggles:

```
Notification Preferences

Task Assignments
☑ Notify me when tasks are assigned to me
☑ Show in-app notifications
☐ Send email notifications (future)

Task Reminders
☑ Remind me 1 hour before due time
☑ Remind me when task is overdue
Reminder time: [1 hour before ▼]

Task Updates
☑ Notify when my completed tasks are reviewed
☐ Notify when tasks are reassigned

Training
☑ Notify when new training is available
☑ Remind me about required training

[Save Preferences]  [Cancel]
```

**Action**: Mike toggles off "Remind me when task is overdue" and clicks "Save Preferences"

**Result**: Settings saved, toast confirmation shown

---

## Demo Flow 5: Creating Manual Task (Priority 2)

**Goal**: Show property manager creating ad-hoc tasks

**Persona**: Property Manager (Sarah)
**Duration**: 2 minutes

### Step-by-Step Flow

#### 1. Create Task Form
**Screen**: Create Task (`/tasks/new`)

**UI Elements**:
- Form fields:
  - **Property**: [Dropdown: Downtown Hotel ▼]
  - **Title**: [Text input: required]
  - **Category**: [Dropdown: Cleaning | Maintenance | Guest Service | Compliance]
  - **Priority**: [Radio: 🔴 High | 🟡 Medium | 🟢 Low]
  - **Description**: [Textarea: optional]
  - **Assign To**: [Dropdown: Select staff member ▼]
  - **Due Date**: [Date picker]
  - **Due Time**: [Time picker]
  - **Location/Room**: [Text input: optional]
  - **Attach Training**: [Dropdown: Select training material (optional) ▼]
  - **Recurring**: [Checkbox] Set as recurring task (disabled for POC)

- Buttons:
  - [Create Task] (primary)
  - [Save as Draft] (secondary)
  - [Cancel]

**Demo Action**: Sarah fills in:
```
Property: Seaside Resort
Title: Deep clean lobby restrooms
Category: Cleaning
Priority: High
Description: Pre-weekend deep clean before busy check-in period
Assign To: Maria Garcia
Due Date: Tomorrow
Due Time: 10:00 AM
Location: Lobby - Public Restrooms
Attach Training: Public Area Cleaning Standards
```

**Action**: Sarah clicks "Create Task"

---

#### 2. Task Created Confirmation
**Screen**: Redirect to Tasks list

**UI Elements**:
- Success toast: "✓ Task created and assigned to Maria Garcia"
- New task appears at top of list
- Notification sent to Maria
- Task shows in property dashboard

---

## Demo Flow 6: Service Recovery Workflow (Priority 1)

**Goal**: Show complete guest complaint resolution cycle

**Persona**: Multiple (Sarah → Mike → Sarah)
**Duration**: 2-3 minutes (quick walkthrough showing connected flow)

### Complete Workflow Overview

#### Stage 1: Complaint Received
**Screen**: Reviews Dashboard
- Negative review appears: ⭐⭐ "Room service was slow, waited 90 minutes"
- Property: Airport Inn
- Status: New

#### Stage 2: Task Generated
**Screen**: Review Detail → Generate Task
- Auto-generated task: "Follow up with guest about room service delay"
- Category: Guest Service
- Priority: High
- Assigned to: Sarah (Property Manager)
- Due: Today (same day)
- Training attached: "Service Recovery Best Practices"

#### Stage 3: Investigation Task
**Screen**: Sarah's view
- Sarah completes training
- Sarah adds note: "Investigated - kitchen understaffed during dinner rush"
- Sarah creates follow-up task: "Contact guest to apologize and offer compensation"
- Sarah creates operational task: "Review staffing levels for dinner service"

#### Stage 4: Guest Follow-up
**Screen**: Task completion
- Follow-up task shows linked review
- Template response available: "Guest service recovery script"
- Compensation tracked: "50% discount on next stay"
- Status: Resolved

#### Stage 5: Analytics
**Screen**: Dashboard
- Service recovery metrics:
  - Response time: 2 hours
  - Resolution time: 4 hours
  - Guest contacted: Yes
  - Status: Closed
- Task feeds into performance dashboard

---

## Supporting Screens & Features

### User Switcher (POC Only)
**Location**: Top-right corner of nav bar

**UI**: Dropdown menu
```
Current User: Sarah Chen (Property Manager) ▼

Switch User:
• Alex Johnson - Corporate Admin
• Sarah Chen - Property Manager ✓
• Mike Rodriguez - Housekeeping Staff
• Lisa Park - Maintenance Staff
• James Chen - Front Desk
• Maria Garcia - Housekeeping Staff
```

**Purpose**: Demo different role perspectives without real authentication

---

### Navigation Structure

**Top Navigation**:
```
[Taskii Logo]  Dashboard  Tasks  Reviews  Properties  [🔔 3]  [Sarah Chen ▼]
```

**Role-Based Navigation**:

**Corporate Admin**:
- Dashboard (All properties overview)
- Properties (Manage properties)
- Tasks (All tasks across properties)
- Reviews (All reviews)
- Analytics (Deep dive)
- Settings

**Property Manager**:
- Dashboard (Property overview)
- Tasks (Create, assign, view)
- Reviews (View and respond)
- Staff (View team)
- Settings

**Staff**:
- My Tasks (Focus view)
- Dashboard (Simple overview)
- Training (My training materials)
- Settings

---

## Data Model for Demo

### Properties
```javascript
[
  {
    id: 1,
    name: "Downtown Hotel",
    location: "123 Main St, Downtown",
    rooms: 120,
    activeStaff: 15
  },
  {
    id: 2,
    name: "Seaside Resort",
    location: "456 Beach Blvd, Coastal Area",
    rooms: 200,
    activeStaff: 25
  },
  {
    id: 3,
    name: "Airport Inn",
    location: "789 Airport Dr, Terminal Area",
    rooms: 80,
    activeStaff: 10
  }
]
```

### Users
```javascript
[
  {
    id: 1,
    name: "Alex Johnson",
    role: "admin",
    email: "alex@taskii.com",
    properties: [1, 2, 3]
  },
  {
    id: 2,
    name: "Sarah Chen",
    role: "manager",
    email: "sarah@taskii.com",
    properties: [1, 3]
  },
  {
    id: 3,
    name: "Mike Rodriguez",
    role: "staff",
    department: "Housekeeping",
    email: "mike@taskii.com",
    property: 1
  },
  // ... more staff
]
```

### Tasks
```javascript
[
  {
    id: 1,
    title: "Deep clean Room 305 bathroom",
    description: "Guest reported cleanliness issues...",
    category: "cleaning",
    priority: "high",
    status: "pending",
    assignedTo: 3,
    createdBy: 2,
    property: 1,
    room: "305",
    dueDate: "2025-10-20T14:00:00Z",
    trainingRequired: [1],
    linkedReview: 1,
    createdAt: "2025-10-20T10:15:00Z"
  },
  // ... more tasks
]
```

### Reviews
```javascript
[
  {
    id: 1,
    guestName: "Guest J.S.",
    rating: 2,
    reviewText: "Room 305 had cleanliness issues...",
    property: 1,
    room: "305",
    date: "2025-10-18T16:30:00Z",
    status: "task_created",
    sentiment: "negative",
    taskId: 1
  },
  // ... more reviews
]
```

### Training Materials
```javascript
[
  {
    id: 1,
    title: "Bathroom Cleaning Protocol",
    category: "cleaning",
    type: "video",
    url: "/training/bathroom-cleaning.mp4",
    duration: "3:24",
    checklist: [...],
    pdfUrl: "/training/cleaning-standards.pdf"
  },
  // ... more training
]
```

---

## Demo Script Summary

**Total Demo Time**: ~15 minutes

### Act 1: The Problem (2 min)
1. Show review dashboard with negative review
2. Explain manual process pain point
3. Click "Generate Task" to show automation

### Act 2: Intelligence (3 min)
4. Show AI-generated task details
5. Highlight auto-filled fields, priority, training
6. Create task

### Act 3: Execution (4 min)
7. Switch to staff user (Mike)
8. View assigned task
9. Complete required training
10. Start and complete task with notes

### Act 4: Insights (3 min)
11. Switch back to manager
12. Show multi-property dashboard
13. Review analytics and metrics
14. Filter by property

### Act 5: Extras (3 min)
15. Show notification center
16. Update notification preferences
17. Create manual task
18. Quick tour of service recovery workflow

### Closing (1 min)
- Recap key features
- Highlight extensibility (future features)
- Q&A

---

## Technical Requirements for Demo

### Database Seed Data Needed
- 3 properties
- 6 users (1 admin, 2 managers, 3 staff)
- 10-15 tasks (mix of pending, in progress, completed, overdue)
- 5-7 guest reviews
- 3-5 training materials
- 5-10 notifications

### Key UI States to Build
- Empty states ("No tasks yet")
- Loading states (spinners/skeletons)
- Success states (toast notifications)
- Error states (form validation)
- Filtered states (tasks by status, property)

### Critical User Flows to Test
1. Review → Task generation → Assignment
2. Staff task completion with training
3. Property switching and filtering
4. Notification viewing and preferences
5. Manual task creation

---

## Success Metrics

**Demo is successful if**:
- ✅ All 6 main flows complete without errors
- ✅ Transitions between users/roles are smooth
- ✅ Data updates are visible in real-time (or with refresh)
- ✅ UI is clean and professional (doesn't need polish)
- ✅ Audience understands the value proposition
- ✅ Core automation concept is clear

**Demo fails if**:
- ❌ Critical flows crash or error
- ❌ Data doesn't persist or update
- ❌ UI is too confusing to follow
- ❌ Value proposition is unclear
