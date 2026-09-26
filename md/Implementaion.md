# Job Application Tracker — Full Implementation Plan

<aside>
🎯

**Purpose:** This is the single portfolio product that grows with the roadmap. We learn a concept only when the product needs it, implement it end-to-end, ship it, debug it, and then explain it in an interview.

</aside>

## 1. Product Brief

### Product

**Job Application Tracker** — a personal job-search workspace for tracking applications, interviews, follow-ups, notes, and outcomes.

### Problem

Job seekers commonly track applications across spreadsheets, bookmarks, email, and notes. That makes it difficult to answer:

- What have I applied to?
- Which applications need follow-up?
- What stage is each application in?
- Which companies and roles are active?
- How is my search progressing?

### Target User

A job seeker managing an active frontend/job search with multiple applications and interview processes.

### Core Outcome

The user can capture an opportunity once and manage its complete lifecycle from **saved → applied → screening → interview → offer/rejected**, with search, filtering, reminders, notes, and useful statistics.

### Portfolio Outcome

The product should demonstrate:

- JavaScript fundamentals
- React component design
- state and data flow
- forms and validation
- routing
- asynchronous data fetching
- API/data-layer separation
- authentication
- reusable UI
- accessibility
- testing
- debugging
- performance
- Git workflow
- deployment
- product thinking

### Non-goals

Do **not** build:

- a job-board scraper
- automated job applications
- AI resume generation
- social networking
- chat
- complex notifications infrastructure
- mobile app
- admin panel
- payments

These are scope traps. The portfolio is a **frontend engineering product**, not a startup.

---

## 2. Product Principles

1. **Feature-first, not phase-first.**
2. Every feature must create a visible product outcome.
3. Learn → implement → break → debug → test → ship → explain.
4. Prefer simple architecture until complexity is justified.
5. No TypeScript for this roadmap.
6. No library unless it solves a real problem.
7. No duplicated state when the value can be derived.
8. Every async feature must have loading, success, empty, and error behavior where applicable.
9. Every completed feature must be committed.
10. The deployed application is the source of truth, not screenshots.

---

## 3. Tech Stack

| Area | Choice | Why |
| --- | --- | --- |
| Language | JavaScript | Matches the roadmap and keeps the learning target focused. |
| UI | React | Primary frontend interview target. |
| Build | Vite | Fast development and simple production builds. |
| Styling | Tailwind CSS | Fast UI implementation and responsive design practice. |
| Routing | React Router | Real multi-page application flow. |
| Backend service | Supabase | Managed database + authentication without turning the portfolio into a backend project. |
| Data layer | Dedicated API/repository modules | Keeps UI independent from the backend implementation. |
| Testing | Vitest + React Testing Library | Unit and user-flow testing. |
| API mocking | MSW | Test async UI behavior without relying on a live backend. |
| Linting | ESLint | Catch common JavaScript/React mistakes. |
| Formatting | Prettier | Consistent code formatting. |
| Version control | Git + GitHub | Professional workflow and portfolio proof. |
| Deployment | Vercel | Simple production deployment for the React app. |

### Stack rule

Do **not** add Redux, Zustand, TanStack Query, Next.js, TypeScript, a UI component library, or a custom Node backend just because they are popular.

Add a tool only when the current implementation exposes a real problem that the tool solves.

---

## 4. Product Architecture

### High-level flow

```
User
 ↓
React UI
 ↓
Route
 ↓
Feature component
 ↓
Custom hook / state logic
 ↓
Repository / API module
 ↓
Supabase
 ↓
Database
```

### Suggested project structure

```
src/
├── app/
│   ├── App.jsx
│   ├── routes.jsx
│   └── providers/
├── components/
│   ├── ui/
│   └── layout/
├── features/
│   ├── applications/
│   │   ├── components/
│   │   ├── hooks/
│   │   ├── application.api.js
│   │   ├── application.utils.js
│   │   └── application.validation.js
│   ├── interviews/
│   ├── companies/
│   ├── dashboard/
│   └── auth/
├── lib/
│   ├── supabase.js
│   └── constants.js
├── hooks/
├── utils/
├── styles/
└── main.jsx
```

Do not create folders until the feature needs them.

---

## 5. Core Domain Model

### Application

```
id
user_id
company_name
role_title
job_url
location
employment_type
source
status
priority
salary_min
salary_max
applied_at
next_follow_up_at
created_at
updated_at
```

### Interview

```
id
application_id
round
type
scheduled_at
status
notes
created_at
```

### Note

```
id
application_id
content
created_at
updated_at
```

### Company

```
id
user_id
name
website
location
notes
created_at
```

### Initial status values

```
saved
applied
screening
interview
offer
rejected
withdrawn
```

Keep the domain small. Add fields only when a real feature requires them.

---

# 6. Feature-by-Feature Implementation Plan

## Feature 0 — Repository + Development Foundation

### Outcome

A clean React application that runs locally and is pushed to GitHub.

### Build

- Create Vite React JavaScript project.
- Configure Tailwind.
- Configure ESLint + Prettier.
- Add Git repository.
- Create initial folder structure.
- Add environment variable handling.
- Create basic application shell.
- Add README with setup instructions.

### Learn

- Vite
- npm scripts
- React entry point
- environment variables
- Git workflow

### Done when

- App runs locally.
- Production build succeeds.
- Repository is public.
- README explains setup.
- First meaningful commit exists.

---

## Feature 1 — Application Dashboard UI

### Outcome

A realistic dashboard using local/mock data.

### Build

- Sidebar/navigation.
- Dashboard header.
- Application summary cards.
- Recent applications.
- Status breakdown.
- Empty state.
- Responsive layout.

### Learn

- JSX
- components
- props
- destructuring
- `.map()`
- keys
- conditional rendering
- composition
- reusable components

### Interview proof

Explain:

- why components are split this way
- where data lives
- how props flow
- why list keys are required

---

## Feature 2 — Application List

### Outcome

The user can view all applications.

### Build

- Application table/list.
- Application card for responsive layout.
- Status badge.
- Company and role.
- Applied date.
- Empty state.
- Loading skeleton placeholder.

### Learn

- rendering collections
- reusable component APIs
- derived UI
- conditional UI

---

## Feature 3 — Search, Filter and Sort

### Outcome

The application list behaves like a real product.

### Build

- Search by company/role.
- Status filter.
- Priority filter.
- Sort by date.
- Sort by company.
- Clear filters.
- Result count.
- Empty filtered state.

### Learn

- array transformation
- `filter`
- `map`
- `sort`
- derived data
- immutability
- controlled inputs

### Rule

Do not store filtered applications separately. Derive them from the source applications and active filters.

---

## Feature 4 — Create Application

### Outcome

A user can add an application.

### Build

- Create application form.
- Required fields.
- URL validation.
- Salary validation.
- Status selection.
- Date fields.
- Submit state.
- Success feedback.
- Error feedback.

### Learn

- controlled forms
- validation
- form state
- submit lifecycle
- reusable form fields

---

## Feature 5 — Edit + Delete Application

### Outcome

Full local CRUD exists.

### Build

- Edit form.
- Delete confirmation.
- Update UI.
- Delete UI.
- Optimistic interaction where safe.
- Error recovery.

### Learn

- CRUD lifecycle
- state transitions
- confirmation patterns
- error handling

### Interview proof

Explain the difference between:

- UI state
- server state
- derived state

---

## Feature 6 — Application Detail

### Outcome

Every application has a dedicated detail view.

### Build

- Dynamic route.
- Application summary.
- Job link.
- Status controls.
- Notes section.
- Interview section.
- Follow-up information.
- Edit action.

### Learn

- React Router
- route params
- nested layouts
- navigation
- 404 handling

---

## Feature 7 — Local Persistence

### Outcome

Applications survive browser refresh.

### Build

- localStorage persistence.
- serialization/deserialization.
- storage utility.
- corrupt-storage fallback.
- clear/reset behavior.

### Learn

- browser storage
- JSON
- custom hooks
- persistence boundaries

### Rule

Storage logic must not be scattered throughout components.

---

## Feature 8 — Debounced Search

### Outcome

Search does not react to every keystroke when async search is introduced.

### Build

- `useDebounce`.
- Search input.
- delayed query.
- cleanup.

### Learn

- closures
- timers
- cleanup
- debounce
- async UI thinking

### Interview proof

Implement debounce from a blank file.

---

## Feature 9 — Backend + Database

### Outcome

Local mock data is replaced by persistent user data.

### Build

- Create Supabase project.
- Create tables.
- Add relationships.
- Add indexes for common queries.
- Configure environment variables.
- Create database client.
- Create repository/API modules.

### Learn

- database basics
- API boundaries
- CRUD requests
- asynchronous data
- environment configuration

### Architecture rule

Components must **not** call Supabase directly.

Use:

```
Component
 → Hook
 → Repository/API
 → Supabase
```

---

## Feature 10 — Real Application CRUD

### Outcome

Create/read/update/delete now persist remotely.

### Build

- Fetch applications.
- Create application.
- Update application.
- Delete application.
- Refresh.
- Request errors.
- Loading states.
- Empty states.
- Retry.

### Learn

- async/await
- Promise lifecycle
- request/response handling
- error normalization
- API modules

---

## Feature 11 — Authentication

### Outcome

Each user sees only their own applications.

### Build

- Sign up.
- Login.
- Logout.
- Session restoration.
- Protected routes.
- Unauthorized state.
- Auth loading state.

### Learn

- authentication flow
- session state
- protected routes
- authorization boundaries

### Security rule

Never expose secrets in the frontend.

---

## Feature 12 — User Data Isolation

### Outcome

Application data belongs to the authenticated user.

### Build

- user ownership field.
- row-level security.
- policies.
- authenticated queries.
- unauthorized access testing.

### Learn

- authorization vs authentication
- database security
- user-scoped data

---

## Feature 13 — Interviews

### Outcome

An application can contain an interview timeline.

### Build

- Add interview.
- Edit interview.
- Delete interview.
- Interview round.
- Date/time.
- Interview type.
- Notes.
- Status.

### Learn

- relational data
- nested feature workflows
- date handling
- modal/form reuse

---

## Feature 14 — Notes

### Outcome

Each application can store useful notes.

### Build

- Add note.
- Edit note.
- Delete note.
- Note timestamps.
- Empty state.

### Learn

- reusable CRUD patterns
- optimistic UI thinking
- component reuse

---

## Feature 15 — Follow-up Workflow

### Outcome

The product actively helps manage pending follow-ups.

### Build

- Next follow-up date.
- Upcoming follow-ups.
- Overdue follow-ups.
- Mark followed up.
- Dashboard follow-up section.

### Learn

- date comparisons
- derived state
- sorting
- conditional styling

---

## Feature 16 — Dashboard Analytics

### Outcome

The dashboard becomes useful rather than decorative.

### Build

- total applications
- active applications
- interviews
- offers
- rejection count
- response rate
- status distribution
- applications over time

### Learn

- `reduce`
- aggregation
- derived metrics
- data transformation

### Rule

Metrics are derived from source data. Do not maintain duplicate counters unless there is a real persistence requirement.

---

## Feature 17 — URL Query State

### Outcome

Filters can be shared/bookmarked.

### Build

- search query in URL.
- status filter in URL.
- sort in URL.
- pagination in URL where applicable.
- restore filters on refresh.

### Learn

- URLSearchParams
- query parameters
- state synchronization

---

## Feature 18 — Pagination

### Outcome

The application remains usable with a large dataset.

### Build

- page size.
- next/previous.
- current page.
- result count.
- loading transitions.
- empty page handling.

### Learn

- server-side pagination
- request parameters
- async state
- large dataset thinking

---

## Feature 19 — Reusable UI System

### Outcome

The application stops accumulating duplicated UI.

### Build only what the product needs:

- Button
- Input
- Select
- Badge
- Card
- Modal
- Toast
- Skeleton
- EmptyState
- ErrorState
- ConfirmDialog

### Learn

- component API design
- composition
- variants
- accessibility
- reuse without over-abstraction

---

## Feature 20 — Accessibility Pass

### Outcome

Core workflows are keyboard accessible and semantically correct.

### Audit

- labels
- buttons
- form errors
- focus management
- modal focus
- keyboard navigation
- visible focus
- semantic headings
- accessible status messages
- color contrast

### Learn

- semantic HTML
- ARIA basics
- keyboard interaction
- focus management

---

## Feature 21 — Error Architecture

### Outcome

Failures are handled consistently.

### Build

- API error normalization.
- reusable ErrorState.
- retry actions.
- form errors.
- route-level fallback.
- unexpected error boundary.

### Learn

- error boundaries
- error states
- debugging
- resilient UI

---

## Feature 22 — Testing

### Outcome

Critical behavior is protected by automated tests.

### Unit tests

Test:

- filtering
- sorting
- statistics
- validation
- date calculations
- data transformations

### Component tests

Test:

- application form
- filters
- status changes
- modal behavior

### User-flow tests

Test:

- login
- create application
- edit application
- delete application
- filter applications

### Learn

- testing philosophy
- user-focused assertions
- mocking
- async tests

---

## Feature 23 — API Mocking

### Outcome

Frontend behavior can be tested without depending on a live backend.

### Build

- MSW handlers.
- success responses.
- loading behavior.
- server errors.
- empty responses.

### Learn

- network mocking
- deterministic testing
- async failure testing

---

## Feature 24 — Debugging Lab

### Outcome

You can diagnose bugs instead of guessing.

Intentionally introduce:

- stale state bug
- incorrect dependency bug
- broken filter
- failed API request
- race condition
- missing key
- uncontrolled/controlled input issue
- timer cleanup issue

For each bug document:

```
Symptom
→ Reproduction
→ Root cause
→ Fix
→ Prevention
```

This becomes interview material.

---

## Feature 25 — Performance

### Outcome

Performance work is based on measurement.

### Measure

- unnecessary renders
- expensive derived calculations
- large lists
- bundle size
- network requests

### Optimize only where evidence exists

- memoization
- stable callbacks
- pagination
- lazy loading
- code splitting
- debouncing

### Learn

- React render cycle
- React DevTools
- `memo`
- `useMemo`
- `useCallback`
- browser performance basics

---

## Feature 26 — Production UX Polish

### Outcome

The application feels finished.

### Add

- responsive layouts
- consistent spacing
- loading skeletons
- empty states
- error states
- toast feedback
- confirmation dialogs
- disabled submit states
- mobile navigation
- accessible focus states

No cosmetic polishing before core functionality works.

---

## Feature 27 — Production Configuration

### Outcome

The app can run safely in production.

### Build

- production environment variables.
- separate development/production configuration.
- production build verification.
- deployment configuration.
- SPA route fallback.
- error monitoring strategy/documentation.

---

## Feature 28 — Deployment

### Outcome

Anyone can use the application through a public URL.

### Ship

- deploy frontend.
- configure environment variables.
- configure Supabase production project.
- test authentication.
- test CRUD.
- test routing.
- test refresh on nested routes.
- verify production build.

### Deliverables

- live URL
- GitHub repository
- README
- screenshots

---

## Feature 29 — Git + Professional Workflow

### Workflow

```
main
 ↓
feature branch
 ↓
implementation
 ↓
test
 ↓
commit
 ↓
pull request
 ↓
review/check
 ↓
merge
```

### Commit examples

```
feat: add application creation form
feat: add application filtering
fix: prevent duplicate application submission
refactor: separate application API layer
test: cover application status updates
perf: debounce application search
docs: update production setup
```

---

## Feature 30 — Portfolio Presentation

### README must explain

1. What the product does.
2. Why it exists.
3. Main features.
4. Tech stack.
5. Architecture.
6. Data flow.
7. Key technical decisions.
8. Testing strategy.
9. Performance work.
10. Challenges and debugging stories.
11. Trade-offs.
12. Local setup.
13. Live demo.

### Include

- live URL
- screenshots
- architecture diagram
- feature walkthrough
- GitHub repository

---

# 7. End-to-End Feature Order

Do not build this randomly.

```
1. Repository foundation
        ↓
2. Dashboard UI
        ↓
3. Application list
        ↓
4. Search/filter/sort
        ↓
5. Create application
        ↓
6. Edit/delete
        ↓
7. Application detail
        ↓
8. Local persistence
        ↓
9. Supabase database
        ↓
10. Real CRUD
        ↓
11. Authentication
        ↓
12. User data isolation
        ↓
13. Interviews
        ↓
14. Notes
        ↓
15. Follow-ups
        ↓
16. Analytics
        ↓
17. URL query state
        ↓
18. Pagination
        ↓
19. Reusable UI system
        ↓
20. Accessibility
        ↓
21. Error architecture
        ↓
22. Testing
        ↓
23. API mocking
        ↓
24. Debugging
        ↓
25. Performance
        ↓
26. Production UX
        ↓
27. Production configuration
        ↓
28. Deployment
        ↓
29. Professional Git workflow
        ↓
30. Portfolio presentation
```

---

# 8. Learning Loop

Every feature follows the same loop:

### 1. Understand

Learn only the concepts required for the feature.

### 2. Implement

Build the feature from a blank file where practical.

### 3. Break

Intentionally change something and observe the failure.

### 4. Debug

Use browser DevTools, React DevTools, logs, breakpoints, and network inspection.

### 5. Test

Write tests for important behavior.

### 6. Ship

Commit the feature and deploy when appropriate.

### 7. Explain

Answer:

- What problem does this feature solve?
- Where does the state live?
- How does data flow?
- Why did I choose this approach?
- What can fail?
- How is failure handled?
- How would I improve it?

If you cannot explain it, the feature is not finished.

---

# 9. Definition of Done

A feature is **not done** because the UI works once.

A feature is done when:

- [ ]  Requirement is clear.
- [ ]  UI works.
- [ ]  State/data flow is understood.
- [ ]  Loading state exists where needed.
- [ ]  Empty state exists where needed.
- [ ]  Error state exists where needed.
- [ ]  Validation exists where needed.
- [ ]  Responsive behavior works.
- [ ]  Accessibility is acceptable.
- [ ]  Important logic is tested.
- [ ]  Code is understandable.
- [ ]  No unnecessary abstraction was added.
- [ ]  Git commit exists.
- [ ]  README/documentation is updated when the feature changes architecture.

---

# 10. Interview Extraction

Every major feature must produce interview material.

### JavaScript

- array transformations
- closures
- debounce
- immutability
- async/await
- promises
- event loop
- data transformation

### React

- component boundaries
- props
- state
- derived state
- effects
- custom hooks
- routing
- controlled forms
- rendering behavior
- performance

### Machine Coding

Be able to rebuild isolated versions of:

- searchable application list
- filter panel
- debounced search
- CRUD form
- modal
- pagination
- dashboard statistics
- status pipeline

### Project discussion

Be able to explain:

- architecture
- data flow
- API layer
- authentication
- error handling
- testing
- debugging
- performance
- deployment
- trade-offs

---

# 11. Portfolio Quality Bar

The final product should prove:

```
Can build UI
      +
Can manage state
      +
Can transform data
      +
Can consume APIs
      +
Can handle failures
      +
Can structure React code
      +
Can test behavior
      +
Can debug problems
      +
Can optimize with evidence
      +
Can use Git professionally
      +
Can deploy
      =
Job-ready frontend project
```

The goal is **not** to have the biggest project.

The goal is to have a project where you can open the repository and confidently explain almost every important decision.

---

# 12. Scope Control

### Never add a feature because:

- it looks impressive
- another portfolio has it
- a tutorial included it
- a technology is trendy
- you are bored with the current feature

### Add a feature only if it:

1. improves the product,
2. teaches a roadmap skill,
3. creates interview evidence, or
4. exposes a real engineering problem worth solving.

If it does none of these, cut it.

---

# 13. Final Portfolio Deliverables

By completion:

- [ ]  Public GitHub repository
- [ ]  Live production URL
- [ ]  Authentication
- [ ]  Persistent application data
- [ ]  Application CRUD
- [ ]  Search/filter/sort
- [ ]  Application detail
- [ ]  Interviews
- [ ]  Notes
- [ ]  Follow-ups
- [ ]  Analytics
- [ ]  Responsive UI
- [ ]  Accessibility pass
- [ ]  Automated tests
- [ ]  API mocking
- [ ]  Documented debugging cases
- [ ]  Performance notes
- [ ]  Architecture documentation
- [ ]  Strong README
- [ ]  Screenshots
- [ ]  Interview project walkthrough
- [ ]  Machine-coding features extracted from the project

<aside>
🚢

**Shipping rule:** Never wait for the entire portfolio to be finished. Ship the smallest useful version first, then evolve it feature-by-feature as the roadmap teaches the next skill.

</aside>