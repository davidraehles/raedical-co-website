---
description: "Task list for Create Portfolio Site feature"
---

# Tasks: Create Portfolio Site

**Input**: Design documents from `/specs/002-create-portfolio-site/`
**Prerequisites**: plan.md, spec.md, research.md, data-model.md

**Tests**: Tests are included for critical user journeys as per the Project Constitution.

**Organization**: Tasks are grouped by user story to enable independent implementation and testing of each story.

## Phase 1: Setup (Shared Infrastructure)

**Purpose**: Project initialization and basic structure

- [ ] T001 Initialize Next.js project with TypeScript, Tailwind CSS, and ESLint
- [ ] T002 [P] Install dependencies (next-mdx-remote, gray-matter, zod, clsx, tailwind-merge, lucide-react)
- [ ] T003 Create project directory structure (src/content, src/lib, src/components, src/types)
- [ ] T004 [P] Configure Tailwind CSS in tailwind.config.ts (colors, fonts)
- [ ] T005 [P] Setup global styles in src/app/globals.css

---

## Phase 2: Foundational (Blocking Prerequisites)

**Purpose**: Core infrastructure that MUST be complete before ANY user story can be implemented

**⚠️ CRITICAL**: No user story work can begin until this phase is complete

- [ ] T006 Create Zod schemas for Project and BlogPost in src/lib/schemas.ts
- [ ] T007 Implement MDX utility functions (getFiles, getFileBySlug) in src/lib/mdx.ts
- [ ] T008 [P] Create reusable UI components (Button, Container) in src/components/ui/
- [ ] T009 Create Header component with navigation in src/components/layout/Header.tsx
- [ ] T010 Create Footer component in src/components/layout/Footer.tsx
- [ ] T011 Assemble Root Layout in src/app/layout.tsx

**Checkpoint**: Foundation ready - user story implementation can now begin in parallel

---

## Phase 3: User Story 1 - View Projects Portfolio (Priority: P1) 🎯 MVP

**Goal**: Visitors can see a showcase of projects on the homepage.

**Independent Test**: Visit homepage, verify project list is visible and clickable.

### Tests for User Story 1 (REQUIRED) ⚠️

- [ ] T012 [P] [US1] E2E test for Homepage/Hero project list in tests/e2e/homepage.spec.ts

### Implementation for User Story 1

- [ ] T013 [P] [US1] Create sample project MDX files in src/content/projects/
- [ ] T014 [P] [US1] Create ProjectCard component in src/components/features/ProjectCard.tsx
- [ ] T015 [US1] Implement Hero/ProjectList section in src/components/features/Hero.tsx
- [ ] T016 [US1] Implement Homepage route fetching projects in src/app/(site)/page.tsx
- [ ] T017 [US1] Implement Project Detail page (optional per spec, but implied by "view more details") in src/app/(site)/projects/[slug]/page.tsx

**Checkpoint**: At this point, User Story 1 should be fully functional and testable independently

---

## Phase 4: User Story 2 - Contact Owner (Priority: P1)

**Goal**: Visitors can find contact information.

**Independent Test**: Navigate to Contact page, verify mailto link exists.

### Tests for User Story 2 (REQUIRED) ⚠️

- [ ] T018 [P] [US2] E2E test for Contact page in tests/e2e/contact.spec.ts

### Implementation for User Story 2

- [ ] T019 [US2] Create Contact page layout in src/app/(site)/contact/page.tsx
- [ ] T020 [US2] Implement contact information display with mailto link in src/app/(site)/contact/page.tsx

**Checkpoint**: At this point, User Stories 1 AND 2 should both work independently

---

## Phase 5: User Story 3 - Access Legal Information (Priority: P1)

**Goal**: Visitors can access Imprint and Privacy Policy.

**Independent Test**: Click footer links, verify legal pages load.

### Tests for User Story 3 (REQUIRED) ⚠️

- [ ] T021 [P] [US3] E2E test for Legal pages navigation in tests/e2e/legal.spec.ts

### Implementation for User Story 3

- [ ] T022 [P] [US3] Create Imprint page content in src/app/(site)/imprint/page.tsx (or .mdx)
- [ ] T023 [P] [US3] Create Privacy Policy page content in src/app/(site)/privacy/page.tsx (or .mdx)
- [ ] T024 [US3] Ensure Footer links point to correct legal routes in src/components/layout/Footer.tsx

**Checkpoint**: All P1 stories complete. Site is legally compliant and functional.

---

## Phase 6: User Story 4 - Read Blog (Priority: P2)

**Goal**: Visitors can read blog posts.

**Independent Test**: Navigate to Blog, click post, read content.

### Tests for User Story 4 (REQUIRED) ⚠️

- [ ] T025 [P] [US4] E2E test for Blog listing and post view in tests/e2e/blog.spec.ts

### Implementation for User Story 4

- [ ] T026 [P] [US4] Create sample blog post MDX files in src/content/posts/
- [ ] T027 [P] [US4] Create PostCard component in src/components/features/PostCard.tsx
- [ ] T028 [US4] Implement Blog Listing page in src/app/(site)/blog/page.tsx
- [ ] T029 [US4] Implement Blog Post Detail page in src/app/(site)/blog/[slug]/page.tsx

**Checkpoint**: All user stories should now be independently functional

---

## Phase 7: Polish & Cross-Cutting Concerns

**Purpose**: Improvements that affect multiple user stories

- [ ] T030 [P] Verify responsive design on mobile/tablet breakpoints
- [ ] T031 [P] Run accessibility audit (axe-core)
- [ ] T032 Update README.md with project documentation
- [ ] T033 Final code cleanup and linting check

---

## Dependencies & Execution Order

### Phase Dependencies

- **Setup (Phase 1)**: No dependencies
- **Foundational (Phase 2)**: Depends on Setup
- **User Stories (Phase 3-5)**: Depend on Foundational. US1, US2, US3 are P1 and can be parallelized.
- **User Story 4 (Phase 6)**: Depends on Foundational. P2 priority.

### Parallel Opportunities

- T013 (Sample Projects) and T014 (ProjectCard) can run in parallel.
- T022 (Imprint) and T023 (Privacy) can run in parallel.
- US1, US2, and US3 are all P1 and independent, suitable for parallel team execution.

## Implementation Strategy

### MVP First (P1 Stories)

1. Complete Setup & Foundational.
2. Implement US1 (Projects), US2 (Contact), US3 (Legal).
3. Validate MVP.
4. Implement US4 (Blog) as a follow-up release.