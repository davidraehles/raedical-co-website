# Research: Create Portfolio Site

## 1. Content Management (MDX)

**Decision**: Use `next-mdx-remote` combined with `gray-matter` for frontmatter parsing.

**Rationale**:
- **Server Components**: Works seamlessly with Next.js App Router Server Components, allowing content fetching on the server.
- **Flexibility**: Allows custom components to be passed to MDX files (e.g., for the Project showcase).
- **Lightweight**: Avoids the overhead of heavier CMS-like solutions or unmaintained libraries like Contentlayer.
- **Control**: Direct access to the file system via `fs` allows for simple listing and filtering of posts/projects.

**Alternatives Considered**:
- **@next/mdx**: Good for pages that *are* MDX files, but less flexible for loading dynamic lists of content (like a blog index) with metadata.
- **Contentlayer**: Previously popular but currently unmaintained/deprecated.
- **Velite**: Promising type-safe content library, but might be overkill for a simple portfolio start.

## 2. Styling Strategy

**Decision**: Tailwind CSS (Mandated).

**Rationale**:
- **Performance**: Generates minimal CSS bundle based on usage.
- **Mobile-First**: Utility classes make responsive design intuitive.
- **Consistency**: Enforces a design system via configuration.

**Best Practices**:
- Use `clsx` and `tailwind-merge` for conditional class application in reusable components.
- Define custom colors/fonts in `tailwind.config.ts` to match branding.

## 3. Project Structure

**Decision**: Use `src/` directory structure.

**Rationale**:
- **Organization**: Separates application code from configuration files at the root.
- **Standard**: Default recommendation for modern Next.js applications.

**Structure**:
- `src/app`: Routes.
- `src/content`: MDX files (Projects, Posts). *Note: Placing content inside `src` ensures it's tracked by build tools, though root `content/` is also common. We will use `src/content` to keep everything self-contained.*
- `src/components`: React components.
- `src/lib`: Utilities (MDX helpers).

## 4. Contact Implementation

**Decision**: `mailto:` link (as per Spec).

**Rationale**:
- **Simplicity**: Meets the immediate requirement without backend infrastructure.
- **User Preference**: Explicitly requested by the user.

**Future Proofing**:
- If a form is added later, we will use React Hook Form + Zod as per Constitution.

## 5. Legal Pages

**Decision**: Static MDX pages.

**Rationale**:
- **Maintainability**: Easy to update text without touching code.
- **Consistency**: Same styling and layout as the rest of the site.