# Layout and Grid System - Taskii Design System

## Grid Foundation

### Base Grid System
- **Columns**: 12-column grid system for flexibility
- **Gutters**: 16px (mobile), 24px (tablet), 32px (desktop)
- **Margins**: 16px (mobile), 24px (tablet), 32px (desktop)
- **Container Max-width**: 1200px (desktop)

### Responsive Breakpoints
- **Mobile**: 320px - 480px
- **Tablet**: 481px - 1023px
- **Desktop**: 1024px - 1200px+

## Layout Patterns

### Mobile Layout (≤480px)

#### Single Column Stack
- Full-width components stack vertically
- 16px margins on left/right
- 16px vertical spacing between components
- Priority-based content ordering

#### Task List Layout
```
[Header - 64px fixed]
[Filter Bar - 48px] 
[Task Cards - scrollable]
  - Card 1 (full width)
  - Card 2 (full width)
  - Card 3 (full width)
[Bottom Nav - 80px fixed]
```

#### Task Detail Layout
```
[Header with Back - 64px]
[Task Priority Banner - 40px]
[Task Content - scrollable]
  - Title section
  - Description
  - Assignment info
  - Due date
  - Attachments
[Action Button - 56px fixed]
```

### Tablet Layout (481px - 1023px)

#### Two-Column Hybrid
- Navigation sidebar: 240px (collapsible to 64px)
- Main content: Remaining width
- Cards display 2-up in available space
- Improved information density

#### Master-Detail Pattern
```
[Header - 72px]
[Content Area]
├── [Task List - 40%]
└── [Task Detail - 60%]
```

### Desktop Layout (≥1024px)

#### Three-Column Dashboard
```
[Header - 72px]
[Content Area]
├── [Sidebar - 240px]
├── [Main Content - flexible]
└── [Right Panel - 320px] (contextual)
```

#### Property Management Layout
```
[Top Navigation - 72px]
├── [Property Selector - 240px sidebar]
├── [Task Dashboard - main area]
│   ├── [Quick Stats - top row]
│   ├── [Task List - 60%]
│   └── [Activity Feed - 40%]
└── [Context Panel - 320px] (property details)
```

## Component Spacing

### Vertical Rhythm
- **Base Unit**: 8px
- **Component Spacing**: Multiples of 8px (8, 16, 24, 32, 48, 64)
- **Section Spacing**: 32px minimum between major sections
- **Card Spacing**: 16px between cards (mobile), 24px (desktop)

### Horizontal Spacing
- **Container Padding**: 16px (mobile), 24px (tablet), 32px (desktop)
- **Component Padding**: 16px internal padding for cards/containers
- **Element Spacing**: 8px between related elements, 16px between groups

## Card-Based Layouts

### Task Cards Grid
#### Mobile
- Single column, full width
- 16px margins, 16px gaps between cards
- Cards maintain minimum 80px height

#### Tablet
- 2-column grid with 24px gaps
- Cards adapt to available width
- Maintain aspect ratios

#### Desktop
- 3-4 column grid depending on container width
- 24px gaps between cards
- Fixed card width with flexible container

### List vs. Grid Toggle
- **List View**: Single column, compact height, more information visible
- **Grid View**: Multi-column, card-based, visual emphasis
- **User Preference**: Remember selection per user
- **Context Adaptive**: Default to list on mobile, grid on desktop

## Navigation Layouts

### Mobile Navigation
#### Bottom Tab Bar
```
Height: 80px (includes safe area)
Items: 4-5 main sections
Layout: Even distribution across width
Active State: Icon + label color change
Badge Support: Notification indicators
```

#### Collapsible Top Header
```
Default: 64px height
Scroll Behavior: Collapse to 48px on scroll
Search: Expandable search bar
Context: Property selector (if multi-property)
```

### Desktop Navigation

#### Horizontal Top Navigation
```
Height: 72px
Layout: Logo (left) + Navigation (center) + User (right)
Search: Prominent search bar in center
Responsive: Collapses to hamburger menu on smaller screens
```

#### Vertical Sidebar
```
Width: 240px (expanded), 64px (collapsed)
Sections: Primary navigation + property switcher
Collapsible: Hamburger menu control
Responsive: Overlay on tablet, hidden on mobile
```

## Dashboard Layouts

### Executive Dashboard (Corporate Users)
```
[KPI Cards Row - 4 across]
[Performance Charts Row - 2 across]
[Property Status Grid - responsive columns]
[Recent Activity List - full width]
```

### Property Manager Dashboard
```
[Property Header - name, stats, quick actions]
[Task Overview Cards - 3 across]
[Current Tasks List - main content area]
[Staff Status Sidebar - 280px]
```

### Frontline Staff Dashboard
```
[Welcome Header - personal greeting]
[My Tasks Today - priority sorted]
[Quick Actions - add task, request help]
[Training Notifications - if any]
```

## Form Layouts

### Single Column Forms (Mobile)
- All fields stack vertically
- Full-width inputs with 16px margins
- Labels above inputs
- 24px spacing between field groups
- Primary action button at bottom

### Multi-Column Forms (Desktop)
- Related fields grouped horizontally
- 2-3 columns maximum
- Logical tab order maintained
- Responsive collapse to single column

### Modal Form Layout
```
[Modal Header - 64px]
[Form Content - scrollable]
  - Field groups with consistent spacing
  - Progressive disclosure for advanced options
[Action Bar - 72px] (Cancel + Primary action)
```

## Data Display Layouts

### Table Layouts
#### Mobile Tables
- Horizontal scroll with fixed first column
- Card-based alternative for complex data
- Expandable rows for additional details

#### Desktop Tables
- Full-width tables with fixed headers
- Sorting and filtering controls
- Row actions on hover/selection

### Chart and Analytics Layouts
- Responsive chart sizing
- Legend positioning adapts to screen size
- Export and filter controls consistent placement
- Drill-down capability on larger screens

## Accessibility Layout Considerations

### Focus Management
- Logical tab order through all interactive elements
- Skip links for keyboard navigation
- Focus trapping in modals and overlays

### Screen Reader Layout
- Proper heading hierarchy (h1 → h2 → h3)
- Landmark regions (nav, main, aside, footer)
- Descriptive section labeling

### Touch and Motor Accessibility
- 44px minimum touch targets
- Adequate spacing between interactive elements
- Alternative navigation methods for complex gestures

## Performance Considerations

### Layout Optimization
- CSS Grid and Flexbox for modern browsers
- Graceful degradation for older browsers
- Efficient re-rendering on state changes

### Mobile Performance
- Minimize layout shifts during loading
- Optimize for single-hand use patterns
- Reduce cognitive load with simplified layouts

### Adaptive Loading
- Progressive enhancement based on screen size
- Lazy loading for off-screen components
- Efficient state management for layout changes