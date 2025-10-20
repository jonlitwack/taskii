# User Experience Patterns - Taskii Design System

## Core UX Principles

### 1. Operational Efficiency
Every interaction should reduce friction in hospitality operations, not add complexity.

### 2. Context-Aware Design
The interface adapts based on user role, property type, time of day, and operational context.

### 3. Error Prevention
Design patterns that prevent common mistakes rather than just handling errors after they occur.

### 4. Progressive Training
Embed learning opportunities directly into workflows without disrupting operational tempo.

## Key User Flows

### Task Management Flow

#### Creating Tasks (Property Manager)
1. **Quick Add**: FAB → Task type selection → Auto-populated fields based on type
2. **Bulk Creation**: Template selection → Property/staff assignment → Batch creation
3. **Smart Suggestions**: AI-generated task recommendations based on recent guest feedback

#### Task Assignment Pattern
1. **Smart Assignment**: System suggests best-qualified staff member
2. **Manual Override**: Manager can reassign with reason tracking
3. **Workload Balancing**: Visual indicators show staff capacity before assignment

#### Task Completion (Frontline Staff)
1. **Task Discovery**: Push notification → App badge → Task list
2. **Execution Guidance**: Task details → Training materials (if needed) → Step-by-step guidance
3. **Completion Verification**: Photo upload → Notes → Status update → Optional peer review

### Multi-Property Navigation

#### Property Switching
- **Favorites**: Quick access to frequently managed properties
- **Recent**: Last 5 properties accessed
- **Search**: Type-ahead search by name or location
- **Portfolio View**: Switch to aggregated view across all properties

#### Context Preservation
- Maintain scroll position when switching between properties
- Remember filter/sort preferences per property
- Preserve task creation state when interruptions occur

### Guest Feedback Integration

#### Review Response Workflow
1. **Alert Reception**: Real-time notification of new negative review
2. **Impact Assessment**: Automatic categorization and urgency scoring
3. **Task Generation**: Suggested tasks for service recovery
4. **Assignment & Tracking**: Assign to appropriate staff with deadline
5. **Follow-up**: Automated reminder for guest follow-up communication

## Mobile-Specific Patterns

### Thumb-Driven Navigation
- **Bottom Navigation**: Primary app sections accessible with thumb
- **Swipe Actions**: Left swipe = complete task, right swipe = view details
- **Pull to Refresh**: Standard pattern for updating task lists
- **Floating Action Button**: Most common action (Add Task) always accessible

### Offline Capability
- **Task Sync**: Complete tasks offline, sync when connection restored
- **Visual Indicators**: Clear offline status indication
- **Conflict Resolution**: Handle sync conflicts gracefully with user choice
- **Essential Functions**: Critical features work without internet

### Mobile Forms
- **Single Column Layout**: All form fields stack vertically
- **Large Touch Targets**: Minimum 44px height for all inputs
- **Input Types**: Proper keyboard types (numeric, email, etc.)
- **Progressive Disclosure**: Show only essential fields initially

## Desktop Optimization

### Multi-Column Layouts
- **Dashboard**: 3-column layout for portfolio overview
- **Task Management**: Master-detail view with task list + detail panel
- **Forms**: Multi-column layout for efficient data entry

### Keyboard Navigation
- **Tab Order**: Logical tab sequence through interactive elements
- **Shortcuts**: Common actions accessible via keyboard (Ctrl+N = New Task)
- **Quick Actions**: Hover states reveal additional action options

## Notification System

### Notification Hierarchy
1. **Critical**: System failures, safety issues (immediate interruption)
2. **Urgent**: Overdue tasks, guest complaints (persistent banner)
3. **Important**: New assignments, deadlines (push notification)
4. **Informational**: Completion updates, training available (in-app badge)

### Delivery Channels
- **Push Notifications**: Mobile alerts for urgent items
- **In-App Banners**: Persistent display for ongoing issues
- **Email Digest**: Daily/weekly summaries for managers
- **SMS Backup**: Critical alerts if app notifications fail

### Notification Banner Pattern
```
Position: Top of screen, below navigation
Behavior: Persistent until dismissed or resolved
Actions: Primary action button + dismiss option
Styling: Color-coded by urgency level
Animation: Slide down entry, fade out dismissal
Stacking: Multiple banners stack with priority ordering
```

## Error Prevention Patterns

### Task Assignment Validation
- **Workload Check**: Warn if staff member already at capacity
- **Skill Verification**: Confirm staff has required training for task type
- **Schedule Conflicts**: Alert if assigned during staff member's time off
- **Location Logic**: Prevent assigning tasks to wrong property/area

### Form Validation
- **Real-time Feedback**: Validate fields as user types, not just on submit
- **Clear Error Messages**: Specific guidance on how to fix issues
- **Progressive Enhancement**: Basic functionality works even if JavaScript fails

### Data Loss Prevention
- **Auto-save**: Forms save progress automatically
- **Navigation Warnings**: Alert before leaving pages with unsaved changes
- **Session Recovery**: Restore form state after unexpected app closure

## Accessibility Patterns

### Screen Reader Support
- **Semantic HTML**: Proper heading hierarchy and landmark regions
- **ARIA Labels**: Descriptive labels for interactive elements
- **Status Updates**: Announce task completion and other state changes
- **Navigation Aid**: Skip links and keyboard shortcuts

### Visual Accessibility
- **High Contrast Mode**: Alternative color scheme for visual impairments
- **Text Scaling**: Support browser/system text size preferences
- **Focus Indicators**: Clear visual indication of keyboard focus
- **Color Independence**: Never rely on color alone to convey information

### Motor Accessibility
- **Large Touch Targets**: Exceed minimum size requirements
- **Gesture Alternatives**: Provide button alternatives to swipe gestures
- **Timing Flexibility**: Extend timeouts for slower interactions
- **Voice Control**: Support system voice navigation commands

## Performance Patterns

### Loading States
- **Skeleton Screens**: Show content structure while loading
- **Progressive Loading**: Display most important content first
- **Optimistic Updates**: Show changes immediately, handle failures gracefully
- **Background Sync**: Update data without interrupting user workflow

### Caching Strategy
- **Critical Path**: Cache essential screens for instant loading
- **Stale While Revalidate**: Show cached content while fetching updates
- **Offline Storage**: Store completed tasks locally until sync possible

## Training Integration Patterns

### Just-in-Time Learning
- **Contextual Help**: Training links appear when relevant to current task
- **Micro-Learning**: Bite-sized training modules (2-3 minutes max)
- **Progress tracking**: Visual indicators of training completion
- **Skill Verification**: Quick quizzes to confirm understanding

### Onboarding Flow
- **Role-Based Tours**: Different walkthroughs for different user types
- **Progressive Disclosure**: Introduce features gradually over first week
- **Success Metrics**: Track completion rates and time-to-productivity
- **Peer Support**: Connect new users with experienced mentors