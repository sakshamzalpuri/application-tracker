# Job Application Tracker — Project To-Do

> Portfolio product: a frontend engineering job-search tracker (saved → applied → screening → interview → offer/rejected).
> Rule: work **feature-by-feature**, not phase-by-phase. A feature isn't done until it's built, tested, committed, and you can explain it. Don't jump ahead — each feature depends on the ones before it.

---

## Phase 0 — Repository & Dev Foundation
**Goal:** A running React app pushed to GitHub.
- [v] Create Vite + React (JavaScript, no TS) project
- [y] Configure Tailwind CSS
- [y] Configure ESLint + Prettier
- [] Init Git repo, push to GitHub (public)
- [] Create initial folder structure (`src/app`, `src/components`, `src/features`, `src/lib`, etc.)
- [] Set up environment variable handling (`.env`, `.env.example`)
- [] Build basic app shell (layout wrapper, routing placeholder)
- [] Write README with setup instructions
- [] ✅ Done when: app runs locally, `npm run build` succeeds, repo is public, first meaningful commit exists

---

## Phase 1 — Application Dashboard UI *(mock data)*
- [ ] Sidebar / navigation
- [ ] Dashboard header
- [ ] Summary cards (counts by status)
- [ ] Recent applications widget
- [ ] Status breakdown widget
- [ ] Empty state
- [ ] Responsive layout
- [ ] Interview prep: be able to explain component splitting, props flow, why keys matter

## Phase 2 — Application List
- [ ] Table/list view of applications
- [ ] Card view for responsive/mobile
- [ ] Status badge component
- [ ] Company + role display
- [ ] Applied date display
- [ ] Empty state
- [ ] Loading skeleton

## Phase 3 — Search, Filter & Sort
- [ ] Search by company/role
- [ ] Filter by status
- [ ] Filter by priority
- [ ] Sort by date
- [ ] Sort by company
- [ ] "Clear filters" action
- [ ] Result count display
- [ ] Empty filtered state
- [ ] ⚠️ Rule: derive filtered results from source data + active filters — never store a separate filtered array

## Phase 4 — Create Application
- [ ] Create form (all required fields)
- [ ] URL validation
- [ ] Salary validation
- [ ] Status selection field
- [ ] Date fields
- [ ] Submit/loading state
- [ ] Success feedback
- [ ] Error feedback

## Phase 5 — Edit + Delete Application
- [ ] Edit form
- [ ] Delete confirmation dialog
- [ ] Update UI on edit
- [ ] Remove UI on delete
- [ ] Optimistic update (where safe)
- [ ] Error recovery
- [ ] Interview prep: explain UI state vs. server state vs. derived state

## Phase 6 — Application Detail View
- [ ] Dynamic route (`/applications/:id`)
- [ ] Summary section
- [ ] Job link
- [ ] Status controls
- [ ] Notes section (placeholder)
- [ ] Interview section (placeholder)
- [ ] Follow-up info
- [ ] Edit action
- [ ] 404 handling

## Phase 7 — Local Persistence
- [ ] localStorage read/write utility
- [ ] Serialize/deserialize applications
- [ ] Corrupt-storage fallback
- [ ] Clear/reset action
- [ ] Custom `usePersistedState`-style hook
- [ ] ⚠️ Rule: keep storage logic centralized, not scattered across components

## Phase 8 — Debounced Search
- [ ] `useDebounce` hook
- [ ] Wire into search input
- [ ] Cleanup on unmount
- [ ] Interview prep: implement debounce from scratch, unaided

---

## Phase 9 — Backend & Database (Supabase)
- [ ] Create Supabase project
- [ ] Create tables (applications, interviews, notes, companies)
- [ ] Define relationships
- [ ] Add indexes for common queries
- [ ] Configure env variables for Supabase
- [ ] Create Supabase client module
- [ ] Create repository/API modules per feature
- [ ] ⚠️ Architecture rule: components never call Supabase directly → Component → Hook → Repository/API → Supabase

## Phase 10 — Real Application CRUD (remote)
- [ ] Fetch applications from Supabase
- [ ] Create application (remote)
- [ ] Update application (remote)
- [ ] Delete application (remote)
- [ ] Manual refresh
- [ ] Request error handling
- [ ] Loading states
- [ ] Empty states
- [ ] Retry logic

## Phase 11 — Authentication
- [ ] Sign up flow
- [ ] Login flow
- [ ] Logout flow
- [ ] Session restoration on reload
- [ ] Protected routes
- [ ] Unauthorized state UI
- [ ] Auth loading state
- [ ] ⚠️ Security rule: never expose secrets in frontend code

## Phase 12 — User Data Isolation
- [ ] Add `user_id` ownership field
- [ ] Enable Row-Level Security (RLS) in Supabase
- [ ] Write RLS policies
- [ ] Authenticated queries only
- [ ] Test unauthorized access is blocked

## Phase 13 — Interviews
- [ ] Add interview
- [ ] Edit interview
- [ ] Delete interview
- [ ] Round field
- [ ] Date/time field
- [ ] Interview type field
- [ ] Notes field
- [ ] Status field

## Phase 14 — Notes
- [ ] Add note
- [ ] Edit note
- [ ] Delete note
- [ ] Timestamps
- [ ] Empty state

## Phase 15 — Follow-up Workflow
- [ ] Next follow-up date field
- [ ] "Upcoming follow-ups" view
- [ ] "Overdue follow-ups" view
- [ ] Mark-as-followed-up action
- [ ] Dashboard follow-up section

## Phase 16 — Dashboard Analytics
- [ ] Total applications metric
- [ ] Active applications metric
- [ ] Interviews metric
- [ ] Offers metric
- [ ] Rejection count metric
- [ ] Response rate metric
- [ ] Status distribution chart/view
- [ ] Applications-over-time view
- [ ] ⚠️ Rule: derive all metrics from source data — no duplicate counters

## Phase 17 — URL Query State
- [ ] Search query synced to URL
- [ ] Status filter synced to URL
- [ ] Sort synced to URL
- [ ] Pagination synced to URL (if applicable)
- [ ] Restore filters on page refresh

## Phase 18 — Pagination
- [ ] Page size control
- [ ] Next/previous navigation
- [ ] Current page indicator
- [ ] Result count
- [ ] Loading transition between pages
- [ ] Empty page handling

---

## Phase 19 — Reusable UI System
Build only what the product actually needs:
- [ ] Button
- [ ] Input
- [ ] Select
- [ ] Badge
- [ ] Card
- [ ] Modal
- [ ] Toast
- [ ] Skeleton
- [ ] EmptyState
- [ ] ErrorState
- [ ] ConfirmDialog

## Phase 20 — Accessibility Pass
- [ ] Audit form labels
- [ ] Audit buttons (semantics, focus)
- [ ] Audit form error announcements
- [ ] Focus management on route change
- [ ] Modal focus trap
- [ ] Full keyboard navigation
- [ ] Visible focus states
- [ ] Semantic heading structure
- [ ] Accessible status/toast messages
- [ ] Color contrast check

## Phase 21 — Error Architecture
- [ ] Normalize API errors into a consistent shape
- [ ] Reusable `ErrorState` component
- [ ] Retry actions where relevant
- [ ] Form-level error display
- [ ] Route-level fallback UI
- [ ] React error boundary for unexpected errors

## Phase 22 — Testing
- [ ] Unit tests: filtering, sorting, statistics, validation, date calc, transformations
- [ ] Component tests: application form, filters, status changes, modal behavior
- [ ] User-flow tests: login, create/edit/delete application, filter applications

## Phase 23 — API Mocking (MSW)
- [ ] Set up MSW handlers
- [ ] Mock success responses
- [ ] Mock loading behavior
- [ ] Mock server errors
- [ ] Mock empty responses

## Phase 24 — Debugging Lab
Intentionally introduce and document each bug (Symptom → Reproduction → Root cause → Fix → Prevention):
- [ ] Stale state bug
- [ ] Incorrect `useEffect` dependency bug
- [ ] Broken filter
- [ ] Failed API request
- [ ] Race condition
- [ ] Missing list key
- [ ] Controlled/uncontrolled input issue
- [ ] Timer cleanup issue

## Phase 25 — Performance
- [ ] Measure unnecessary re-renders (React DevTools)
- [ ] Measure expensive derived calculations
- [ ] Measure large-list rendering cost
- [ ] Measure bundle size
- [ ] Measure network request waterfall
- [ ] Apply `memo` / `useMemo` / `useCallback` only where evidence justifies it
- [ ] Apply lazy loading / code splitting where justified
- [ ] Apply debouncing where justified

## Phase 26 — Production UX Polish
- [ ] Responsive layouts across all views
- [ ] Consistent spacing system
- [ ] Loading skeletons everywhere needed
- [ ] Empty states everywhere needed
- [ ] Error states everywhere needed
- [ ] Toast feedback for actions
- [ ] Confirmation dialogs for destructive actions
- [ ] Disabled submit states
- [ ] Mobile navigation
- [ ] Accessible focus states

## Phase 27 — Production Configuration
- [ ] Production environment variables
- [ ] Separate dev/prod config
- [ ] Verify production build
- [ ] Deployment configuration
- [ ] SPA route fallback (refresh on nested routes)
- [ ] Document error-monitoring strategy

## Phase 28 — Deployment
- [ ] Deploy frontend (Vercel)
- [ ] Configure production env variables
- [ ] Configure Supabase production project
- [ ] Test auth in production
- [ ] Test CRUD in production
- [ ] Test routing in production
- [ ] Test refresh on nested routes
- [ ] Verify production build works end-to-end
- [ ] Deliverables: live URL, GitHub repo, README, screenshots

## Phase 29 — Git & Professional Workflow
- [ ] Use feature branches → implement → test → commit → PR → review → merge
- [ ] Follow conventional commit format (`feat:`, `fix:`, `refactor:`, `test:`, `perf:`, `docs:`)

## Phase 30 — Portfolio Presentation
README must cover:
- [ ] What the product does
- [ ] Why it exists
- [ ] Main features
- [ ] Tech stack
- [ ] Architecture
- [ ] Data flow
- [ ] Key technical decisions
- [ ] Testing strategy
- [ ] Performance work
- [ ] Challenges & debugging stories
- [ ] Trade-offs
- [ ] Local setup instructions
- [ ] Live demo link

Include:
- [ ] Live URL
- [ ] Screenshots
- [ ] Architecture diagram
- [ ] Feature walkthrough
- [ ] GitHub repo link

---

## Definition of Done (apply to every feature)
- [ ] Requirement is clear
- [ ] UI works
- [ ] State/data flow understood
- [ ] Loading state exists where needed
- [ ] Empty state exists where needed
- [ ] Error state exists where needed
- [ ] Validation exists where needed
- [ ] Responsive behavior works
- [ ] Accessibility is acceptable
- [ ] Important logic is tested
- [ ] Code is understandable
- [ ] No unnecessary abstraction added
- [ ] Git commit exists
- [ ] README updated if architecture changed

## Final Deliverables Checklist
- [ ] Public GitHub repository
- [ ] Live production URL
- [ ] Authentication
- [ ] Persistent application data
- [ ] Application CRUD
- [ ] Search/filter/sort
- [ ] Application detail
- [ ] Interviews
- [ ] Notes
- [ ] Follow-ups
- [ ] Analytics
- [ ] Responsive UI
- [ ] Accessibility pass
- [ ] Automated tests
- [ ] API mocking
- [ ] Documented debugging cases
- [ ] Performance notes
- [ ] Architecture documentation
- [ ] Strong README
- [ ] Screenshots
- [ ] Interview project walkthrough
- [ ] Machine-coding features extracted from the project

---

### Guardrails (re-read when tempted to scope-creep)
- No Redux/Zustand/TanStack Query/Next.js/TypeScript/UI kit/custom backend unless a real problem demands it.
- No feature added because it "looks impressive" or a tutorial had it.
- Ship the smallest useful version first — evolve feature-by-feature.
