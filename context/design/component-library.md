# Component Library - Taskii Design System

## Core Components

### Buttons

#### Primary Button
**Usage**: Main actions, task completion, form submission
```
Background: Taskii Blue (#2563EB)
Text: White (#FFFFFF)
Border Radius: 8px
Padding: 12px 24px (mobile), 10px 20px (desktop)
Font: Label Large (14px, Medium)
Hover: Darker blue (#1D4ED8)
Focus: Blue outline + darker background
Disabled: Gray background (#D1D5DB), gray text (#9CA3AF)
```

#### Secondary Button
**Usage**: Secondary actions, cancel operations
```
Background: Transparent
Text: Taskii Blue (#2563EB)
Border: 1px solid Taskii Blue
Border Radius: 8px
Padding: 12px 24px (mobile), 10px 20px (desktop)
Hover: Light blue background (#EFF6FF)
Focus: Blue outline
```

#### Tertiary Button
**Usage**: Subtle actions, inline operations
```
Background: Transparent
Text: Gray (#374151)
Border: None
Padding: 8px 16px
Hover: Light gray background (#F3F4F6)
Underline on hover for text-only variants
```

#### Floating Action Button (FAB)
**Usage**: Primary mobile action (Add Task)
```
Background: Taskii Blue (#2563EB)
Size: 56px × 56px
Border Radius: 50%
Icon: White plus icon
Shadow: 0 4px 12px rgba(37, 99, 235, 0.3)
Position: Fixed bottom-right, 16px from edges
```

### Task Cards

#### Standard Task Card
**Usage**: Individual task display in lists and grids
```
Background: White (#FFFFFF)
Border: 1px solid Light Gray (#E5E7EB)
Border Radius: 12px
Padding: 16px
Shadow: 0 1px 3px rgba(0, 0, 0, 0.1)
Hover: Subtle shadow increase
```

**Card Structure**:
- Priority indicator (colored left border, 4px width)
- Task title (Heading 3)
- Property name/location (Body Medium, Gray)
- Due date (Label Medium, contextual color)
- Assignee avatar + name (Body Small)
- Status badge (bottom right)

#### Compact Task Card
**Usage**: Dense list views, mobile overview, user preference for information density
```
Reduced padding: 12px
Single line layout for mobile
Priority dot instead of border
Truncated text with expansion on tap
Preference-based: Adapts to user's density preference
```

#### Urgent Task Card
**Usage**: High-priority, overdue tasks
```
Border: 2px solid Error Red (#EF4444)
Background: Light red tint (#FEF2F2)
Animated pulse effect for overdue items
Bold priority indicator
```

### Forms

#### Input Field
```
Background: White (#FFFFFF)
Border: 1px solid Gray (#D1D5DB)
Border Radius: 8px
Padding: 12px 16px
Font: Body Large (16px) - prevents zoom on iOS
Focus: Blue border (#2563EB), blue outline
Error: Red border (#EF4444), red helper text
User Preference: Adapts to font size preference
```

#### Text Area
```
Extends Input Field styling
Min-height: 80px
Resize: Vertical only
Auto-expand for mobile (up to 200px max)
```

#### Select Dropdown
```
Styled consistently with Input Field
Down arrow icon (right aligned)
Native dropdown on mobile for better UX
Custom styled dropdown on desktop
```

#### Checkbox
```
Size: 20px × 20px
Border: 2px solid Gray (#D1D5DB)
Border Radius: 4px
Checked: Blue background (#2563EB), white checkmark
Focus: Blue outline
Larger touch target: 44px × 44px minimum
```

#### Radio Button
```
Size: 20px × 20px
Border: 2px solid Gray (#D1D5DB)
Border Radius: 50%
Selected: Blue border + inner blue dot
Focus: Blue outline
```

### Navigation

#### Top Navigation Bar
```
Background: White (#FFFFFF)
Height: 64px (mobile), 72px (desktop)
Border bottom: 1px solid Light Gray (#E5E7EB)
Logo: Left aligned
User menu: Right aligned (includes preference settings)
Search: Center (desktop only)
```

#### Bottom Navigation (Mobile)
```
Background: White (#FFFFFF)
Height: 80px (includes safe area)
Border top: 1px solid Light Gray (#E5E7EB)
4-5 primary navigation items
Icon + label below
Active state: Blue icon + text
Badge support: Notification indicators based on user preferences
```

#### Sidebar Navigation (Desktop)
```
Width: 240px (collapsed: 64px)
Background: Light gray (#F9FAFB) or adapts to theme preference
Collapsible with hamburger menu
Nested menu support for property selection
User preference: Remember collapsed/expanded state
```

#### Breadcrumbs
```
Typography: Body Small (12px)
Separator: "/" or chevron icon
Max 3 levels on mobile
Truncation: "..." for overflow
Color: Gray (#6B7280) with blue active item
```

### Notification Components

#### Notification Banner
```
Position: Top of interface, below navigation
Height: Variable (40-60px based on content)
Background: Priority-based colors (see Color System)
Border Radius: 8px (when not full-width)
Padding: 12px 16px
Dismissible: X icon (respects user preference for auto-dismiss)
Actions: 1-2 action buttons based on notification type
```

#### Notification Center
```
Panel: Slides from right (desktop) or full-screen (mobile)
Header: "Notifications" with filter options
Grouping: By type, priority, or time (user preference)
Mark as Read: Individual and bulk actions
Settings Link: Direct access to notification preferences
```

#### Push Notification Preview
```
Shows how notifications appear on user's device
Respects platform conventions (iOS, Android, Desktop)
Preview includes: Icon, title, body, action buttons
User can test notification appearance
```

### User Preference Components

#### Preference Settings Panel
```
Layout: Organized sections with clear headings
Notification Preferences: Channel selection, frequency, quiet hours
Display Preferences: Theme, font size, density
Task View Preferences: List/grid, sorting, filters
Language & Region: Timezone, language selection
```

#### Notification Frequency Selector
```
Options: Instant, Every 15 minutes, Hourly, Daily digest, Custom
Visual: Radio buttons with descriptions
Preview: Shows example of selected frequency
Smart Defaults: Based on user role and property type
```

#### Theme Selector
```
Options: Light, Dark, Auto (system), High Contrast
Preview: Live preview of interface changes
Persistence: Syncs across all user devices
Accessibility: Enhanced options for visual needs
```

### Data Display

#### Property Selector
```
Dropdown with search functionality
Property avatars/logos
Current property highlighted
Recent properties at top (based on user access patterns)
Favorites: User can mark frequently accessed properties
Alphabetical sorting option
```

#### Status Badges
```
Border Radius: 16px (pill shape)
Padding: 4px 12px
Typography: Label Medium (12px, Medium, All Caps)
Colors match status (Success Green, Warning Amber, etc.)
User Preference: Can customize which statuses to highlight
```

#### Progress Indicators
```
Circular: For task completion percentage
Linear: For overall property/portfolio progress
Animated transitions
Color-coded by performance (Green = good, Red = attention needed)
```

#### Avatar Component
```
Sizes: 24px, 32px, 40px, 56px
Border Radius: 50%
Fallback: Initials on colored background
Online indicator: Green dot (bottom right)
User Preference: Can hide online status for privacy
```

### Modals and Overlays

#### Modal Dialog
```
Background: White with rounded corners (12px)
Max-width: 90vw (mobile), 500px (desktop)
Backdrop: Semi-transparent black (rgba(0, 0, 0, 0.5))
Animation: Slide up from bottom (mobile), fade + scale (desktop)
Close: X icon (top right) + backdrop click + ESC key
```

#### Bottom Sheet (Mobile)
```
Slides up from bottom
Handle indicator at top
Backdrop dismissal
Supports partial and full-screen modes
Swipe-to-dismiss gesture
```

#### Toast Notifications
```
Position: Top center (mobile), top right (desktop)
Auto-dismiss: Based on user preference (2-8 seconds)
Action button support
Stack multiple notifications
Swipe-to-dismiss (mobile)
User Preference: Can disable auto-dismiss
```

### Loading States

#### Skeleton Loading
```
Animated shimmer effect
Matches content structure
Gray gradient animation
Maintains layout during loading
Respects user motion preferences
```

#### Spinner
```
Blue color matching brand
Multiple sizes: 16px, 24px, 32px
Center-aligned in containers
Smooth rotation animation
Respects reduced motion preferences
```

## Responsive Behavior

### Breakpoints
- **Mobile**: ≤480px
- **Tablet**: 481px - 1023px  
- **Desktop**: ≥1024px

### Touch Targets
- Minimum 44px × 44px for all interactive elements
- Increased spacing between adjacent interactive items
- Thumb-friendly positioning for primary actions

### User Preference Adaptations
- **Font Size**: All components scale with user's font size preference
- **Density**: Compact/comfortable/spacious layout options
- **Motion**: Respects reduced motion preferences
- **Contrast**: Enhanced contrast mode available

### Adaptive Layouts
- Single column (mobile) → Multi-column (tablet/desktop)
- Bottom navigation (mobile) → Sidebar (desktop)
- Full-screen modals (mobile) → Centered modals (desktop)
- Stacked forms (mobile) → Multi-column forms (desktop)

## Accessibility Features

### Screen Reader Support
- Semantic HTML structure
- ARIA labels and descriptions
- Live regions for dynamic content updates
- Skip links for keyboard navigation

### Keyboard Navigation
- Tab order follows logical flow
- Focus indicators clearly visible
- Keyboard shortcuts for common actions
- Escape key consistently closes overlays

### Visual Accessibility
- High contrast mode option
- Respects system font size preferences
- Color-blind friendly alternatives
- Reduced motion options for animations

### Motor Accessibility
- Large touch targets exceed minimums
- Voice control command support
- Alternative interaction methods
- Adjustable timing for interactions