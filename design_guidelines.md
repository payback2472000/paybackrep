# Payback247 P2P Network Marketing Dashboard - Design Guidelines

## Design Approach

**Design System**: Material Design 3 principles adapted for financial/productivity applications, with enhanced visual appeal for user engagement and trust-building in a network marketing context.

**Justification**: This application requires both utility (data management, payment tracking) and emotional engagement (growth motivation, network visualization). Material Design provides robust patterns for data-dense interfaces while allowing vibrant customization.

---

## Core Design Elements

### A. Color Palette

**Primary Colors (Dark Mode)**
- Primary: 220 85% 55% (Vibrant blue - trust, technology, growth)
- Primary Light: 220 80% 65%
- Primary Dark: 220 90% 45%

**Primary Colors (Light Mode)**
- Primary: 220 75% 50%
- Primary Light: 220 70% 60%
- Primary Dark: 220 80% 40%

**Accent & Status Colors**
- Success: 142 70% 45% (earnings, confirmed payments)
- Warning: 35 90% 55% (pending actions, timers)
- Error: 0 70% 50% (disputes, expired payments)
- Info: 200 80% 50% (notifications, help text)

**Background & Surfaces (Dark Mode)**
- Background: 220 20% 10%
- Surface: 220 15% 15%
- Surface Elevated: 220 15% 18%

**Background & Surfaces (Light Mode)**
- Background: 220 20% 98%
- Surface: 0 0% 100%
- Surface Elevated: 220 30% 97%

**Text Colors**
- Dark Mode Primary Text: 0 0% 95%
- Dark Mode Secondary Text: 0 0% 70%
- Light Mode Primary Text: 220 20% 15%
- Light Mode Secondary Text: 220 15% 45%

### B. Typography

**Font Families**
- Primary: 'Inter' (Google Fonts) - body text, UI elements
- Display: 'Poppins' (Google Fonts) - headings, stat numbers
- Monospace: 'JetBrains Mono' - transaction IDs, wallet addresses

**Type Scale**
- Headline Large: 32px / 600 weight (dashboard stat values)
- Headline Medium: 24px / 600 weight (section headers)
- Title: 20px / 600 weight (card titles)
- Body Large: 16px / 400 weight (primary content)
- Body: 14px / 400 weight (secondary content)
- Caption: 12px / 400 weight (labels, helper text)

### C. Layout System

**Spacing Units**: Use Tailwind's 4-based scale: 2, 4, 6, 8, 12, 16, 20, 24, 32
- Component padding: p-4 to p-6
- Section spacing: py-8 to py-12
- Card gaps: gap-4 to gap-6
- Grid/list item spacing: space-y-4

**Grid System**
- Desktop Sidebar: 280px fixed width (expanded), 64px (collapsed)
- Main Content: max-w-7xl with px-4 to px-8
- Card Layouts: grid-cols-1 md:grid-cols-2 lg:grid-cols-3 xl:grid-cols-4
- Dashboard Stats: Always 4 columns on desktop, 2 on tablet, 1 on mobile

**Container Widths**
- Full app: w-full
- Content area: max-w-7xl mx-auto
- Forms/modals: max-w-2xl
- Stat cards: Full width of grid column

### D. Component Library

**Cards**
- Base: Rounded corners (rounded-lg), subtle shadow (shadow-sm), surface background
- Elevated: shadow-md with surface-elevated background
- Interactive: Hover state with shadow-lg transition
- Stat Cards: Gradient backgrounds (primary to primary-dark at 135deg), white text, large numbers (text-4xl)

**Buttons**
- Primary: Gradient background (primary to primary-dark), white text, rounded-lg, px-6 py-3
- Secondary: Outline style, primary border/text, hover fills with light primary
- Danger: Error color background for destructive actions
- Icon Buttons: w-10 h-10 rounded-full with centered icon

**Forms**
- Input Fields: Dark surface background, subtle border, rounded-md, px-4 py-2.5
- Focus State: Primary color ring (ring-2 ring-primary)
- Labels: Text-sm font-medium, mb-2
- File Upload: Dashed border, p-8, center-aligned with upload icon

**Badges & Status Indicators**
- Pill shape: rounded-full px-3 py-1 text-xs
- Color coded: Success (green), Warning (orange), Error (red), Info (blue), Neutral (gray)
- With icons: Leading icon (12px) + text

**Navigation**
- Sidebar Items: rounded-lg, p-3, hover background (surface-elevated)
- Active State: Primary background with 20% opacity
- Icons: 20px, left-aligned with 8px gap to text
- Notification Badges: Absolute positioned, small circle with count

**Data Display**
- Tables: Striped rows, hover highlight, sticky headers
- Progress Bars: Rounded-full, primary gradient fill, light background
- Network Tree: Card-based nodes, connecting lines, expandable levels
- Timers: Large countdown numbers with label, warning color when < 1 hour

**Modals & Overlays**
- Backdrop: Dark overlay (bg-black/60)
- Modal: Surface background, rounded-xl, max-w-2xl, shadow-2xl
- Close Button: Top-right, icon button style
- Actions: Bottom-aligned, space-x-4

**Payment Method Tabs**
- Horizontal tabs above payment details
- Active tab: Primary color underline (border-b-2), bold text
- Inactive: Secondary text, hover state

### E. Animations

**Use Sparingly**
- Page Transitions: Fade in content (150ms ease-in)
- Card Hover: Scale up slightly (scale-105, 200ms)
- Button Clicks: Subtle scale down (scale-95, 100ms)
- Notifications: Slide in from top (300ms ease-out)
- Modals: Fade in backdrop + scale up modal (200ms)
- NO complex animations on data tables or forms

---

## Page-Specific Guidelines

### Landing Page (Public)
- Hero Section: 60vh height, gradient background (primary to primary-dark), centered headline + CTA
- How It Works: 3-column grid with icon-based cards
- Income Plans: Card carousel showing Referral, Binary, Matrix with key stats
- FAQ: Expandable accordion style
- Footer: 4-column layout (About, Links, Contact, Social)

### Dashboard (Authenticated)
- Stat Cards Row: 4 gradient cards with large numbers, icons, trend indicators
- Account Status Banner: Full-width, colored based on status (success/warning)
- Referral Links Section: 2-column grid with copy buttons and social share icons
- Visual Hierarchy: Stats → Status → Actions

### Join/Payment Tab
- Progress Bar: Top of page, shows 5/5 payments completed
- Payment Cards: Expandable accordion, status badge on header
- Payment Interface: Tabbed (QR, Bank, UPI, Crypto), details in copyable fields, upload zone, submit button
- Timer: Prominent countdown in warning color

### Matrix/Binary Tabs
- Overview Stats: Row of 3-4 stat cards
- Level Breakdown: Expandable cards showing fill progress
- Queue Table: Sortable, searchable, highlight current user row
- Team Visualization: Tree structure with user avatars in circular nodes

### Admin Panel
- User Table: Full-width, search bar top-right, sortable columns
- Dispute Cards: List view with action buttons (Resolve for Sender/Receiver)
- System Config: Form layout with edit mode toggle, danger zone separated

---

## Images

**Hero Section**: Large background image (1920x1080) showing diverse people collaborating, successful network, or financial growth visualization. Apply dark gradient overlay (60% opacity) for text readability.

**Dashboard Stat Card Icons**: Use icon library (Heroicons) for:
- Total Income: Currency icon
- Sponsor Income: Users icon  
- Binary Income: Diagram icon
- Matrix Income: Grid icon

**User Avatars**: Circular, 40px for lists, 80px for profiles, default gradient backgrounds with initials if no image

**Payment QR Codes**: Display 200x200px QR codes with border and label

**No other images needed** - interface is data and component-focused.