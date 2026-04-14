# Skill: web-design-guidelines

Apply Vercel-inspired web design principles to any UI task in this project.

## What this skill does

When invoked, review the current file or selection and apply the following guidelines. Report what was changed and why.

---

## Layout & Spacing

- Use an 8px base grid. All spacing values should be multiples of 8 (8, 16, 24, 32, 48, 64).
- Max content width: `1200px`, centered with `margin: 0 auto`.
- Section padding: `96px 0` on desktop, `64px 0` on mobile.
- Never use arbitrary pixel values for spacing — use `--space-*` tokens or the grid.

## Typography Rules

- One typeface per role: sans-serif for UI, monospace for code.
- Heading hierarchy: only one `<h1>` per page; `<h2>` for sections; `<h3>` for cards.
- Line height: `1.5` for body, `1.15` for headings above `2xl`.
- Letter spacing: `-0.02em` on headings ≥ `2xl`; `0` on body.
- Max line length: `68ch` for readable prose blocks.

## Color Usage

- Background: `--color-paper` or `--color-ink` (dark mode)
- Text on light: `--color-ink`; text on dark: `--color-paper`
- Accent (`--color-accent`) only for: CTAs, active states, highlights — never for backgrounds
- Muted text (`--color-muted`) for metadata, labels, secondary info only

## Component Patterns

- **Buttons:** Solid (primary), outlined (secondary), ghost (tertiary). No more than two button variants per view.
- **Cards:** `border: 1px solid var(--color-border)` + `border-radius: 6px`. No shadow by default.
- **Inputs:** Full-width on mobile. `border-radius: 4px`. Focus ring: `outline: 2px solid var(--color-accent)`.
- **Dividers:** Use `<hr>` or `border-top: 1px solid var(--color-border)`. Never use box shadows as separators.

## Responsive Breakpoints

```css
/* Mobile-first */
/* sm  */ @media (min-width: 640px)  { }
/* md  */ @media (min-width: 768px)  { }
/* lg  */ @media (min-width: 1024px) { }
/* xl  */ @media (min-width: 1280px) { }
```

## Performance Defaults

- Images: always include `width`, `height`, and `loading="lazy"` (except above-the-fold hero).
- Fonts: `font-display: swap` on all `@font-face` declarations.
- No layout-blocking scripts in `<head>` — use `defer` or `type="module"`.

## Accessibility Baseline

- Every interactive element must be keyboard-reachable.
- Contrast ratio ≥ 4.5:1 for body text, ≥ 3:1 for large text and UI components.
- All images need descriptive `alt` text (empty `alt=""` for decorative images).
- Avoid `outline: none` without a visible focus replacement.
