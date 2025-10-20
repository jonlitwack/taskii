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
**Usage**: Dense list views, mobile overview
```
Reduced padding: 12px
Single line layout for mobile
Priority dot instead of border
Truncated text with expansion on tap
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
User menu: Right aligned
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
```

#### Sidebar Navigation (Desktop)
```
Width: 240px (collapsed: 64px)
Background: Light gray (#F9FAFB)
Collapsible with hamburger menu
Nested menu support for property selection
```

#### Breadcrumbs
```
Typography: Body Small (12px)
Separator: "/" or chevron icon
Max 3 levels on mobile
Truncation: "..." for overflow
Color: Gray (#6B7280) with blue active item
```

### Data Display

#### Property Selector
```
Dropdown with search functionality
Property avatars/logos
Current property highlighted
Recent properties at top
Alphabetical sorting option
```

#### Status Badges
```
Border Radius: 16px (pill shape)
Padding: 4px 12px
Typography: Label Medium (12px, Medium, All Caps)
Colors match status (Success Green, Warning Amber, etc.)
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
```

### Modals and Overlays

#### Modal Dialog
```
Background: White with rounded corners (12px)
Max-width: 90vw (mobile), 500px (desktop)
Backdrop: Semi-transparent black (rgba(0, 0, 0, 0.5))
Animation: Slide up from bottom (mobile), fade + scale (desktop)
Close: X icon (top right) + backdrop click
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
Auto-dismiss: 4 seconds (info), 6 seconds (error)
Action button support
Stack multiple notifications
Swipe-to-dismiss (mobile)
```

### Loading States

#### Skeleton Loading
```
Animated shimmer effect
Matches content structure
Gray gradient animation
Maintains layout during loading
```

#### Spinner
```
Blue color matching brand
Multiple sizes: 16px, 24px, 32px
Center-aligned in containers
Smooth rotation animation
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

### Adaptive Layouts
- Single column (mobile) → Multi-column (tablet/desktop)
- Bottom navigation (mobile) → Sidebar (desktop)
- Full-screen modals (mobile) → Centered modals (desktop)
- Stacked forms (mobile) → Multi-column forms (desktop)