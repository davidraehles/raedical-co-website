# Quickstart: Portfolio Site

## Prerequisites

- Node.js 20+ (LTS)
- npm or pnpm

## Installation

1. **Clone the repository**:
   ```bash
   git clone <repo-url>
   cd raedical-co-website
   ```

2. **Install dependencies**:
   ```bash
   npm install
   ```

## Development

Start the local development server:

```bash
npm run dev
```

The site will be available at `http://localhost:3000`.

## Content Management

### Adding a Project

1. Create a new MDX file in `src/content/projects/`.
2. Add the required frontmatter (see `specs/002-create-portfolio-site/data-model.md`).
3. Write the project description in Markdown/MDX.

### Adding a Blog Post

1. Create a new MDX file in `src/content/posts/`.
2. Add the required frontmatter.
3. Write the article content.

## Testing

Run the test suite:

```bash
# Unit tests
npm run test

# E2E tests
npm run test:e2e
```

## Deployment

The project is configured for Vercel.

1. Push changes to the `main` branch.
2. Vercel will automatically build and deploy the site.