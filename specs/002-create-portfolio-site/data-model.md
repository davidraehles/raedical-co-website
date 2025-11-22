# Data Model: Portfolio Site

## Overview

The data model for this project is file-based, using Markdown/MDX files with YAML frontmatter.

## Entities

### 1. Project

Represents a portfolio item showcased in the Hero section or a dedicated projects list.

**Source**: `src/content/projects/*.mdx`

**Frontmatter Schema**:

| Field | Type | Required | Description | Validation |
|-------|------|----------|-------------|------------|
| `title` | string | Yes | Name of the project | Max 100 chars |
| `description` | string | Yes | Short summary | Max 200 chars |
| `image` | string | Yes | Path to cover image | Must start with `/` (public dir) |
| `link` | string | No | External URL to project | Valid URL format |
| `tags` | string[] | No | Tech stack used | - |
| `date` | date | Yes | Project completion date | ISO 8601 (YYYY-MM-DD) |
| `featured` | boolean | No | Show in Hero section | Default: false |

**Example**:
```yaml
---
title: "E-Commerce Platform"
description: "A full-stack shop built with Next.js and Stripe."
image: "/images/projects/ecommerce.jpg"
link: "https://example.com"
tags: ["Next.js", "Stripe", "Tailwind"]
date: "2024-01-15"
featured: true
---
```

### 2. BlogPost

Represents an article in the blog section.

**Source**: `src/content/posts/*.mdx`

**Frontmatter Schema**:

| Field | Type | Required | Description | Validation |
|-------|------|----------|-------------|------------|
| `title` | string | Yes | Article headline | Max 100 chars |
| `date` | date | Yes | Publication date | ISO 8601 (YYYY-MM-DD) |
| `excerpt` | string | Yes | Preview text | Max 200 chars |
| `author` | string | No | Author name | Default: "David Rähles" |
| `coverImage` | string | No | Hero image for post | Must start with `/` |

**Example**:
```yaml
---
title: "Why I chose Next.js"
date: "2024-03-10"
excerpt: "Exploring the benefits of the App Router for static sites."
author: "David Rähles"
---
```

## Validation

We will use **Zod** to validate frontmatter at build/runtime when fetching content.

```typescript
// src/lib/mdx.ts (Conceptual)
const ProjectSchema = z.object({
  title: z.string().max(100),
  description: z.string().max(200),
  image: z.string().startsWith('/'),
  link: z.string().url().optional(),
  tags: z.array(z.string()).optional(),
  date: z.string().transform((str) => new Date(str)),
  featured: z.boolean().default(false),
});
```