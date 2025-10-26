# Party Pocket - Design Guidelines

## Design Approach
**Reference-Based Approach** drawing inspiration from modern mobile-first social and productivity apps:
- **Primary References**: Houseparty (playful social gaming), Instagram (modern mobile UI patterns), Notion (clean productivity tools)
- **Key Principle**: Energetic playfulness meets functional clarity - the games section should feel exciting and social while productivity tools maintain clean efficiency

## Typography System

**Font Families**:
- Primary: Inter (Google Fonts) - Clean, modern, excellent mobile readability
- Accent: Poppins (Google Fonts) - Rounded, friendly for game titles and CTAs

**Type Scale**:
- Hero/Game Titles: text-4xl to text-5xl, font-bold (Poppins)
- Section Headers: text-2xl to text-3xl, font-semibold (Poppins)
- Player Names/Labels: text-lg to text-xl, font-medium (Inter)
- Body Text: text-base, font-normal (Inter)
- Captions/Metadata: text-sm, font-normal (Inter)
- Buttons: text-base to text-lg, font-semibold (Poppins)

## Layout System

**Spacing Primitives**: Use Tailwind units of **2, 4, 6, 8, 12, 16** for consistent rhythm
- Tight spacing (buttons, inline elements): p-2, gap-2
- Standard spacing (cards, sections): p-4, p-6, gap-4
- Generous spacing (major sections): p-8, p-12, mt-16
- Mobile-optimized: Always use responsive spacing (p-4 md:p-8)

**Container Strategy**:
- Full viewport mobile app: All screens use h-screen with overflow management
- Safe area padding: px-4 for all content to respect mobile notches
- Bottom navigation clearance: pb-20 for content above bottom nav
- Max-width constraints: max-w-md mx-auto for content-heavy screens

**Grid System**:
- Single column default (mobile-first)
- Game elements: Circular/radial layouts for bottle spin, player arrangement
- Productivity tools: Traditional vertical stacks with clear sections

## Component Library

### Navigation
**Bottom Tab Bar** (persistent across app):
- Fixed bottom navigation with 5 icons
- Active state: Icon with label, slight scale up
- Inactive: Icon only, reduced opacity
- Height: h-16 with safe area padding
- Icons: Heroicons (outline for inactive, solid for active)
- Tabs: Games, Toss, Notes, Tasks, Calculator

### Game Components

**Bottle Spinner (Truth or Dare)**:
- Centered SVG bottle in circular player arrangement
- Player badges arranged in perfect circle using CSS transforms
- Spin button: Large, pill-shaped, positioned at bottom with backdrop blur
- Winner highlight: Pulsing ring animation, scale transform
- Confetti: Canvas-based particle system on win

**Player Setup**:
- Input field: Rounded-full, large touch target (h-14)
- Add button: Circular FAB-style with icon
- Player chips: Rounded-full badges with delete icon
- Counter display: Large text-6xl in circular badge
- Quick actions: Outlined buttons for "Add Random" helpers

**Game Modal Overlays**:
- Full-screen takeover modals for game actions
- Backdrop: backdrop-blur-lg with semi-transparent background
- Content card: Rounded-3xl corners, centered, max-w-sm
- Large readable text for truth/dare/charade words
- Action buttons: Full-width, stacked vertically, generous spacing (space-y-4)

**Timer Component (Charades)**:
- Circular progress ring (SVG) 
- Large countdown numbers: text-6xl, tabular-nums
- Visual states: Smooth color transitions (no specific colors, just state indicators)
- Sound indicator: Small speaker icon with wave animation
- Controls: Icon buttons for pause/resume

**Scoreboard**:
- Team cards with rounded-2xl containers
- Score display: text-5xl, tabular-nums, font-bold
- Stats breakdown: Grid layout with labeled metrics
- Progress bars: Rounded-full, h-2 for visual score comparison

### Productivity Components

**Notes/Tasks Interface**:
- Clean list view with card-based items
- Item cards: rounded-xl, p-4, with subtle shadow
- Floating Action Button: Fixed bottom-right (bottom-24 right-4)
- Checkbox styling: Large touch targets (w-6 h-6), rounded
- Swipe actions: Delete/complete gestures with visual feedback

**Calculator**:
- Button grid: 4-column layout, equal-height buttons
- Number buttons: text-2xl, aspect-square touch targets
- Operation buttons: Distinct visual treatment
- Display: Top-aligned, text-4xl to text-6xl, tabular-nums, right-aligned
- Min height per button: h-16 for comfortable tapping

### Interactive Elements

**Primary Buttons**:
- Large touch targets: min-h-12 to min-h-14
- Rounded-full for game actions, rounded-xl for forms
- Font: Poppins semibold
- Icon + text combinations where helpful
- Loading states: Spinner animation, disabled appearance

**Secondary Buttons**:
- Outlined style with transparent background
- Same sizing as primary for consistency
- Used for "Skip", "Cancel", alternative actions

**Icon Buttons**:
- Circular: rounded-full, w-12 h-12 minimum
- Clear active/focus states
- Used for: delete, edit, settings, info

**Input Fields**:
- Rounded-xl borders
- Large padding: px-4 py-3
- Clear labels above inputs (text-sm, font-medium)
- Error states: Red border, helper text below
- Focus: Ring treatment for accessibility

### Cards & Containers

**Game Mode Cards** (Home Screen):
- Large tappable cards: rounded-2xl, p-6
- Icon at top (Heroicons, size-12 to size-16)
- Title below icon: text-xl, font-bold
- Brief description: text-sm, muted text
- Hover/tap: Slight scale transform (scale-[0.98])

**Content Cards** (Notes, Tasks):
- Rounded-xl corners
- Padding: p-4
- Clear separation with spacing: space-y-4
- Expandable/collapsible for detailed views

## Animations & Micro-interactions

**Essential Animations** (purposeful only):
- Bottle spin: 2-4s ease-out rotation with momentum
- Modal entrances: Slide-up with spring animation (0.3s)
- Timer countdown: Smooth circular progress
- Confetti: Particle burst on game wins (1.5s duration)
- Tab switches: Fade transition (0.2s)

**Micro-interactions**:
- Button press: Scale transform (scale-95), instant feedback
- Checkbox toggle: Checkmark draw animation
- Swipe gestures: Visual drag feedback
- Pull-to-refresh: Loading spinner with spring physics

**Performance Note**: Keep animations to 60fps, use CSS transforms (translateX, scale) over position changes

## Mobile-Specific Considerations

**Touch Optimization**:
- Minimum tap target: 44x44px (w-11 h-11)
- Spacing between tappable elements: minimum gap-2
- Prevent accidental taps: Adequate padding around critical actions
- Swipe gestures: Clear visual affordances

**Responsive Behavior**:
- Portrait-primary orientation (lock for games)
- Small screens (320px): Reduce text scales by one step
- Large screens (768px+): Center content with max-w-md
- Keyboard handling: Scroll to input when focused

**Loading & Performance**:
- Skeleton screens for initial loads
- Instant feedback on all interactions
- Optimistic UI updates (update UI before server confirmation)
- Progressive enhancement: Core features work immediately

## Accessibility

**Touch & Interaction**:
- All interactive elements meet 44x44px minimum
- Sufficient contrast for text legibility
- Focus indicators for keyboard navigation (tab support on tablets)
- Screen reader labels on icon-only buttons

**Visual Hierarchy**:
- Clear heading structure (h1, h2, h3)
- Consistent use of font weights for importance
- Generous line-height for readability: leading-relaxed (1.625)
- Maximum text width for notes/tasks: max-w-prose

## Screen-Specific Layouts

**Home Dashboard**: 
- Hero section with app name/tagline at top
- Grid of game mode cards (2 columns on small screens)
- Utility tools below (calculator, notes quick access)
- Bottom navigation always visible

**Game Screens**:
- Full viewport immersive experience
- Back button: Fixed top-left, clear tap target
- Score/status: Fixed top bar
- Main game area: Centered in remaining space
- Actions: Fixed bottom with backdrop blur

**Settings Screens**:
- Grouped sections with rounded-xl containers
- Toggle switches: Large, iOS-style
- List items: Tappable rows with chevron indicators
- Destructive actions: Clearly differentiated (e.g., "Delete All Data")

This design system creates an energetic, modern mobile experience that balances playful game interactions with clean, functional productivity tools—all optimized for touch-first interaction and maximum engagement for the 13-35 target audience.