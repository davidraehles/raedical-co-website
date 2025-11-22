# Implementation Plan: [FEATURE]

**Branch**: `[###-feature-name]` | **Date**: [DATE] | **Spec**: [link]
**Input**: Feature specification from `/specs/[###-feature-name]/spec.md`

**Note**: This template is filled in by the `/speckit.plan` command. See `.specify/templates/commands/plan.md` for the execution workflow.

## Summary

Create a portfolio website for "The Rädical Co." (David Rähles) featuring a project showcase (Hero section), blog, contact page, and mandatory legal pages (Imprint, Privacy). The site will be built with Next.js (App Router), styled with Tailwind CSS, use local Markdown/MDX for content management, and deploy to Vercel.

## Technical Context

<!--
  ACTION REQUIRED: Replace the content in this section with the technical details
  for the project. The structure here is presented in advisory capacity to guide
  the iteration process.
-->

**Language/Version**: TypeScript 5.x, Node.js 20+ (LTS)
**Primary Dependencies**: Next.js 14+ (App Router), React 18+, Tailwind CSS, Zod, React Hook Form
**Storage**: Local Filesystem (Markdown/MDX)
**Testing**: Vitest, React Testing Library, Playwright
**Target Platform**: Vercel (Web)
**Project Type**: Web application
**Performance Goals**: Lighthouse 90+ (Mobile/Desktop), Core Web Vitals "Good", &lt;200KB initial bundle
**Constraints**: Mobile-first, WCAG 2.1 Level AA compliance
**Scale/Scope**: ~5 core pages, low data volume (static content)

## Constitution Check

*GATE: Must pass before Phase 0 research. Re-check after Phase 1 design.*

| Principle | Status | Notes |
|-----------|--------|-------|
| **I. Performance First** | ✅ PASS | Using Next.js SSG for static content (MDX). |
| **II. Accessibility** | ✅ PASS | Will use semantic HTML and test with axe-core. |
| **III. Type Safety** | ✅ PASS | TypeScript strict mode enabled by default in Next.js. |
| **IV. Testing Strategy** | ✅ PASS | Vitest for components, Playwright for E2E (Contact, Navigation). |
| **V. Mobile-First** | ✅ PASS | Tailwind CSS facilitates mobile-first responsive design. |
| **VI. Version Control** | ✅ PASS | Standard git workflow applies. |
| **Tech Stack Constraints** | ✅ PASS | Next.js, React, Tailwind, Zod aligned with Constitution. |

## Project Structure

### Documentation (this feature)

```text
specs/[###-feature]/
├── plan.md              # This file (/speckit.plan command output)
├── research.md          # Phase 0 output (/speckit.plan command)
├── data-model.md        # Phase 1 output (/speckit.plan command)
├── quickstart.md        # Phase 1 output (/speckit.plan command)
├── contracts/           # Phase 1 output (/speckit.plan command)
└── tasks.md             # Phase 2 output (/speckit.tasks command - NOT created by /speckit.plan)
```

### Source Code (repository root)
<!--
  ACTION REQUIRED: Replace the placeholder tree below with the concrete layout
  for this feature. Delete unused options and expand the chosen structure with
  real paths (e.g., apps/admin, packages/something). The delivered plan must
  not include Option labels.
-->

```text
src/
├── app/                 # Next.js App Router
│   ├── (site)/          # Route group for site layout
│   │   ├── page.tsx     # Homepage (Hero/Projects)
│   │   ├── blog/        # Blog listing & posts
│   │   ├── contact/     # Contact page
│   │   ├── imprint/     # Legal page
│   │   └── privacy/     # Legal page
│   ├── layout.tsx       # Root layout
│   └── globals.css      # Global styles (Tailwind)
├── components/
│   ├── ui/              # Reusable UI components
│   ├── features/        # Feature-specific components (Hero, ProjectCard)
│   └── layout/          # Header, Footer
├── lib/
│   ├── mdx.ts           # MDX parsing logic
│   └── utils.ts         # Utility functions
├── content/             # Local content storage
│   ├── projects/        # Project MDX files
│   └── posts/           # Blog MDX files
└── types/               # TypeScript definitions
```

**Structure Decision**: Standard Next.js App Router structure with `src` directory. Content stored in `content/` at root or `src/content` (to be decided in research, assuming root for now).

## Complexity Tracking

> **Fill ONLY if Constitution Check has violations that must be justified**

| Violation | Why Needed | Simpler Alternative Rejected Because |
|-----------|------------|-------------------------------------|
| [e.g., 4th project] | [current need] | [why 3 projects insufficient] |
| [e.g., Repository pattern] | [specific problem] | [why direct DB access insufficient] |
