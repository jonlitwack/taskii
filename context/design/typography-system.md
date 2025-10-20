# Typography System - Taskii Design System

## Font Selection

### Primary Typeface: Inter
- **Rationale**: Excellent readability on mobile devices, professional appearance, extensive language support for international properties
- **Usage**: All interface text, body copy, form labels
- **Fallbacks**: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif

### Display Typeface: Inter (Bold/Semibold)
- **Usage**: Large headings, hero text, marketing content
- **Rationale**: Maintains consistency while providing emphasis through weight

### Monospace: SF Mono / Consolas
- **Usage**: Property codes, timestamps, technical data, reference numbers
- **Rationale**: Clear distinction of systematic data from narrative content

## Type Scale

### Mobile-First Scale (Base: 16px)

**Display Large**
- Size: 32px (2rem)
- Line Height: 36px (2.25rem)
- Weight: 700 (Bold)
- Usage: Page titles, major section headers

**Display Medium**
- Size: 28px (1.75rem)
- Line Height: 32px (2rem)
- Weight: 600 (Semibold)
- Usage: Card titles, modal headers

**Heading 1**
- Size: 24px (1.5rem)
- Line Height: 28px (1.75rem)
- Weight: 600 (Semibold)
- Usage: Section headers, task category titles

**Heading 2**
- Size: 20px (1.25rem)
- Line Height: 24px (1.5rem)
- Weight: 600 (Semibold)
- Usage: Subsection headers, property names

**Heading 3**
- Size: 18px (1.125rem)
- Line Height: 22px (1.375rem)
- Weight: 500 (Medium)
- Usage: Card headers, form section titles

**Body Large**
- Size: 16px (1rem)
- Line Height: 24px (1.5rem)
- Weight: 400 (Regular)
- Usage: Primary body text, task descriptions

**Body Medium**
- Size: 14px (0.875rem)
- Line Height: 20px (1.25rem)
- Weight: 400 (Regular)
- Usage: Secondary text, metadata, captions

**Body Small**
- Size: 12px (0.75rem)
- Line Height: 16px (1rem)
- Weight: 400 (Regular)
- Usage: Fine print, timestamps, helper text

**Label Large**
- Size: 14px (0.875rem)
- Line Height: 20px (1.25rem)
- Weight: 500 (Medium)
- Usage: Form labels, button text, tab labels

**Label Medium**
- Size: 12px (0.75rem)
- Line Height: 16px (1rem)
- Weight: 500 (Medium)
- Usage: Small button text, badges, tags

### Desktop Scale Adjustments (≥1024px)

**Display Large**: 40px (2.5rem) / 44px (2.75rem) line height
**Display Medium**: 32px (2rem) / 36px (2.25rem) line height
**Heading 1**: 28px (1.75rem) / 32px (2rem) line height

## User Preference Typography

### Font Size Scaling
- **Small**: 90% of base scale (14.4px base)
- **Medium**: 100% of base scale (16px base) - Default
- **Large**: 110% of base scale (17.6px base)
- **Extra Large**: 125% of base scale (20px base)

### Reading Preferences
- **Comfortable**: Standard line height (1.5x)
- **Compact**: Reduced line height (1.4x) for information density
- **Spacious**: Increased line height (1.6x) for easier reading

### Dyslexia-Friendly Options
- Alternative font: OpenDyslexic (optional)
- Increased character spacing (0.12em)
- Enhanced line height (1.6x minimum)
- Reduced text justification

## Contextual Typography

### Task Cards
- **Task Title**: Heading 3 (18px, Medium)
- **Task Description**: Body Medium (14px, Regular)
- **Due Date**: Label Medium (12px, Medium)
- **Priority Badge**: Label Medium (12px, Medium, All Caps)

### Navigation
- **Primary Nav Items**: Label Large (14px, Medium)
- **Secondary Nav Items**: Label Medium (12px, Medium)
- **Breadcrumbs**: Body Small (12px, Regular)

### Forms
- **Form Labels**: Label Large (14px, Medium)
- **Input Text**: Body Large (16px, Regular)
- **Helper Text**: Body Small (12px, Regular)
- **Error Text**: Body Small (12px, Regular, Red)

### Notifications
- **Notification Title**: Label Large (14px, Medium)
- **Notification Body**: Body Medium (14px, Regular)
- **Notification Timestamp**: Body Small (12px, Regular)
- **Action Buttons**: Label Medium (12px, Medium)

### Data Tables
- **Column Headers**: Label Large (14px, Medium)
- **Cell Data**: Body Medium (14px, Regular)
- **Row Actions**: Label Medium (12px, Medium)

### Training Content
- **Training Title**: Heading 2 (20px, Semibold)
- **Training Body**: Body Large (16px, Regular)
- **Training Steps**: Body Medium (14px, Regular) with numbered list
- **Training Notes**: Body Small (12px, Regular, Italic)

## Accessibility Considerations

### Reading Experience
- Minimum 16px base size for body text on mobile
- 1.5x line height minimum for improved readability
- Sufficient color contrast (see Color System)
- Support for user font size preferences

### International Properties
- Font supports extended Latin, Cyrillic, and basic multilingual plane
- Text can scale up to 200% without horizontal scrolling
- Consistent spacing across different character sets
- Right-to-left (RTL) text support for Arabic properties

### Visual Accessibility
- High contrast typography options
- Font weight variations for emphasis without relying on color
- Clear visual hierarchy through size and weight combinations
- Support for system-level typography preferences

## Responsive Behavior

### Breakpoint Adjustments
- **Mobile (≤480px)**: Base scale, optimized for thumb interaction
- **Tablet (481-1023px)**: Slight size increases for better readability
- **Desktop (≥1024px)**: Full desktop scale with enhanced hierarchy

### Dynamic Scaling
- Text scales with user's browser/system preferences
- Maintains proportional relationships across all sizes
- Preserves touch targets and interactive areas
- Adapts to user's personal font size preferences

## Special Text Treatments

### Status Indicators
- **All Caps**: Label text for status badges (COMPLETED, OVERDUE, etc.)
- **Tabular Numbers**: For consistent alignment in data tables
- **Monospace**: Property codes, timestamps, reference numbers

### Emphasis Patterns
- **Bold (600)**: Primary actions, important information
- **Medium (500)**: Labels, secondary hierarchy
- **Regular (400)**: Body text, descriptions
- **Color**: Primary brand blue for links and interactive text

### Personalization Features
- **User Name Display**: Heading 3 (18px, Medium) in personal areas
- **Preference Labels**: Body Medium (14px, Regular) with clear hierarchy
- **Settings Text**: Body Large (16px, Regular) for readability

### Multi-language Considerations
- Line height increases for scripts with ascenders/descenders
- Character spacing adjustments for dense scripts
- Consistent brand feeling across all supported languages
- Font fallbacks for unsupported characters

## Performance Optimization

### Font Loading
- System fonts prioritized for instant rendering
- Web fonts loaded asynchronously with fallbacks
- Font-display: swap for better user experience
- Reduced font variants to minimize loading time

### Text Rendering
- Optimized for mobile performance
- Consistent rendering across devices
- Efficient re-flow during dynamic content updates
- Minimal layout shift during font loading