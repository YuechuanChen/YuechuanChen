# Academic Personal Page README — Design Spec

**Date**: 2026-05-29
**Status**: Approved

## Overview

Transform a bare-bones placeholder `README.md` into a polished academic personal page for a GitHub profile. The output is a single-file template the user fills in by searching for `REPLACE:` markers and replacing them with real content.

## Constraints

- **Single file**: `README.md` only, no external assets or build step
- **No custom fonts**: GitHub sanitizes external CSS; rely on the system font stack
- **No JavaScript**: GitHub strips all JS from rendered READMEs
- **GitHub-compatible HTML**: Only inline styles on a whitelist of allowed tags work

## Design Decisions

### Layout: Single Column Academic

A vertical stack matching the traditional academic CV format. Each section is a self-contained block with a styled heading and divider.

Section order (top to bottom):
1. Header (name, role, institution, links)
2. About Me
3. Education
4. Research Interests
5. Skills
6. Projects
7. Publications
8. Contact
9. Footer

### Color Palette: Warm Scholar

| Role | Hex | Usage |
|---|---|---|
| Primary text | `#1c1917` | Body, names |
| Heading | `#78350f` | Section titles |
| Accent | `#b45309` | Dividers, links, badges |
| Muted | `#78716c` | Secondary text, dates |
| Background | `#fafaf9` | Optional `<table>` / `<div>` backgrounds |
| Subtle border | `#e7e5e4` | Table borders, separators |

### Typography

No custom fonts. Use GitHub's native stack: `-apple-system, BlinkMacSystemFont, "Segoe UI", "Noto Sans", Helvetica, Arial, sans-serif, "Apple Color Emoji", "Segoe UI Emoji"`.

- Name: `<h1>` with `font-size: 2em` and warm dark color
- Subtitle: `<p>` with `font-size: 1em` and muted color
- Section headings: `<h2>` with amber accent `border-bottom`
- Body: default markdown paragraph rendering
- Code/inline tech: backtick-wrapped for GitHub's monospace rendering

### Section Specifications

#### 1. Header
- Centered, name in large warm heading
- Subtitle line: "Undergraduate Researcher @ [Institution]"
- Badge row below: GitHub, email, personal website, Google Scholar (icon + link)

#### 2. About Me
- 2-3 sentence paragraph
- First line: degree program and institution
- Second line: current focus and interests
- Third line: open to collaboration / contact

#### 3. Education
- Table with columns: Degree | Institution | Period | GPA / Notes
- Bold the degree name
- Italicize dates in muted color

#### 4. Research Interests
- Unordered list of 3-5 topics
- Each item: bold keyword, dash, brief description
- Example: **Machine Learning** — focusing on interpretable models and their applications in healthcare.

#### 5. Skills
- Three subsections: Languages, Frameworks & Tools, Domains
- Each as a compact comma-separated list or badge-style inline code spans

#### 6. Projects
- Each project as a sub-heading (`###`) with:
  - One-line description
  - Tech stack in `code` spans
  - Link to repo (if public)
- Sorted by recency

#### 7. Publications
- Ordered list by year (most recent first)
- Each entry: authors (bold your name), title, venue, year, link
- If no publications, include a TBD placeholder line or remove the section entirely (noted with a comment)

#### 8. Contact
- Table or grid of icon + link pairs
- Email, GitHub, personal website, Google Scholar, LinkedIn

#### 9. Footer
- Thin amber line
- Small muted text: "Last updated: [date]" and a license/attribution note if desired

### Template Mechanism

All placeholder text uses HTML comment markers:

```markdown
<!-- REPLACE: yourname@example.com -->
yourname@example.com
```

The user edits by searching `REPLACE:` globally and replacing each occurrence. Sections that may not apply (e.g., Publications if none exist) are wrapped in conditional comments.

### Files Changed

| File | Action |
|---|---|
| `README.md` | Full rewrite — replace placeholder template with polished academic page |

## Template Content Summary

```
README.md (~120-150 lines)
├── <!-- REPLACE: --> markers: ~30
├── Sections: 9
├── HTML tables: 2 (Education, Contact)
├── HTML headings/dividers: ~9
└── Pure markdown body text
```

## Self-Review

- **Placeholder scan**: All `REPLACE:` markers are explicit and searchable. No TBDs remain.
- **Internal consistency**: Color palette, section order, and typography rules are uniform across all sections.
- **Scope**: One file, one template. No dependencies, no build step, no external assets.
- **Ambiguity**: Every placeholder has a concrete example value. Section visibility for Publications is gated with a clear comment.
