---
name: Obsidian Precision
colors:
  surface: '#131315'
  surface-dim: '#131315'
  surface-bright: '#39393b'
  surface-container-lowest: '#0e0e10'
  surface-container-low: '#1c1b1d'
  surface-container: '#201f22'
  surface-container-high: '#2a2a2c'
  surface-container-highest: '#353437'
  on-surface: '#e5e1e4'
  on-surface-variant: '#c2c6d6'
  inverse-surface: '#e5e1e4'
  inverse-on-surface: '#313032'
  outline: '#8c909f'
  outline-variant: '#424754'
  surface-tint: '#adc6ff'
  primary: '#adc6ff'
  on-primary: '#002e6a'
  primary-container: '#4d8eff'
  on-primary-container: '#00285d'
  inverse-primary: '#005ac2'
  secondary: '#ddb7ff'
  on-secondary: '#490080'
  secondary-container: '#6f00be'
  on-secondary-container: '#d6a9ff'
  tertiary: '#ffb786'
  on-tertiary: '#502400'
  tertiary-container: '#df7412'
  on-tertiary-container: '#461f00'
  error: '#ffb4ab'
  on-error: '#690005'
  error-container: '#93000a'
  on-error-container: '#ffdad6'
  primary-fixed: '#d8e2ff'
  primary-fixed-dim: '#adc6ff'
  on-primary-fixed: '#001a42'
  on-primary-fixed-variant: '#004395'
  secondary-fixed: '#f0dbff'
  secondary-fixed-dim: '#ddb7ff'
  on-secondary-fixed: '#2c0051'
  on-secondary-fixed-variant: '#6900b3'
  tertiary-fixed: '#ffdcc6'
  tertiary-fixed-dim: '#ffb786'
  on-tertiary-fixed: '#311400'
  on-tertiary-fixed-variant: '#723600'
  background: '#131315'
  on-background: '#e5e1e4'
  surface-variant: '#353437'
  surface-card: '#18181b'
  surface-hover: '#27272a'
  border-subtle: rgba(255, 255, 255, 0.10)
  border-focus: '#71717a'
  text-primary: '#f4f4f5'
  text-secondary: '#e4e4e7'
  text-muted: '#a1a1aa'
  text-subtle: '#71717a'
  status-danger: '#f43f5e'
  status-danger-text: '#fda4af'
  status-info: '#3b82f6'
  status-info-text: '#93c5fd'
  status-warning: '#f59e0b'
  status-warning-text: '#fcd34d'
  status-success: '#10b981'
  status-success-text: '#4ade80'
  status-purple: '#a855f7'
  status-purple-text: '#d8b4fe'
typography:
  headline-xl:
    fontFamily: Geist
    fontSize: 24px
    fontWeight: '700'
    lineHeight: 32px
    letterSpacing: -0.025em
  headline-xl-mobile:
    fontFamily: Geist
    fontSize: 20px
    fontWeight: '700'
    lineHeight: 28px
    letterSpacing: -0.02em
  headline-sm:
    fontFamily: Geist
    fontSize: 16px
    fontWeight: '600'
    lineHeight: 24px
    letterSpacing: -0.015em
  body-md:
    fontFamily: Geist
    fontSize: 14px
    fontWeight: '500'
    lineHeight: 20px
    letterSpacing: -0.01em
  body-sm:
    fontFamily: Geist
    fontSize: 13px
    fontWeight: '400'
    lineHeight: 18px
    letterSpacing: 0em
  label-md:
    fontFamily: Geist
    fontSize: 12px
    fontWeight: '500'
    lineHeight: 16px
    letterSpacing: 0em
  label-eyebrow:
    fontFamily: Geist
    fontSize: 11px
    fontWeight: '600'
    lineHeight: 14px
    letterSpacing: 0.05em
  metadata-xs:
    fontFamily: Geist
    fontSize: 12px
    fontWeight: '400'
    lineHeight: 16px
    letterSpacing: 0em
rounded:
  sm: 0.125rem
  DEFAULT: 0.25rem
  md: 0.375rem
  lg: 0.5rem
  xl: 0.75rem
  full: 9999px
spacing:
  gutter: 1.5rem
  margin: 1.5rem
  space-xs: 0.25rem
  space-sm: 0.5rem
  space-md: 0.75rem
  space-lg: 1rem
  space-xl: 1.5rem
---

# Design System: trackr

A refined, high-density dark mode design system for the **trackr** job application tracker web application.

---

## 1. Visual Theme & Philosophy
- **Aesthetic**: Minimalist, high-contrast, dense SaaS productivity tool (Linear / Notion inspired).
- **Mode**: Primary dark mode with deep zinc/obsidian surfaces and subtle 1px translucent borders.
- **Elevation & Shadows**: Flat overall layout; soft floating shadows reserved exclusively for floating navigation (`shadow-lg shadow-black/40` or `shadow-xl shadow-black/25`).
- **Typography & Copy**: Clean sans-serif, sentence-case headings and labels, concise and actionable wording.

---

## 2. Color Palette & Tokens

### Backgrounds & Surfaces
- **Canvas / Page Background**: `#09090b` (Tailwind `bg-zinc-950` / zinc dark canvas)
- **Card / Surface Background**: `rgba(24, 24, 27, 0.6)` to `rgba(24, 24, 27, 0.9)` (`bg-zinc-900/60` to `bg-zinc-900/90`)
- **Floating Bar Background**: `rgba(24, 24, 27, 0.85)` with `backdrop-blur-md`
- **Subtle Surface Hover**: `rgba(39, 39, 42, 0.5)` (`bg-zinc-800/50`)

### Borders & Separators
- **Standard Card / Container Border**: `1px solid rgba(255, 255, 255, 0.1)` (`border-white/10`)
- **Nav Pill Border**: `1px solid rgba(255, 255, 255, 0.1)` or `border-zinc-800/80`
- **Input Focus Border**: `#71717a` (`border-zinc-500`)

### Typography Colors
- **Primary Headings & Metrics**: `#f4f4f5` (`text-zinc-100`)
- **Body & Secondary Values**: `#e4e4e7` (`text-zinc-200`)
- **Muted Labels & Metadata**: `#a1a1aa` (`text-zinc-400`)
- **De-emphasized / Percentages**: `#71717a` (`text-zinc-500`)

### Semantic & Status Accents
- **Overdue / Danger / High Priority**: Rose
  - Background: `rgba(244, 63, 94, 0.10)` (`bg-rose-500/10`)
  - Border: `rgba(244, 63, 94, 0.25)` (`border-rose-500/25`)
  - Text: `#fda4af` (`text-rose-300`)
  - Accent Bar/Dot: `#f43f5e` (`bg-rose-500`)
- **Interview / Info / Active**: Blue
  - Background: `rgba(59, 130, 246, 0.10)` (`bg-blue-500/10`)
  - Border: `rgba(59, 130, 246, 0.25)` (`border-blue-500/25`)
  - Text: `#93c5fd` (`text-blue-300`)
  - Accent Bar/Dot: `#3b82f6` (`bg-blue-500`)
- **Idle / Warning / Screening / Medium Priority**: Amber
  - Background: `rgba(245, 158, 11, 0.10)` (`bg-amber-500/10`)
  - Border: `rgba(245, 158, 11, 0.25)` (`border-amber-500/25`)
  - Text: `#fcd34d` (`text-amber-300`)
  - Accent Bar/Dot: `#f59e0b` (`bg-amber-500`)
- **Applied / Positive Trend / Low Priority**: Emerald / Zinc
  - Text / Trend: `#4ade80` (`text-emerald-400`)
  - Progress Bar / Dot: `#10b981` (`bg-emerald-500`)
- **Offer / Stage**: Purple
  - Badge Background: `rgba(168, 85, 247, 0.12)`
  - Badge Text: `#d8b4fe` (`text-purple-300`)
  - Dot / Progress: `#a855f7` (`bg-purple-500`)
- **Rejected**: Rose / Zinc muted
  - Badge Background: `rgba(244, 63, 94, 0.10)`
  - Badge Text: `#fda4af`
  - Dot: `#f43f5e`

---

## 3. Typography Scale & Weights
- **Page Title**: `20px - 24px` (`text-xl sm:text-2xl font-bold tracking-tight text-zinc-100`)
- **Section Headers & Eyebrows**: `11px - 12px` (`text-xs font-semibold uppercase tracking-wider text-zinc-400`)
- **Card Subheaders / Body**: `13px - 14px` (`text-xs sm:text-sm font-medium text-zinc-200`)
- **Metadata / Timestamps / Counts**: `12px` (`text-xs text-zinc-400` / `text-zinc-500`)

---

## 4. Layout & Spacing Rules
- **Vertical Spacing Rhythm**: Strict `24px` (`space-y-6` / `gap-6`) between major vertical sections.
- **Card / Table Container**: `1px solid rgba(255,255,255,0.1)` border against canvas (`bg-zinc-900/60` to `bg-zinc-900/80`), `rounded-xl`.
- **Border Radius**:
  - Cards & Table Containers: `rounded-xl`
  - Inputs, Dropdowns & Buttons: `rounded-lg` (8px)
  - Status Badges & Nav: `rounded-full` (9999px)
