# Icon System - Taskii Design System

## Icon Philosophy

### Hospitality-Focused Iconography
Icons should immediately communicate meaning within the context of hotel and travel operations. Each icon serves the operational reality of hospitality staff who need to understand functionality at a glance.

### Consistency Standards
- **Style**: Outlined icons for primary navigation, filled icons for status/completion
- **Weight**: 2px stroke weight for optimal mobile visibility
- **Size**: 24px base size, scalable to 16px, 32px, 48px
- **Grid**: Based on 24px × 24px artboard with 2px padding

## Core Icon Categories

### Navigation Icons

**Dashboard**
- Icon: Grid of squares (represents multiple properties/overview)
- Usage: Main dashboard navigation
- Alt: Overview grid icon

**Tasks** 
- Icon: Checklist with checkmarks
- Usage: Task management section
- Alt: Task checklist icon

**Properties**
- Icon: Building/hotel outline
- Usage: Property selection and management
- Alt: Hotel building icon

**Staff**
- Icon: Multiple person silhouettes
- Usage: Staff management and assignment
- Alt: Staff team icon

**Analytics**
- Icon: Bar chart with upward trend
- Usage: Performance analytics and reporting
- Alt: Analytics chart icon

**Training**
- Icon: Graduation cap or book with person
- Usage: Training materials and certification
- Alt: Training education icon

**Settings**
- Icon: Gear/cog wheel
- Usage: App settings and preferences
- Alt: Settings gear icon

### Task Type Icons

**Housekeeping**
- Icon: Vacuum cleaner or bed with pillows
- Color: Soft blue (#3B82F6)
- Usage: Room cleaning, maintenance tasks

**Guest Service**
- Icon: Person with speech bubble or concierge bell
- Color: Hospitality gold (#F59E0B)
- Usage: Front desk, concierge, guest relations tasks

**Maintenance**
- Icon: Wrench and screwdriver crossed or toolbox
- Color: Orange (#EA580C)
- Usage: Repair, technical, facility tasks

**Food & Beverage**
- Icon: Plate and utensils or wine glass
- Color: Green (#10B981)
- Usage: Restaurant, room service, catering tasks

**Safety & Compliance**
- Icon: Shield with checkmark or clipboard with star
- Color: Red (#EF4444)
- Usage: Health inspections, safety protocols, compliance

**Training**
- Icon: Book with person or presentation screen
- Color: Purple (#8B5CF6)
- Usage: Staff development, certification tasks

### Status Icons

**Completed**
- Icon: Filled circle with checkmark
- Color: Success green (#10B981)
- Usage: Successfully finished tasks

**In Progress**
- Icon: Half-filled circle or rotating arrows
- Color: Info blue (#3B82F6)
- Usage: Currently being worked on

**Pending**
- Icon: Empty circle or clock
- Color: Gray (#6B7280)
- Usage: Not yet started tasks

**Overdue**
- Icon: Circle with exclamation mark or warning triangle
- Color: Error red (#EF4444)
- Usage: Past due date tasks

**Blocked**
- Icon: Octagon with X or barrier symbol
- Color: Warning amber (#F59E0B)
- Usage: Cannot proceed due to dependency

### Priority Icons

**High Priority**
- Icon: Upward arrow or exclamation mark in triangle
- Color: Error red (#EF4444)
- Usage: Urgent, immediate attention required

**Medium Priority**
- Icon: Horizontal line/dash or medium-height bar
- Color: Warning amber (#F59E0B)
- Usage: Important but not urgent

**Low Priority**
- Icon: Downward arrow or short bar
- Color: Gray (#6B7280)
- Usage: Can be done when time allows

### Action Icons

**Add/Create**
- Icon: Plus sign in circle
- Usage: Create new tasks, add items

**Edit**
- Icon: Pencil or edit pen
- Usage: Modify existing items

**Delete**
- Icon: Trash can or X
- Usage: Remove items (with confirmation)

**Assign**
- Icon: Person with arrow or user-plus
- Usage: Assign tasks to staff members

**Filter**
- Icon: Funnel or filter symbol
- Usage: Filter task lists and views

**Search**
- Icon: Magnifying glass
- Usage: Search functionality

**Refresh**
- Icon: Circular arrow or refresh symbol
- Usage: Update/reload content

**Upload**
- Icon: Cloud with upward arrow or folder with arrow
- Usage: Photo uploads, document attachments

**Download**
- Icon: Cloud with downward arrow or document with arrow
- Usage: Export reports, download files

### Communication Icons

**Notification**
- Icon: Bell (outline for inactive, filled for active)
- Usage: Alert indicators and notification center

**Message**
- Icon: Speech bubble or chat icon
- Usage: Communication, guest feedback, notes

**Phone**
- Icon: Phone handset or mobile device
- Usage: Contact information, call actions

**Email**
- Icon: Envelope (outline or filled)
- Usage: Email communications and notifications

### Guest Experience Icons

**Guest Feedback**
- Icon: Speech bubble with star or thumbs up/down
- Usage: Reviews, ratings, feedback management

**Service Recovery**
- Icon: Heart with plus sign or service bell with arrow
- Usage: Addressing guest complaints and issues

**VIP Guest**
- Icon: Crown or star badge
- Usage: Special guest designations

**Guest Request**
- Icon: Hand with star or service bell
- Usage: Special requests and accommodations

## Implementation Guidelines

### Icon Usage Rules

1. **Consistency**: Always use the same icon for the same concept across the app
2. **Context**: Icons should be immediately recognizable in their operational context
3. **Pairing**: Always pair icons with text labels for clarity
4. **Scalability**: Icons must remain legible at 16px minimum size
5. **Touch Targets**: Ensure 44px minimum touch target around interactive icons

### Color Application

**Default State**: Gray (#6B7280) for inactive/secondary icons
**Active State**: Brand blue (#2563EB) for selected/active icons
**Contextual**: Use category colors for task types and status indicators
**Accessibility**: Maintain 4.5:1 contrast ratio against backgrounds

### Responsive Behavior

**Mobile (≤480px)**
- 24px icon size standard
- Larger touch targets (44px minimum)
- Icons with labels in navigation

**Tablet (481-1023px)**
- 24px icons in navigation
- 20px icons in compact views
- Hover states for interactive icons

**Desktop (≥1024px)**
- 20px icons in dense interfaces
- 24px icons in primary navigation
- 16px icons in data tables and compact views

### Animation Guidelines

**Micro-interactions**
- Subtle scale (0.95x to 1x) on button press
- Color transitions for state changes (200ms ease)
- Rotation for refresh/loading states

**Status Changes**
- Checkmark animation for task completion
- Progress indicators for in-progress tasks
- Attention-grabbing pulse for urgent items

### Accessibility Considerations

**Screen Readers**
- Proper ARIA labels for all interactive icons
- Decorative icons marked as aria-hidden="true"
- Text alternatives that describe function, not appearance

**Visual Accessibility**
- High contrast variants for accessibility mode
- Shape differentiation beyond just color coding
- Consistent positioning for predictable navigation

**Motor Accessibility**
- Adequate spacing between adjacent icons
- Large enough touch targets for various abilities
- Alternative access methods for gesture-based icons