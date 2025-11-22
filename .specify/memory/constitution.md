# [PROJECT_NAME] Constitution
<!-- Example: Spec Constitution, TaskFlow Constitution, etc. -->

## Core Principles

### I. Performance First
Performance is a feature, not an afterthought. We target a Lighthouse Performance score of 90+ on mobile and desktop. Core Web Vitals (LCP, CLS, INP) must remain within "Good" thresholds. Prefer Static Site Generation (SSG) over Server-Side Rendering (SSR) or Client-Side Rendering (CSR) unless dynamic data requirements strictly dictate otherwise. Keep initial bundle sizes small (<200KB).

### II. Accessibility & Inclusivity (NON-NEGOTIABLE)
The website must be accessible to all users. WCAG 2.1 Level AA compliance is mandatory for all pages and components. This includes proper semantic HTML, keyboard navigability, sufficient color contrast, and screen reader support. Automated accessibility tests (e.g., axe-core) must pass in CI, supplemented by manual verification.

### III. Type Safety & Code Quality
We prioritize maintainability and correctness. TypeScript is mandatory with `strict` mode enabled. `any` types are forbidden unless explicitly justified in comments. Code must adhere to project linting (ESLint) and formatting (Prettier) standards. Components should be modular, reusable, and follow the Single Responsibility Principle.

### IV. Comprehensive Testing Strategy
Confidence in deployment comes from testing.
- **Unit/Component Tests**: Required for all UI components and utility logic (Vitest + React Testing Library).
- **E2E Tests**: Required for critical user journeys and form submissions (Playwright).
- **Accessibility Tests**: Automated checks required for all views.
Tests must be written alongside or before implementation.

### V. Mobile-First Responsive Design
Design and implement for mobile screens (320px+) first, then enhance for tablet and desktop. The interface must be fluid and functional across all viewport sizes. Touch targets must be at least 44x44px.

### VI. Version Control & Deployment
All changes must be committed and pushed to the remote repository.
- **Commits**: Use conventional commits (e.g., `feat:`, `fix:`, `docs:`).
- **Pull Requests**: Create a Pull Request (PR) for every feature or fix using the GitHub CLI (`gh pr create`).
- **Workflow**: Always commit, push, and create a PR after completing a significant unit of work or a task.

## Technology Stack Constraints

**Primary Stack**: TypeScript, Next.js (App Router), React, Tailwind CSS.
**State Management**: Prefer React built-in state (Context, Hooks) or URL state. Avoid heavy external state libraries (Redux, etc.) unless complexity warrants it.
**Styling**: Tailwind CSS is the standard. Avoid CSS-in-JS runtime libraries to preserve performance.
**Forms**: React Hook Form + Zod for validation.

## Development Workflow

**Branching**: Feature branch workflow (e.g., `feature/name` or `specs/001-name`).
**Code Review**: All changes require a Pull Request (PR) with at least one approval. PRs must verify that new code complies with Core Principles.
**CI/CD**: Automated tests, linting, and build checks must pass before merging.
**Documentation**: Update relevant documentation (README, specs) with code changes.

## Governance

This constitution defines the non-negotiable rules for the project.
- **Amendments**: Changes to this document require a dedicated PR, discussion, and approval from project maintainers.
- **Versioning**: We follow Semantic Versioning for the constitution.
  - MAJOR: Removing or fundamentally changing a principle.
  - MINOR: Adding a new principle or section.
  - PATCH: Clarifications and non-substantive changes.
- **Compliance**: All feature plans and specifications must explicitly check against these principles.

**Version**: 1.0.0 | **Ratified**: 2025-11-22 | **Last Amended**: 2025-11-22
